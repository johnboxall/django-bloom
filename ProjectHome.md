Bloom is set of open source pluggable applications for rapidly developing mobile websites in Django.

# Bloom Petals #
  * BloomDevice: pluggable application for device detection using [Device Atlas](http://deviceatlas.com/)
  * BloomImage: scales images to fit mobile devices
  * [BloomSMS](BloomSMS.md): component for sending and receiving SMS messages
  * BloomAd: component for including mobile
  * BloomShare: pluggable app for sharing shortened urls
  * BloomUser: extends user model to contain phone numbers
  * BloomTrack: component for tracking page views / unique visitors

# Installing Bloom #

Download the latest stable version of Bloom:

```
$ wget http://django-bloom.googlecode.com/files/bloom-0.1.tar.gz
$ tar -tzvf archive.tar.gz bloom-0.1.tar.gz
$ cd django-bloom
$ python setup.py install
```

Or if you're feeling lucky, the latest SVN release:
```
$ svn checkout http://django-bloom.googlecode.com/svn/trunk/ django-bloom
$ cd bloom
$ python setup.py install
```

### Petal Spotlight: BloomDevice ###

BloomDevice uses [Device Atlas](http://deviceatlas.com/) to detect the browsing device from `request.META['HTTP_USER_AGENT']`. BloomDevice modifies the `request` object, adding the dictionary `request.device` which contains information about the browsing device pulled from Device Atlas.

For example:

```
>>> request.META['HTTP_USER_AGENT']

'SonyEricssonW850i/R1GB Browser/NetFront/3.3 Profile/MIDP-2.0 Configuration/CLDC-1.1'

>>> request.device

{u'mobileDevice': '1', u'displayWidth': '240', u'displayHeight': '320', u'vendor': 'Sony Ericsson',  u'model': 'W850i', ...}
```

Device detection can be used either on all requests through `bloom.device.middleware.DeviceDetectMiddleware` or applied to individual views with the decorator function `bloom.device.decorators.detect_device`.