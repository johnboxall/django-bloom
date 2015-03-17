# Introduction #
bloom-sms is designed to use any number of SMS providers.  There is currently a connector for UpsideWireless, however it is not difficult to add other providers.

bloom-sms allows applications and other petals to make use of the SMS system to send message and receive messages from mobile phones.


Bloom.sms is based on the interaction model that SMS providers expose a web service api to send SMS messages and call a webservice api that you expose to notify you of received messages.

There is a basic widget to give you an example of how bloom.sms works.
Add bloom.sms.views.send\_sms\_view to your url patterns and it should display a basic page with a field to send a SMS message to a phone number.
This widget expects your settings.py to contain the correct values, and for the template directory bloom.sms.templates to be added to your templates directory.

# Installation Guide #

  1. Modify `settings.py`

# Installation Overview #

### 1. Modify `settings.py` ###

Add 'bloom.sms' to your `INSTALLED_APPS`:

```
INSTALLED_APPS = (
    ...
    'bloom.sms',
    ...
)
```

Configure SMS provider:

```
# SMS provider credentials
BLOOM_SMS_SERVICE_PROVIDER = 'UPSIDE'
BLOOM_SMS_SERVICE_USERNAME = 'username'
BLOOM_SMS_SERVICE_PASSWORD = 'password'

# turn on or off recording of SMS messages into the bloom.sms.models database
BLOOM_SMS_RECORD_SENT = False
BLOOM_SMS_RECORD_RECEIVED = False
```

# Provider specific settings

# Upside
BLOOM\_SMS\_UPSIDE\_TOKEN = '' # Get from Upside
BLOOM\_SMS\_UPSIDE\_SIG = '' # Get from Upside# SMS provider credentials
BLOOM_SMS_SERVICE_PROVIDER = 'UPSIDE'
BLOOM_SMS_SERVICE_USERNAME = 'username'
BLOOM_SMS_SERVICE_PASSWORD = 'password'

# turn on or off recording of SMS messages into the bloom.sms.models database
BLOOM_SMS_RECORD_SENT = False
BLOOM_SMS_RECORD_RECEIVED = False
}}}

[BloomSMSAPI API Documentation]

[BloomSMSConnector Writing A Connector]```