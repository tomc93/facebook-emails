Outputs a list of all your Facebook friend's email addresses in the form [username]@facebook.com, one per line. You can then copy and paste the list into the Bcc field of an email, and each of your friends will receive an individual Facebook message with the contents of the email.

`npm install -g facebook-emails`

`usage: facebook-emails [user id] [access token]`


## Access Token

Get an access token by visiting
  
[https://developers.facebook.com/tools/explorer](https://developers.facebook.com/tools/explorer)

and clicking the "Get Access Token" button. No permissions need to be selected.

## User ID

Can either be your username, which is found at the end of your profile URL, for example "loren.sandsramshaw" in:

`https://www.facebook.com/loren.sandsramshaw`

or your numerical ID.

## Send Email

Gmail has a daily limit of 500 recipients, so the list must be split up if you have more than 500 Facebook friends:

```
$ facebook-emails user token > friends
$ split -l 499 friends gmail
```

This will result in files 'gmailaa', 'gmailab', etc. Once a day (on a Mac):

`$ cat gmailaa | pbcopy`

In Gmail, using the account to which your Facebook account is tied, compose a message to yourself and paste into the Bcc field.

## Import to Google Contacts

```
$ facebook-emails user token > friends
$ echo 'E-mail 1 - Value' > contacts.csv && cat friends >> contacts.csv
```

In Google Contacts, select More -> Import and choose `contacts.csv`
  
