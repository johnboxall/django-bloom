# Introduction #

BloomTrack provides basic analytic for your mobile website by recording META information about all visitors. For an overview of mobile analytics, read this entry at MyMart:

[http://blog.mymart.com/2008/07/22/bango-releases-the-google-analytics-of-mobile/](http://blog.mymart.com/2008/07/22/bango-releases-the-google-analytics-of-mobile/)

BloomTrack can be used either on all requests through `bloom.track.middleware.TrackMiddleare` or applied to individual views with the decorator function `bloom.device.decorators.track`.

# Installation Overview #

  1. Install Bloom
  1. Modify `settings.py`
  1. Usage

# Installation Guide #

### 1. Install Bloom ###

Follow the Bloom install guide here.

### 2. Modify `settings.py` ###

Add `bloom.track` to `INSTALLED_APPS`:

```
INSTALLED_APPS = (
    ...
    'bloom.track',
    ...
)
```

### 3. Usage ###

BloomTrack can be used either on all requests through `bloom.track.middleware.TrackMiddleware` or applied to individual views with the decorator function `bloom.device.decorators.track`.

To use the `TrackMiddleware` add it to your `MIDDLEWARE_CLASSES`:

```
MIDDLEWARE_CLASSES = (
    ...
    'bloom.track.middleware.TrackMiddleware',
    ...
)
```

To use the `track` decorator, use it on a view:

```
from bloom.track.decorators import track

@track
def my_view(request):
    ...
```

All analytic records are stored in the `bloom_track` table.