bloom-share lets you shorten urls so that they are more easily shared on character restricted mediums.

# Introduction #
bloom-share shortens urls by storing the full url in a database and doing lookups on request then redirecting to the proper url.  bloom-share exists because SMS message are only permitted to contain 140 characters, so longer/complex urls would consume too many characters in an SMS message.

# Installation Overview #

  * Add bloom.share to your INSTALLED\_APPS:

INSTALLED\_APPS = (
> ...
> 'bloom.share',
> ...
)

  * Add bloom.share.views lookup\_view to your urls patterns so that sharedlinks will resolve properly

urlpatterns = patterns('',
> ...
> > (r'^lookup/(?P

&lt;slug&gt;

[A-Za-z0-9]+)/$', lookup\_view),

> ...
)

  * Add the correct settings to your settings.py so that sharedlinks are created with the correct base url and slug length

```
BLOOM_SHARE_BASE_URL = 'http://localhost:8000/lookup'
# This is the starting length for your slug,
# if bloom creates 10 different slugs and they all find existing matches,
# then bloom will use BLOOM_SHARE_SLUG_LENGTH+1 to create the next slug.
# basically keep an eye on slug usage and increment this if your users are doing alot of sharing
BLOOM_SHARE_SLUG_LENGTH = 5
```


Now with the lookups correctly configured you can add the bloom.share functionality throughout your app .


bloom.share.utils always expects there to be a sharer and sharee user object.
You may be wondering how you would manage to always have user objects for phone\_numbers to potentially non registered users,
before you try to call share\_url you should probably read through the code in share\_by\_email and share\_by\_sms.
There is a call to functions from BloomUser that will make it easier to do such things as always have a user object associated with a number.

There are 2 basic widgets to give you an example of how bloom.share works.
Add bloom.share.views.share\_by\_email\_view and bloom.share.views.share\_by\_sms\_view to your url patterns and it should display
a basic page with a fields to share a url to an email address and to a phone number respectively.
These widgets expect your settings.py to contain the correct values, and for the template directory bloom.share.templates to be added to your templates directory.

[API Documentation](BloomShareAPI.md)