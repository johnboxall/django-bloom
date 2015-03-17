bloom-user extends the User model much like profiles do, to contain phone numbers

# Introduction #
bloom-user is very similar to a profile.  Profiles only allow a 1 to 1 relationship with users and profiles, since a user may have more than one phone number (home, mobile, second mobile,etc) bloom.user could not be made into a profile.  Otherwise bloom.user looks very much like a standard profile.

The 2 functions that exist in bloom.user.utils are get\_or\_create\_user\_by\_phone\_number and get\_or\_create\_user\_by\_email.
Their names make what they do pretty self evident.
It allows petals like bloom.share to always associate a sharedlink with a user object for the sharer and sharee.

The only overhead to this is that when registering new users you have to check to see if they already have an entry into the system,
either an existing email or phone\_number.

If you do not find one, then create the user as usual.  If you find a match, then you can simply take the existing user object and fill in the blank fields and set the is\_active value to True.

All accounts that are created automatically by bloom.user are set to is\_active = False, this way you can track activity with non-registered users, but they cannot login until they create proper accounts.


# Installation Overview #


  * Add bloom.user to your INSTALLED\_APPS:

INSTALLED\_APPS = (
> ...
> 'bloom.user',
> ...
)

[API Documentation](BloomUserAPI.md)