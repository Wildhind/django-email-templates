====================
Django-Email-Templates
====================

Simple Django app providing email templates.


Installation
------------
1. Using pip:
::

    pip install -e git+git://github.com/Wildhind/django-email-templates.git#egg=email_templates


2. Add "email_templates" to your INSTALLED_APPS setting like this::
::

    INSTALLED_APPS = (
          ...
          'email_templates',
      )


Usage
-----
Create email template in admin interface.

Somewhere in your code use function send_templated_email()

This function requests two parameters:

 * template slug
 * context

Example:
::

    from email_templates.utils import send_templated_email

    …

    if form.is_valid():
        form.save()
        send_templated_email('new_order', request.POST)
        return render_to_response('main/feedback_ok.html', {'form': form}, context_instance=RequestContext(request))

    …

