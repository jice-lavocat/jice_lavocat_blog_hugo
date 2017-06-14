+++
date = "2017-06-14"
title = "Parse and use URL parameters in Google Tag Manager"
image = "/images/posts/2017/elokenz/appetizer.png"
tags = ["gtm", "google tag manager", "analytics"]
+++

Here is a quick Google Tag Manager tip. I recently had to help a friend to set up online sales tracking on Google Analytics. My friend was using the online learning platform [Teachable](https://teachable.com/).

Whenever someone purchased a lesson, s/he was redirected to an URL similar to the following:

>> `https://example.teachable.com/p/lesson-name?purchased=319528&purchased_course_id=012345&purchased_list_price=6800&final_price=6800&currency=EUR&user_id=5326339&email=contact%example.org&purchased_at=1497262851&is_recurring=false&tax_charge=0`


For this simple context, I just wanted to push the purchase event to Google Analytics together with the purchase price. This is how to do it:

In GTM, check into your Workspace Variables, that the built-in variable **Page URL** is checked :

<img src="/images/posts/2017/gtm/gtm_builtin_variable_page_url.png">


Then, create a new user-defined variable, I called it **Purchased Price**, and select the type **Custom Javascript** (and not Javascript variable).

<img src="/images/posts/2017/gtm/gtm_custom_javascript_variable.png">

This custom javascript variable must be a JS function that returns a single value (int, string, ...). Inside the function you can do many fancy things (see for instance Simon Avaha's post about [10 useful GTM tricks for GTM custom javascript](https://www.simoahava.com/gtm-tips/10-useful-custom-javascript-tricks/).

Here, we will reuse the built-in **Page URL** variable and extract parameters by taking advantage of the modern browsers *searchParams* JS function (be aware that the [compatibility](https://caniuse.com/#feat=urlsearchparams) is rather limited and you might want to use a longer custom function to extract the value).

<script src="https://gist.github.com/tanzaho/1482cc18b88a53646fd2040609bc3fd5.js"></script>

Now, you can use the new variable in your GA tag. This is what I have used :

<img src="/images/posts/2017/gtm/gtm_ga_push_event.png">

Save, and publish your changes. Don't forget to add the goal for this event to Google Analytics:

<img src="/images/posts/2017/gtm/ga_goal_purchase_value.png">


You should be done by now :)
