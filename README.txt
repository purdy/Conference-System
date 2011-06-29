From the author:

Welcome to the PurdyGood Conference System software. This software was 
originally written as a prototype, to learn Go and AppEngine. This software is
open source and available to take & run with, but I do plan on making some sort
of system available that uses this software that the less technically-minded can 
easily work with.

This code isn't meant to be an entire conference site. I assume you have your own
content management system or site for that. Rather, it's supposed to handle 
public registration as well as the necessary administration.

This system is built to scale. So it should be able to handle events from a
small local event to a huge conference with thousands of registrations per hour.

Basically, you log in, set up your event and point your webpage to a URL that's
provided from the system. That public URL gives people the opportunity to
register for your event (as well as manage their registration). When you log in,
you have the capability to review registrations and manage your event.

This system handles a lot of different registration workflows. You can specify
that users have to provide a generic or specific password in order to register or
allow for open registration. You can specify that registrations have to go
through an approval process. You can also specify a cost for registration,
either to be paid up-front or after approval, which uses Google Checkout, so if
you want to charge for the event, you will need to go ahead & set that up.

This system also integrates with Google Analytics, in that goal funnels and
content events are triggered as the user goes through the registration process.

Technical overview:

I haven't learned the data store stuff yet, but if I were to translate this to
how I understand relational database stuff, we would need the following tables:

account (administrator)
 - id, email, fname, lname, company

event (um, the event)
 - id, account_id, title, deadline_time, public_url

event_field (the administrator can specify what fields to ask for on the event
registration form)
 - id, event_id, weight, field_name, question, type, required

registration (the public customer of the event)
 - id, email, source

registration_field (how the public customer answered the questions)
 - id, registration_id, event_field_id, answer