+++
date = "2017-01-02"
title = "Turning emails to html"
image = "/images/posts/2017/email_quoted/focus_view.png"
tags = ["science", "colors", "light"]
+++

I have recently been trying to extract an email I had created on some marketing tool to reuse it to send emails natively via my tool. I am not often working with email delivery problems or similar issues. So I faced a problem I was not expecting when trying to copy my html code. The code retrieved from my email software was not plain html.

It's actually a very easy thing to fix so this post will be very short.



## Get the email source code

The first thing you need is the email source code. Every email software allows you to display the html source code, but the way to do it is different from one to another. By googling, you can find ways to do it for [Microsoft Outlook](http://superuser.com/a/390808/252074), [Thunderbird](https://support.mozilla.org/fr/questions/990484), [Mail](https://www.lifewire.com/view-message-source-os-x-mail-1172799) or [Gmail](https://www.lifewire.com/how-to-view-the-source-of-a-message-in-gmail-1172105).

The relevant part of the email starts generally with :

```
------=_Part_6472660_1251447983.1483289709958
Content-Type: text/html;charset=UTF-8
Content-Transfer-Encoding: quoted-printable
Content-ID: html-body
```

## Quoted Printable HTML

Once you got the email source, you can copy it. You will see that the code is not regular HTML. Lines end with "=" (equal signs), regular "=" are encoded like "=3D" and so on. This is the so-called [quoted-printable encoding](https://en.wikipedia.org/wiki/Quoted-printable). It allows to transmit ASCII characters over email channels.

We don't need to dig deep here, so I just paste this line from wikipedia :

>>> QP works by using the equals sign "=" as an escape character. It also limits line length to 76, as some software has limits on line length.

## How to retrieve html code from Quoted Printable encoding

Several tools exists to encode/decode your QP text into regular html code. You can for instance find :

* http://www.motobit.com/util/quoted-printable-decoder.asp
* https://mothereff.in/quoted-printable
* http://www.webatic.com/run/convert/qp.php

So, what you need to do is to copy the relevant part of the email source , copy it in some decoder, and you will get the HTML you have been looking for.

You should be good now :-)

---

Credit : Teaser photo by [Shaun Price](https://marketplace.500px.com/ShaunPrice)
