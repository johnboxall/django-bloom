# Introduction #

Based on information from BloomDevice, BloomImage resizes images to fit the full width of a mobile device. For example, if you are browsing with a mobile device that has a screen width of 200px - BloomImage will resize a source image to have a width of 200px. This works well for site banners and images that should take up the device's entire screen.

Example:

```
{% load device_image %}
{% device_image "image.jpg" 75x75 as image %}
<img src="{{ image }}" width="{{ image.width }}" height="{{ image.height }}" />
```

Produces:
```
<img src="http://example.com/static/image_jpg_200x200_q85.jpg" width="200" height="99" alt="" />
```

# Installation Overview #


  1. Install Bloom
  1. Install BloomDevice
  1. Install the [Python Imaging Library](http://effbot.org/zone/pil-index.htm) (PIL)
  1. Install `[http://code.google.com/p/sorl-thumbnail/ sorl-thumbnail]`
  1. Modify `settings.py`
  1. Usage

# Installation Guide #

### 1. Install Bloom ###

See the tutorial here...

### 2. Install BloomDevice ###

To install Bloom Device follow the steps in the installation guide:

[http://code.google.com/p/django-bloom/wiki/BloomDevice](http://code.google.com/p/django-bloom/wiki/BloomDevice)

### 3. Install the [Python Imaging Library](http://effbot.org/zone/pil-index.htm) (PIL) ###

BloomImage requires the image manipulation functions provided by the PIL. Installing the PIL is currently out of scope for this guide. Here are links to get you started:

  * [Python Imaging Library](http://effbot.org/zone/pil-index.htm)
  * [Google Guide to Installing PIL](http://code.google.com/appengine/docs/images/installingPIL.html)

### 4. Install [sorl-thumbnail](http://code.google.com/p/sorl-thumbnail/) ###

[sorl-thumbnail](http://code.google.com/p/sorl-thumbnail/) is a pluggable Django application used for creating thumbnail images. It also works for generating images for mobile devices. You can check it out from Google Code:

```
svn checkout http://sorl-thumbnail.googlecode.com/svn/trunk/ sorl-thumbnail
```

At the time of writing `sorl-thumbnail` has not been packaged so you will need to place it in on your Python Path yourself.

### 5. Modify `settings.py` ###

Add `sorl.thumbnail` and `bloom.image` to `INSTALLED_APPS`:

```
INSTALLED_APPS = (
    ...
    'bloom.device',
    'sorl.thumbnail',
    'bloom.image',
    ...
)
```

### 6. Usage ###

BloomDevice generates images that fit the full width of the browsing mobile device. To use BloomDevice, load the `device_image` template tag library and use the template tag `device_image`:

```
{% load device_image %}
{% deviceimage "path/to/image.jpg" 75x75 as image %}
<img src="{{ image }}" width="{{ image.width }}" height="{{ image.height }}" />
```

Note that "path/to/image.jpg" is prepended with `MEDIA_ROOT`. `75x75` means that if no device information is found, set the image to this size.