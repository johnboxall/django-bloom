The BloomUser API Documentation


Inside bloom.user.utils
```
	get_or_create_user_by_phone_number(phone_number):
```
  * Takes a phone\_number and either creates a user using that phone\_number or finds the existing user associated with that number
  * Returns the user object associated with the given phone\_number

```
		get_or_create_user_by_email(email):
```
  * Takes an email address and either finds the user associated with that email or creates one.
  * Returns the user object associated with the given email