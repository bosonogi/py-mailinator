py-mailinator
=============

[![Build Status](https://travis-ci.org/mc706/py-mailinator.svg?branch=master)](https://travis-ci.org/mc706/py-mailinator)
[![PyPI version](https://badge.fury.io/py/py-mailinator.svg)](http://badge.fury.io/py/py-mailinator)
[![Code Health](https://landscape.io/github/mc706/py-mailinator/master/landscape.svg)](https://landscape.io/github/mc706/py-mailinator/master)
[![Coverage Status](https://img.shields.io/coveralls/mc706/py-mailinator.svg)](https://coveralls.io/r/mc706/py-mailinator)

An python wrapper for the mailinator.com api

##Installation

Install using pip

```
pip install py-mailinator
```

##Commands

Retrieve Inbox
Get your api key at the mailinator [settings](https://www.mailinator.com/settings.jsp) page.

```
from pymailinator.wrapper import Inbox

inbox = Inbox(api_key)
inbox.get()
print inbox.messages
```

##Check Mail

```
mail = inbox.messages[0]
mail.get_message()
print mail.body
```
##Inbox Object
Methods:
* `get()` : retrieves inbox
* `count()`: run after get, gets length of inbox
* `view_subjects()`: run after get. Gets lists of subject lines of inbox
* `view_message_ids()`: run after get. Gets lists of subject lines of inbox
* `get_message_by_subject(subject)`: takes a subject as a string, returns message or list of messages with that subject
* `get_message_by_id(id)`: takes an message id as a string, returns the message if it exists
* `filter(field, value)`: returns list of message objects where message.field == value

##Message Object
Methods:
* `get_message()`: retrieves full message body and headers

Attributes:
* `id` : message id
* `subject` : message subject line
* `time` : message delivery time
* `seconds_ago` : number of seconds between time of delivery and time of request
* `origfrom` : Original from field
* `ip` : ip address the email was sent from
* `been_read` : boolean if messsage has been opened
* `headers` : only available after `get_message()`, shows the message headers
* `body` : only available after `get_message()`, shows message body

