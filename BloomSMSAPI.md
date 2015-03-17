The Bloom-SMS API

Inside bloom.sms.init.py
```
send_sms(message, recipient_list):
```
> a wrapper function around SendSMS.send\_sms.
> It takes care of creating the SendSMS object and calls SendSMS.send\_sms for you.
> If you just want to send off an SMS message, this will be the call you want to make.
> You should only need to do it manually if you want to do something more complex than just send an SMS.

> takes an ascii txt message and sends it to every number in the recipient list.
> returns the status of each sent message as a list.
> (ie: the first response in the list matches up to the first number in the recipient list)
> Note: most SMS providers will return a positive status if the api call was successful, however this is not indicative of the status of the 		      actual message.

Inside bloom.sms.utils.py
```
SendSMS.send_sms(message, recipient_list, fail_silenty=True): 
```
> takes an ascii txt message and sends it to every number in the recipient list.
> returns the status of each sent message as a list.
> (ie: the first response in the list matches up to the first number in the recipient list)
> Note: most SMS providers will return a positive status if the api call was successful, however this is not indicative of the status of the 		      actual message.

```
SendSMS.test_connect():
```
> Tests the connection to the SMS provider.
> Returns a boolean indicating the status of the test

```
received_sms(request):
```
> Extracts the received SMS message values from the request object, and returns them as a list.