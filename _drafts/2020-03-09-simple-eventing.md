---
layout: post
title:  "Integrating razorpay into your webapp"
date:   2020-03-09 10:03:36 +0000
categories: Messaging
---
The notion of what information should go into an event is discussed regularly, in most problem domains that use messaging. I think this subject cannot be discussed without understanding two main types of messages found in a messaging system.

## Events

An event is typically produced when some aspect of the domain (I.e., payment, booking, order) changes. OrderPlaced, PaymentSubmitted are good examples of an event. Typically, events are produced after the fact, however this is not a rule. Usually, events are used heavily with publish/subscribe messaging environment where an event could be consumed by multiple consumers. As a rule of thumb an event is produced by a producer but consumed by multiple subscribers.  

## Commands
A command is used to inform an intent (what to do next) to a receiver and typically used with point-to-point messaging. I have seen commands being used to model workflows and long running acvities that use the Saga pattern. Some examples are FraudScreenCommand, CancelBookingCommand. An effect of processing a command may result in an event (e.g., CancelBookingCommand -> BookingCancelledEvent). 

## Pause
The key difference between an event and a command is its intent. If there one thing you take away from this post, then it is the above principles.  

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
