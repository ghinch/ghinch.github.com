---
title:  "Mail Engine for App Engine"
date:   2011-07-13 21:24:01 -0800
excerpt_separator: <!--more-->
categories: code
tags: python appengine django
---
In the process of working on a web application that's been my a side project for a while now, I ran into the problem of needing a mail server for sending user registration emails, and possibly others in the future. Not being a great sysadmin, I didn't want to mess with running my own SMTP server, so I began a search for some kind of hosted solution.
<!--more-->
One solution I came across is a great looking app called [Postmark](https://postmarkapp.com), which provides a REST API for sending emails from your app, for a relatively small cost (1000 free, and then $1.50 for every 1000 after that). While I liked the idea, I've been wanting to do some work on Google's App Engine platform (also I'm cheap), which has an email sending service, and I know with that you get 2000 free emails every day, and additional emails cost $0.001/message (or $1 per 1000). With that in mind I threw together a little app I'm calling Mail Engine, and am releasing it open source in case other developers, like me, are looking for a hosted service, but want to save a little money (and have more control over the app to boot).

[Download from Github](https://github.com/ghinch/Mail-Engine)

At the moment there isn't too much to Mail Engine as far as features or configuration. Authentication is done is done via a simple hash token method, and other than the secret token you just need to configure a default sender and subject. Additionally you can limit which IP addresses it should accept requests from. For more information about setting it up, please see the [README](https://github.com/ghinch/Mail-Engine), also on Github.

Additionally, as I'm using this with a Django project, I threw together a simple mail backend that can be used version 1.2 or later. This should seamlessly allow you to integrate Mail Engine into your Djago app as the email service, and then easily replace it later if you need to. Both Mail Engine and the back end are released with a BSD open source license.

[mail_engine_backend.py](https://gist.github.com/ghinch/557918)
