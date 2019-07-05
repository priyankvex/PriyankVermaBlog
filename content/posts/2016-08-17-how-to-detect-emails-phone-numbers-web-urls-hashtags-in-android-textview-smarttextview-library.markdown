---
author: priyankvex
date: 2016-08-17 12:53:19+00:00
draft: false
title: 'How to detect emails, phone numbers, web URLs, hashtags in Android TextView?
  : SmartTextView library'
type: post
url: /2016/08/17/how-to-detect-emails-phone-numbers-web-urls-hashtags-in-android-textview-smarttextview-library/
tags:
- android
- detect
- edit
- email
- find
- hashtag
- highlight
- in
- number
- phone
- smart
- text
- textview
- url
- view
- web
- website
---

# Smart Text View




**[Star On GitHub](https://github.com/priyankvex/SmartTextView/) [Follow On GitHub](https://github.com/priyankvex)**




Many applications in android use TextView that detects and highlight various string patterns like emails, phone numbers, web URLs and even hashtags.




This functionality is very common and and is used extensively and frequently in many app. Thus to ease the process of adding this functionality I have authored an Android library **SmartTextView.**




**Find and Star it on GitHub** : _https://github.com/priyankvex/SmartTextView_




![smart_text_view_small](https://priyankvex.files.wordpress.com/2016/08/smart_text_view_small.png)






# Features





	  * Detect emails, mobile numbers, URLs
	  * Detect #hash_tags and @mentions
	  * Use default intents or set custom callbacks.
	  * Set different colors for each pattern.




# Usage






    
    compile <span class="pl-s"><span class="pl-pds">'</span>com.priyankvex:smarttextview:1.0.1<span class="pl-pds">'</span></span>





In layout xml file




    
      <<span class="pl-ent">com</span>.wordpress.priyankvex.smarttextview.SmartTextView
    	<span class="pl-e">android</span><span class="pl-e">:</span><span class="pl-e">layout_width</span>=<span class="pl-s"><span class="pl-pds">"</span>match_parent<span class="pl-pds">"</span></span>
    	<span class="pl-e">android</span><span class="pl-e">:</span><span class="pl-e">layout_height</span>=<span class="pl-s"><span class="pl-pds">"</span>wrap_content<span class="pl-pds">"</span></span>
    	<span class="pl-e">android</span><span class="pl-e">:</span><span class="pl-e">textSize</span>=<span class="pl-s"><span class="pl-pds">"</span>9pt<span class="pl-pds">"</span></span>
    	<span class="pl-e">android</span><span class="pl-e">:</span><span class="pl-e">id</span>=<span class="pl-s"><span class="pl-pds">"</span>@+id/textView<span class="pl-pds">"</span></span>
    	/>





In java Activity or Fragment




    
    mSmartTextView <span class="pl-k">=</span> (<span class="pl-smi">SmartTextView</span>) findViewById(<span class="pl-smi">R</span><span class="pl-k">.</span>id<span class="pl-k">.</span>textView);
    	mSmartTextView<span class="pl-k">.</span>setEmailColorCode(<span class="pl-s"><span class="pl-pds">"</span>#3cb371<span class="pl-pds">"</span></span>);
    	mSmartTextView<span class="pl-k">.</span>setPhoneNumberColorCode(<span class="pl-s"><span class="pl-pds">"</span>#ff33aa<span class="pl-pds">"</span></span>);
    	mSmartTextView<span class="pl-k">.</span>setHashTagColorCode(<span class="pl-s"><span class="pl-pds">"</span>#f37735<span class="pl-pds">"</span></span>);
    	mSmartTextView<span class="pl-k">.</span>setUrlColorCode(<span class="pl-s"><span class="pl-pds">"</span>#ffc425<span class="pl-pds">"</span></span>);
    	mSmartTextView<span class="pl-k">.</span>setMentionColorCode(<span class="pl-s"><span class="pl-pds">"</span>#57b884<span class="pl-pds">"</span></span>);
    	mSmartTextView<span class="pl-k">.</span>setDetectMentions(<span class="pl-c1">true</span>);
    	mSmartTextView<span class="pl-k">.</span>setDetectHashTags(<span class="pl-c1">true</span>);
    	mSmartTextView<span class="pl-k">.</span>setText(sampleText);
    	mSmartTextView<span class="pl-k">.</span>setSmartTextCallback(<span class="pl-v">this</span>);





To use custom callbacks




    
    implements <span class="pl-smi">SmartTextCallback</span>



