+++
date = "2017-10-15"
title = "How to send SMS with Hubspot"
# image = "gtm_outbound_link_click_trigger.png"
tags = ["hubspot", "twilio", "front", "sms", "marketing", "growth"]
+++

Hubspot is getting more and more adopted in the world these days. This really nice marketing machine is now used by companies who are interacting with non tech-friendly customers. And when your customers are not tech-savvy you often want to replace email conversations for something more traditional like phone calls or text messages. Here I'm going to give you a short tutorial to show you how you can use SMS into a Hubspot workflow to get a better engagement.

Let's take for instance a fitness club which needs to advertise a special event that has to happen in a few weeks. It's quite likely that they will get a better open rate if they sens SMS to their members in addition to a traditional email.

To make the campaign a bit more complex, we will ask people to register to the event (a Hubspot landing page) to confirm their venue (attendance?). This will allow us to send a couple invitations until our contacts sign up, and it will also allow us to send an SMS before the event to reduce no-shows.


## Tools we will be using

In this tutorial we will be using the following platforms:

* Hubspot (Pro): a marketing/sales automation software. We need to have "Workflows"
* Zapier: an API connector and automation tool
* Twilio: an SMS provider
* Front (optionnal): a communication hub for emails and sms

## The summarized tutorial

To avoid you spend time in reading all the implementation details, I summarize here the main ideas behind the scenario.

* We will create custom contact fields in Hubspot. One field will be keeping the textual content, the second one (boolean) will act as a trigger to send an SMS.
* We will set up a workflow in Hubspot ; when the second field is activated, the workflow will send our contact details to Zapier via a Webhook.
* Zapier will pre-process contacts fields to extract information like {{first_name}} or {{last_name}} from our message
* Zapier will then send the mobile phone recipient together with the text message to Twilio
* The SMS emission is done by Twilio
* (Optional steps)
* To receive and save the discussion history, we will bind Front with Hubspot


## How to do that technically ?

Well, I'm updating this post in 2020, and many explaination that were described here are not valid anymore. If you want to setup a similar scenario, try to do it by following the several documentations available (HubSpot, Twilio and Zapier). Most of the steps are self explanatory but I don't want to rewrite an article that might be deprecated in a few months.

So, good luck with the implementation, and if you need help, contact me (💵💵💵).

