---
author: priyankvex
date: 2018-06-03 13:14:07+00:00
draft: false
title: Creating Outbound Call Warm Transfer Using Twilio In Python and Django
type: post
url: /2018/06/03/creating-outbound-call-warm-transfer-using-twilio-in-python-and-django/
categories:
- Software Engineering
tags:
- agent
- call
- calling
- cloud
- creating
- CreatingOutbound Call Warm Transfer Using Twilio In Python and Django
- django
- hot
- inside
- outbound
- Python
- sales
- telephony
- transfer
- trasnfer
- twilio
- voice
- warm
---

![twilio-730x365](https://priyankvex.files.wordpress.com/2018/06/twilio-730x365.jpg)


Have you ever been connected to a call where it was transferred to a third person for further assistance? Well, that's call transferring.

Warm transfer of calls, in contrast to cold transfer, doesn't disconnect the call in between and thus gives the customers a  more seamless experience.

Recently at work, I was building a system to convert regular calls to a warm transfer if needed. And in this post, I'll be sharing what I learned while building the warm transfer system.


## Outbound calling and warm transfer


An outbound call is a call initiated by a call center agent to the customer. Warm transfer in the case of an outbound call means, a transfer to the second agent while the first agent is also on the call and can drop off later after introducing the customer to the new agent.

For the rest of the post, we'll be referring the parties as:



	  1. The First Agent (Leg 1 of the call)
	  2. The Customer (Leg 2 of the call)
	  3. The Second Agent (Leg 3 of the call, warm transferred to this agent)

We'll be using [Twilio](https://www.twilio.com/) to build our warm transfer system.


## Overview of the system


The system mainly follows the workflow given below:



	  1. A call is created to the first agent (leg 1).
	  2. Once the first agent is connected, call to the customer is initiated (leg 2).
	  3. When the customer picks the call, the agent and the customer are connected by a regular call.
	  4. The agent triggers the warm transfer.
	  5. The customer's leg is updated to be in a new conference call.
	  6. The first agent also joins the same conference call (Negligible delay).
	  7. Now the first agent and the customer are on a conference call.
	  8. The second agent is connected to the conference directly (leg 3).
	  9. The call is warm transferred to the second agent.

Connecting the customer and the first agent by a regular call was done both to retrofit the existing system that supported only regular calls and also not all calls will be needing warm transfers.


## 




## Connecting the first agent and the customer


First, we'll connect the first agent and then the customer. Note that customer is connected in the second leg making it an outbound call.

https://gist.github.com/priyankvex/11c391ff0a594a9824aa3ff4e144dfd3

'twiml_second_leg_url' is the URL that Twilio will hit to get the TwiML once the first agent picks the call.

We want our URL to return a TwiML Dial verb to connect the second leg to the customer.

https://gist.github.com/priyankvex/91831d714b4d8bb6e9c06344462aeaf2

Ideally, we would want our TwiML views to be stateless. Thus all the parameters needed by these views are passed as query parameters.

Note the action URL. Action URL is the URL Twilio will hit when the first leg is disconnected.

We'll use this action URL callback to connect the first agent to the conference call.

At this point, the first agent and the customer are in a regular call.

Next, we'll start the process of warm transfer.


## Triggering warm transfer


The process of warm transfer looks like following:



	  1. We move the customer the conference.
	  2. We move the first agent to the same conference. (negligible delay for humans to perceive).
	  3. We add the second agent as the participant to this conference.

**1. Updating the customer leg to be in the conference**

https://gist.github.com/priyankvex/9b56dc9327ac95fb2866b7312bd85710

We did the following:



	  1. Created a URL that the Twilio will hit to get the updated TwiML.
	  2. Updated the URL for the customer's leg by its call sid.

As soon as we update the URL, Twilio will hit the TwiMLDialConferenceView written below and will put the customer's leg in the conference.

https://gist.github.com/priyankvex/30fa20b8c69986f632edba78e6ebc1e0

**2. Putting the first agent's leg in the conference.**

Remember we gave an action URL ("first_leg_disconnected_url") for the first agent's leg when dialing the customer's leg. This is where we'll leverage it to put this leg into the same conference as the customer.

https://gist.github.com/priyankvex/375ebdc5ae886929cd62ebbf0ec43285

Twilio will hit this view when the first leg gets disconnected because we've moved the second leg of the agent to the conference call.

As we can see, we are returning TwiML to put this leg also on the conference call.

For the cases when we don't want the first leg to go into the conference upon disconnect, we can simply return TwiML HangUp verb to end the call.

So, at this point, the first agent and the customer are on a conference call.

Now, we'll take the final step towards warm transferring the call, connect the second agent to this conference call.

**3. Connecting the second agent to the conference call**

https://gist.github.com/priyankvex/e87cc0ab4f68e3b1f0fc7efd42e667f4

As we can see, to connect the second agent on the conference call we use the conferences API of the Twilio python client.

With early media set to true, we are able to listen live call status of the second agent on the conference call like ringing, busy or answered.

**4. Bonus step**

Treat yourself to a chocolate pudding! We 've implemented a warm transfer system using Twilio, Python, and Django!


## Conclusion


Outbound calls are an important factor in inside sales. Creating a seamless warm transfer can help the businesses drive conversions by connecting the customer to the right person at the right time.

In this post, we implemented an outbound call warm transfer system using Twilio, Python, and Django.


## References


1. [https://www.twilio.com/docs/voice/tutorials/warm-transfer](https://www.twilio.com/docs/voice/tutorials/warm-transfer)

2. [https://www.twilio.com/docs/voice/twiml/conference](https://www.twilio.com/docs/voice/twiml/conference)




# That’s all, folks!



