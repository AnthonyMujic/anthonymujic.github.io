---
layout: post
title: Getting Started With Git

---


Git is an open source version control system. It is ubiquitous in the software development world, but not so in the control systems engineering space. In order to explore why this might be (or whether it should be) I decided to start using git on a toy project.

As mentioned in my last post, I am going to be using Automation Directs' Do-more Designer 1.4.3. (Note that I am not sponsored by Automation Direct, I just mention the full name and version number for the product in case you want to download it and follow along at home).

I created an example project [Pump Station 01](https://github.com/AnthonyMujic/Pump_Station) on GitHub. 

![Pump Station 01](/assets/getting started with git/PumpStation01.png)

From the few commits I have done, it is obvious that there are a few pros and cons to using git for version control of PLC code.

Pros:
<li>Any version control is better than no version control.</li>
<li>I like the git command line work flow.</li>
<li>Code can be stored for free on GitHub, or in a paid private repo, but it doubles as a way to back your code up and allows you to access your code from anywhere.</li>

Cons:
<li>PLC code is saved in a binary format, so the code file cannot be viewed on GitHub. It needs to be downloaded and opened locally in Do-more Designer.</li>

I think the issue of code being saved in a binary format is more a shortcoming of PLC programming in general. I would like to see PLC vendors taking a look at the work being done in domain specific languages and web development frameworks. PLC coding should be text based. These text files should then be able to be represented as ladder logic if that is what the electricians prefer. Perhaps higher level concepts could be used to assist development, then compiled back to ladder logic to allow debugging on-site. 

