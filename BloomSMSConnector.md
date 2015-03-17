
```
	class Connector:
		__init__()
		send_plain_sms(msg,recipient)
		verify_connect()
		was_send_successful(sms_result)
		get_fullresponse(sms_result)
```

> in addition to the class a separate receive function is needed
```
	ProviderName_receive_sms(request)
```


> Connector.init() can take as many or as few arguments as you wish.
> > Once you have defined this function, you have to update bloom.sms.utils.SendSMS() to reflect your parameters.


> Connector.send\_plain\_sms(msg,recipient) takes a msg and a single reciepient number to send the message to.
> > It returns the result value from the SMS provider


> Connector.verify\_connect() connects to the SMS provider and calls their testing function.
> > Returns the result value from the SMS provider.


> Connector.was\_send\_successful(sms\_result) takes the return value from the SMS provider and parses it to determine
> > if the status was successful.  This function exists because many providers
> > do not provider a simple boolean for status but rather a collection of
> > values that have to be evaluated to determine if the send was successful.


> Connector.get\_fullresponse(sms\_result) takes the return value from the SMS provider and creates a human readable version.
> > This function is used for debugging and for storing the fullresponse in the database when
> > > BLOOM\_SMS\_RECORD\_SENT is sent to True


> ProviderName\_receive\_sms(request) Takes the request and extracts the values from the received SMS and places them in a list to return.