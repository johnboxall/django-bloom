# Introduction #

BloomAd provides a set of template tags for inserting ads from mobile ad networks into your website. Currently Admob is supported.

Usage:

```
{% load admob %}
{% admob %}
```

Produces:

```
<img width="300" height="50" alt="Snap. Send. Share ur mobile pics" src="http://mm.admob.com/url/to/an/ad.png"/>
```

# Installation Overview #

  1. Install Bloom
  1. Signup as Admob as an ad publisher
  1. Modify `settings.py`
  1. Usage

# Installation Guide #

### 1. Install Bloom ###

The process is documented here...

### 2. Signup as Admob as an ad publisher ###

To display Admob ads you will need to signup for an Admob account:

[http://www.admob.com/s/home/register/](http://www.admob.com/s/home/register/)

Note your `admob_site_id` - you will need it soon.

### 2. Modify `settings.py` ###

Add `bloom.ad` to `INSTALLED_APPS`:

```
INSTALLED_APPS = (
    ...
    'bloom.device',
    ...
)
```

Add the settings `BLOOM_ADMOB_DEBUG` and `BLOOM_ADMOB_SITE_ID`:

```
BLOOM_ADMOB_DEBUG = True # Switch to False when you are ready to serve ads in Production
BLOOM_ADMOB_SITE_ID = 'get-from-admob' # Your Admob site ID
```

### 4. Usage ###

To display a generic Admob ad with we can use the `admob` template tag in the `admob` tag library:

```
{% load admob %}
{% admob %}
```