+++
title = 'Serverless mail send and reply using cloudflare and gmail'
date = 2024-02-15T17:24:58+09:00
draft = false
hideToc = false
tags = ["cloudflare", "gmail"]
categories = [""]
series = ""
+++

## Requirement 
- A gmail account
- A domain added to cloudflare
- No mail server self-hosting

## What you will get 
- Send and reply email using "alias@your.domain" 
- No worries about all spam, blocking

notice this should also work with other email providers, with little tweaks.

## cloudflare side

1. Login to [cloudflare dashboard](dash.cloudflare.com), go to `Websites` -> chose your site -> `Email Routing`
2. Add rules in `Routing rules` section, the alias will be `alias@your.domain`-ish
3. An email will be sent to your gmail for verification

## gmail side

1. `Google Account Setting` -> `Security` -> enable `2-Step Verification`
2. Goto https://myaccount.google.com/apppasswords, create an app password(will be used later), copy the password (**remove the space in between!**)
3. Goto mail settings -> `Accounts and Import`, in the `Send mail as` section, choose add, 
4. A window pops up, and
    - The first page is about the mail alias we talked in last section. Normally you would also uncheck "Treat as an alias."
    - The second window is **not** the cloudflare SMTP settings! SMTP Server: `smtp.gmail.com`, Username: the **gmail** name(**without** @gmail.com), Password: the SMTP app password you generated before
    - Check you inbox for a verification mail and youre good to go!

ps: You can also "make default" your alias in the `Send mail as` section if you like:)
