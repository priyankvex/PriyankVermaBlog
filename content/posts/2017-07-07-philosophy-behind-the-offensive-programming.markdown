---
author: priyankvex
date: 2017-07-07 19:30:08+00:00
draft: false
title: Philosophy Behind The Offensive Programming
type: post
url: /2017/07/08/philosophy-behind-the-offensive-programming/
categories:
- Software Engineering
tags:
- decorator
- defensive
- exception
- interface
- introduction
- is
- java
- of
- offensive
- podcast
- programming
- Python
- software engineing
- square
- what
- zen
---

![football-1149952_640](https://priyankvex.files.wordpress.com/2017/07/football-1149952_640.jpg)


Recently I was listening to a podcast and there was this really smart guy Piwai talking about something that instantly captivated by attention. That was the coining of the term **Offensive Programming.**

**What is offensive programming?**

Well, you can find the literature on  Wikipedia and also I am not the best person to explain that. So check that out please. But fundamentally, _offensive programming _refers to a style of programming that is exact opposite of the more famous counter-part _the defensive programming._

_Defensive programming_ refers to coding style which adheres to dealing gracefully with conditions that should not happen.

_Offensive programming _on the other hand, well just tells you to let the app crash. Don't try to recover, don't try to handle the exception, just log the stack trace and crash.

The reason behind this is that in reality the problem can be much bigger and somewhere else in the code, as a side effect of you are getting this error in first place. This forces you to fix the problem at the source and will possibly result in a healthier code base.

**When it makes sense to be offensive?**

This was my exact concern while I was listening to this podcast. Thankfully, Piwai answered that himself. I also, talked about it with a really smart guy at the office and he also made the same remarks.

So at Square (the company who do payments and author libraries) what they do is, they stick to a defensive style of programming  for interfaces and parts of code that deals with external interfaces and/or user interactions. Basically, something that is not in your control.

But, for the internal interfaces, where the classes you wrote are going to interact with each other, you don't have to be that paranoid about that. This is where he (Piwai) said you should switch to the _offensive _approach. You have full control over the classes you wrote, and the expected behaviour is in your control. If it fails to do so, it's better to just crash and let the problem to be fixed at the source.

That is the exact reason he said at Square, they make very liberal use of assertions in the code. Assertions are not forgiving at all.

**Example Please!**

I would attempt to point to examples here, one that the Piwai himself talked in very brief and the one that I've encountered myself where I thought it made sense.

In this example, say we are handling credit card objects. There is no point to internally validate the credit card object every time you deal with it.

As soon as we get a credit card, we decorate it with a validated credit card. That's all the defensiveness we had to offer.

Now internally, we go offensive and throw exceptions or assertions every time we encounter an invalidate credit card object.

The code below is not perfect, but can give you an idea.




    
    <span style="color:#008800;font-weight:bold;">class</span> <span style="color:#bb0066;font-weight:bold;">ValidatedCreditCard</span> <span style="color:#008800;font-weight:bold;">extends</span> CreditCard<span style="color:#333333;">{</span>
    
        CreditCard creditCard<span style="color:#333333;">;</span>
    
        ValidatedCreditCard<span style="color:#333333;">(</span>CreditCard creditCard<span style="color:#333333;">){</span>
          <span style="color:#888888;">// Handling external user interactions defensively.</span>
          <span style="color:#008800;font-weight:bold;">try</span><span style="color:#333333;">{</span>
    	creditCard<span style="color:#333333;">.</span><span style="color:#0000cc;">validate</span><span style="color:#333333;">();</span>
          <span style="color:#333333;">}</span>
          <span style="color:#008800;font-weight:bold;">catch</span> <span style="color:#333333;">(</span>CreditCardValidationError e<span style="color:#333333;">)</span> <span style="color:#333333;">{</span>
    	<span style="color:#888888;">// Handle and try to fix the error</span>
    	tryToFixTheCardDetails<span style="color:#333333;">();</span>
          <span style="color:#333333;">}</span>
          <span style="color:#008800;font-weight:bold;">this</span><span style="color:#333333;">.</span><span style="color:#0000cc;">creditCard</span> <span style="color:#333333;">=</span> creditCard<span style="color:#333333;">;</span>
        <span style="color:#333333;">}</span>
    <span style="color:#333333;">}</span>
    
    <span style="color:#008800;font-weight:bold;">public</span> <span style="color:#008800;font-weight:bold;">static</span> <span style="color:#333399;font-weight:bold;">void</span> <span style="color:#0066bb;font-weight:bold;">main</span><span style="color:#333333;">(</span>String<span style="color:#333333;">[]</span> args<span style="color:#333333;">){</span>
    
        CreditCard c  <span style="color:#333333;">=</span> getCreditCardFromUser<span style="color:#333333;">();</span>
        c <span style="color:#333333;">=</span> ValidatedCreditCard<span style="color:#333333;">(</span>c<span style="color:#333333;">);</span>
        <span style="color:#888888;">// Time to go offensive</span>
        <span style="color:#888888;">// ...</span>
        <span style="color:#008800;font-weight:bold;">if</span> <span style="color:#333333;">(</span>c <span style="color:#333333;">==</span> <span style="color:#008800;font-weight:bold;">null</span><span style="color:#333333;">){</span>
          <span style="color:#008800;font-weight:bold;">throw</span> <span style="color:#008800;font-weight:bold;">new</span> <span style="color:#0066bb;font-weight:bold;">CardInvalidException</span><span style="color:#333333;">();</span>
        <span style="color:#333333;">}</span>
    <span style="color:#333333;">}</span>





Another example I can think of is a much simpler one and more relatable.
Suppose, we have a utility function that uploads a file to s3.
It would make sense to follow offensive programming style and just throw an exception if somehow they file or the key reaching the function is None.




    
    <span style="color:#008800;font-weight:bold;">def</span> <span style="color:#0066bb;font-weight:bold;">upload_file_to_s3</span>(<span style="color:#007020;">file</span>, key):
        <span style="color:#008800;font-weight:bold;">if</span> <span style="color:#007020;">file</span> <span style="color:#000000;font-weight:bold;">is</span> <span style="color:#007020;">None</span> <span style="color:#000000;font-weight:bold;">or</span> key <span style="color:#000000;font-weight:bold;">is</span> <span style="color:#007020;">None</span>:
    	<span style="color:#008800;font-weight:bold;">raise</span> <span style="color:#ff0000;font-weight:bold;">TypeError</span>
    







**Few more tips from the podcast**

**1. How to start with offensive programming?**

Best way is to start putting assertions in the code, where you think is suitable. Yeah, we'll experience more crashes and that's awesome!

Because now we know that we have a problem.

**2.  We feel more confident about the code base:**

We just know that, this method doesn't try to handle nulls, thus I can confidently say that it was not null or it would've crashed.

**3. Do incremental roll outs.**

When you ship a code, roll it out like for 1% of users. We'll have a ton of crash reports, and that's good! I mean not for the 1% users but they are taking one for the team!

**4. Crash at preventable errors and recover from expect-able errors :**

Preventable errors are invalid arguments, NPEs etc. Go offensive on these.

Expectable errors are like resource depletion, invalid user inputs etc.

Try to recover from these.



Overall, it was nice to listen to a guy who works at a company like Square talking about how they use _offensive programming _for a healthier code base. And if Square is doing something, we all can learn something from that!
