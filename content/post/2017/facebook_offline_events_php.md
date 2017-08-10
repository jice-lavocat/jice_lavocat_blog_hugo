+++
date = "2017-08-10"
title = "Send Offline Events to Facebook Ads using PHP"
image = "/images/posts/2017/facebook_offline/facebook_offline.png"
tags = ["facebook", "api", "php", "advertisement", "ads"]
+++

If you are using Facebook Ads, chances are that you are simply using the conversion pixel and [standard events](https://developers.facebook.com/docs/ads-for-websites/pixel-events/v2.10) to optimize your bids. But in complexe scenarios, you cannot use live events, and you need to switch to Offline events instead.

What we're going to see here, is how to send a purchase events to Facebook, when this purchase has been created/validated manually by the admin via a back office.

I recently had to help implementing [Facebook Offline Events](https://developers.facebook.com/docs/marketing-api/offline-conversions/v2.10) in a PHP environment. The client that needed to have offline events was an online retailer selling expensive products. He couldn't simply accept online orders, he also needed to verify each single one before sending the purchase. Their internal workflow was designed in this way to avoid frauds. In addition to that, as products are expensive, purchasing with a credit card could lead to payment issues with banks. So most customers like to purchase via bank transfers instead.

The shop had a custom Prestashop installation (so, it's built with PHP), but the script I'm going to share below can also be used on any other PHP-based shop (Magento, WooCommerce, Open Cart, Sylius, ...).


## General Setup

Here we will assume that you want to optimize Facebook Ads based on purchases and that work with an online platform that allows you to validate purchases manually. When these purchases are validated, you can run a script that will POST a hit to Facebook API with all necessary data.

I'm not going to explain the general setup on Facebook Business Manager since it's already in the [documentation](https://developers.facebook.com/docs/marketing-api/offline-conversions/v2.10). What you have to know it's that it's cumbersome. Honestly, you need to perform 15 or 20 steps before getting your `access token` and `offline_event_set_id`.

So, let's assume that you manage to get these two information, what you need now is to find where the validation occurs in your code. You will need to place a hook, or insert your custom script here. I'm not giving any details here since it really depends on the platform you're using. The script should be able to access _user_ (email, contact info) and _purchase_ (amount) variables.

>>> **A side note on user privacy**: Facebook Ads is much more intrusive in terms of privacy than Google Adwords. Google Adwords, would provide you with unique anonymous IDs that you need to send back to the platform. On the contrary, with Facebook, you have to send the more information you can, so that Facebook can try to match your customer with an existing user. At the end, Facebook will know what your company earned and from who.

Cutting a long story short, here is the piece of code I used to send data to Facebook Ads via a call to cURL :

<script src="https://gist.github.com/tanzaho/163d5b8f269a08b65ac6a66f38905d71.js"></script>

## Test your code and accept ToS

You can try to run this script alone first to see if it's working with your `access token` and `offline_event_set_id`. One issue I have been faced first was that running this script led to an error. After a few attempts, the error message returned by Facebook informed me that I had to accept specific Terms of Services for using offline events. Once it was done, the script was working perfectly.

If the script works, Facebook would return with a code like : `Result encode{"id":"your_offline_event_set_id","num_processed_entries":1}`. Otherwise you will read an error message.

When everything is working, you can browse to your business manager and check [offline events](https://business.facebook.com/offline_events/). It will look like the following.

<img src="/images/posts/2017/facebook_offline/facebook_offline.png">


Was that working for you ?

If yes, you can proceed to the custom install in your own framework. Good luck.
