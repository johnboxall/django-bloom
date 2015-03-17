# Introduction #

BloomDevice uses [Device Atlas](http://deviceatlas.com/) to detect the browsing device from `request.META['HTTP_USER_AGENT']`. BloomDevice modifies the `request` object, adding the dictionary `request.device` which contains information about the browsing device pulled from Device Atlas.

For example:

```
>>> request.META['HTTP_USER_AGENT']

'SonyEricssonW850i/R1GB Browser/NetFront/3.3 Profile/MIDP-2.0 Configuration/CLDC-1.1'

>>> request.device

{u'mobileDevice': '1', u'displayWidth': '240', u'displayHeight': '320', u'vendor': 'Sony Ericsson',  u'model': 'W850i', ...}
```

Device detection can be used either on all requests through `bloom.device.middleware.DeviceDetectMiddleware` or applied to individual views with the decorator function `bloom.device.decorators.detect_device`.

# Installation Overview #

  1. Install Bloom
  1. Signup for [dev.mobi](http://dev.mobi/)
  1. Install Device Atlas Python API
  1. Install Device Atlas dependency `simplejson`
  1. Install Device Atlas JSON library file
  1. Test Device Atlas installation
  1. Modify settings.py
  1. Usage

# Installation Guide #

### 1. Install Bloom ###

See the Bloom installation guide here...

### 2. Signup for [dev.mobi](http://dev.mobi/) ###

You will need a dev.mobi account to download Device Atlas:

[http://dev.mobi/user/register](http://dev.mobi/user/register)

### 3. Install Device Atlas Python API ###

Download the Device Atlas Python API:

[http://deviceatlas.com/downloads](http://deviceatlas.com/downloads)

At the time of writing the Device Atlas Python API has not been packaged using `setuptools` or `distutils`. You will have to build it yourself. Start by unzipping the file into your site-packages directory in a folder called `deviceatlas`.

```
/your/site/packages/directory/deviceatlas/
```

If you're unsure where you site-packages directory is use this command to find it:

```
python -c "from distutils.sysconfig import get_python_lib; print get_python_lib()"
```

_Be sure to move the Device Atlas API into a folder called `deviceatlas`_

### 4. Install Device Atlas dependency `simplejson` ###

To use Device Atlas we'll need to install it's dependencies:

```
easy_install simplejson
```

### 5. Install Device Atlas JSON library file ###

Device Atlas works by parsing a JSON library file of device attributes. We'll need to download this file and put it in the `deviceatlas` directory we created. You can download the free Device Atlas developer file:

[http://deviceatlas.com/product](http://deviceatlas.com/product).

Once you have download the file be sure to place it in your `deviceatlas` directory.

### 6. Test Device Atlas installation ###

Device Atlas should now work. Test it from the Python interpreter:

```
from deviceatlas.api import DaApi
from distutils.sysconfig import get_python_lib
da = DaApi()
path_to_device_atlas_json = "%s/deviceatlas/DeviceAtlas.json" % get_python_lib()
tree = da.getTreeFromFile(path_to_device_atlas_json)
da.getTreeRevision(tree)
ua = 'Mozilla/5.0 (iPhone; U; CPU like Mac OS X; en) AppleWebKit/420+ (KHTML, like Gecko) Version/3.0 Mobile/1A543 Safari/419.3'
da.getProperties(tree, ua)
```

If something breaks, go back and check your steps!

### 7. Modify `settings.py` ###

Add `bloom.device` to `INSTALLED_APPS`:

```
INSTALLED_APPS = (
    ...
    'bloom.device',
    ...
)
```

### 8. Usage ###

Device detection can be used either on all requests through `bloom.device.middleware.DeviceDetectMiddleware` or applied to individual views with the decorator function `bloom.device.decorators.detect_device`.

To use the `DeviceDetectMiddleware` add it to your `MIDDLEWARE_CLASSES`:

```
MIDDLEWARE_CLASSES = (
    ...
    'bloom.device.middleware.DeviceDetectMiddleware',
    ...
)
```

To use the `detect_device` decorator, add it to specific views:

```
from bloom.device.decorators import detect_device

@detect_device
def my_view(request):
    print request.device
    ...
```