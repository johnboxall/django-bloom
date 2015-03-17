The Bloom-Share API Documentation


Inside bloom.share.utils
```
		lookup_url(request, slug):
```
> Takes the request object, and the slug and returns the original full url.

```
		share_url(sharer, url, medium, sharee):
```
  * The sharer is the person who wishes to send the url to the sharee.(this is a user object from django.contrib.auth.models.User)
  * The url is the full url of the site to be shared.
  * medium is the a string indicating the way this url is intended to be shared.(ie: 'email', 'sms',etc)
  * The sharee is the person who is receiving the shortened url. (this is a user object from django.contrib.auth.models.User)
  * Returns the shortened url

```
		share_by_email(request, url, email, subject_template, body_template):
```
  * Shares the given url with the email given.
  * Uses the request object to determine the sharer(this implies that the sharer has to be logged in to share)
  * Uses the email to determine the sharee
  * The subject\_template is the template with which the subject of the email is created.
  * The body\_template is the template with which the body of the email is created.
```
		share_by_sms(request, url, phone_number, body_template):
```
  * Shares the given url with the phone\_number given using bloom.sms
  * Uses the request object to determine the sharer(this implies that the sharer has to be logged in to share)
  * Uses the phone\_number to determine the sharee
  * The body\_template is the template with which the SMS message is created.