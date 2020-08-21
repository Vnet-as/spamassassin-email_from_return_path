# Spamassassin plugins to fight with spoofed email sender headers

## Functionality
1.  Compare the values Return-Path and Mime From header. It supports SRS schemas and newsletters, too
2.  Detect the presence of an email in place of the name inside of Mime From header. Triggers only in case email is detected and differs from the value of name. Eg: "spoofed@email.example" <real@sender.example>


## Required perl modules
- Email::Address
- Email::Valid

## Installation

Create plugins directory

``
mkdir /etc/mail/spamassassin/plugins/
``

and copy .pm files into it.

Enable plugins by copying vnet_plugins.cf into /etc/spamassassin/ or use your own file.

**Be sure to check & tweak the score.**

## Testing

You can check the functionaluty by "cating" an email into spamassassing like:

``cat youremail | spamassassin -D --lint 2>&1 | grep -i failed
``

Then find for terms like Spoof, FromNameIsSpoofedEmail or FromIsNotReturnPath

Enjoy!



