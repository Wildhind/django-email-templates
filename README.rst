====================
Django-Email-Templates
====================

Simple Django app providing email templates.


Installation
------------
1. Using pip:
::

    pip install -e git+git://github.com/Wildhind/django-email-templates.git#egg=email_templates


2. Add "email_templates" to your INSTALLED_APPS setting like this:
::

    INSTALLED_APPS = (
          ...
          'email_templates',
      )

3. Create database table:
::

    python manage.py migrate

4. Configure Email settings in your settings.py:
::

    SERVER_EMAIL = 'email@gmail.com'
    EMAIL_USE_TLS = True
    EMAIL_HOST = 'smtp.gmail.com'
    EMAIL_PORT = 587
    EMAIL_HOST_USER = 'email@gmail.com'
    EMAIL_HOST_PASSWORD = 'password'


Usage
-----
Create email template in admin interface.

Somewhere in your code use function send_templated_email()

This function requests two parameters:

 * template slug
 * context (dict)

Example:
::

    from email_templates.utils import send_templated_email

    …

    if form.is_valid():
        form.save()
        send_templated_email('new_order', request.POST)
        return render_to_response('main/feedback_ok.html', {'form': form}, context_instance=RequestContext(request))

    …

