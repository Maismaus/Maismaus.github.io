---
title: "Tips for the next Mendix Capture the Flag event"
# description: "How to find the best hardware for Mendix developers"
author: "Marius"
url: "/blog/capture-the-flag-tips"
date: "2025-10-18"
tags: ["Mendix", "Development", "Tips", "Challenge", "CTF"]
cover:
   image: "header.png"
   alt: "Hero image for tips on the next Mendix Capture the Flag event (AI generated)"

ShowReadingTime: true
hidemeta: false
showtoc: false
# draft: true
---

After winning [this year's](https://www.linkedin.com/feed/update/urn:li:activity:7383427955881824257/) Mendix Capture the Flag event, many people have asked me for tips. I wrote this writeup with my insights for next Capture the Flag events. Read on to learn more!

## Recap

The Capture the Flag event consisted of three difficulty levels: Pizza Mario (beginner–medium), Patient Portal (hard–insane) and Magic level challenges. In total, you had about 30 hours to complete the 26 challenges. Since we solved 24 challenges (and also ate and slept), this leaves about 20 hours of hacking, which means solving approximately one challenge every hour of hacking. Time is of the essence, and working efficiently is important.

## Strategy

The first thing our team did after the kickoff is talk strategy. There is no single "ultimate" strategy that you should follow, but I think _having_ a strategy defined in your team helps you to focus and work efficiently. 
In our case, we decided to start with the Patient Portal challenges to crack some difficult cases first. We could then do the easier Pizza Mario challenges the next day when we were expecting to be more tired. We left the Magic challenges for last since they are usually not time-efficient to solve.
In previous years we even used a Trello board to track each challenge, but since our team was smaller this year, we didn't feel the need for that this time around.

We then mostly worked on challenges individually, but always communicated which challenge we were working on, so as not to do double work.

## Technical requirements

Of course, there are some requirements before you can get started. These are my personal recommendations:

- **Burp Suite** – Required for analyzing and manipulating browser traffic.
- **Ciphix DevTools** – The tool provides nothing that you cannot do through JavaScript, but it makes it much easier. Make sure you have a version that works on all Mendix apps. Because of the strict mode in Patient Portal, I hardly used it this year.
- **VS Code** – Better editing, built-in error checking, and easy script/data management compared to the browser console.
- **Slack** – Useful for communicating with your team in a separate channel. When you want to switch to another challenge, make sure you update your team with your latest findings.
- **Mendix Studio Pro** – Installing the same Mendix version eliminates the possibility of differences between platform versions. 
Rebuilding the challenge app yourself (especially the domain model) can help you visualize the problem.
- **Excel** – I use Excel to track objects that I found, such as guids or other interesting data points.

## Hacking tips

#### Understand developer mistakes
Most challenges emulate a real-world scenario, including common mistakes. For any challenge:
- Read the description.
- Realize what the developer tried to do.
- Try to figure out what they actually did.
- Realize what common mistakes are when modelling these requirements.
- Exploit those mistakes.

#### Understand web security principles
The hacking challenges provided during the CTF are not unique. Most are either part of [The S-Unit Top 10](https://the-s-unit.nl/the-s-unit-top-10/) or [OWASP Top Ten](https://owasp.org/www-project-top-ten/) application security risks. Make sure you understand these and are able to find and exploit them. SQL injection, cryptographic failures and cross-site scripting (XSS) are all vulnerabilities that played a part in this or previous CTF events.

Luckily, Mendix covers most of the security issues in our day to day work. The features available in Mendix don't contain any security issues by default, unless a developer made mistakes in its implementation. That's why you should always be on the lookout for any custom built methods, which can re-introduce common vulnerabilities.

#### Understand client – server communication
Mendix apps are web-based applications. They are rendered in a browser, and the webapp communicates with the server. Understanding this principle is essential.

HTTP is [stateless](https://stackoverflow.com/questions/4913763/what-does-it-mean-when-they-say-http-is-stateless):

> EVERY resource that is accessed via HTTP is a single request with no threaded connection between them. If you load a web page with an HTML file that within it contains three <img> tags hitting the same server, there will be four TCP connections negotiated and opened, four data transfers, four connections closed. There is simply no state kept at the server at the protocol level that will have the server know anything about you as you come in.

**What does this mean in the context of a CTF?** This means that the client and server must communicate expectations. When clicking a button, the client already knows the request it needs to send to the server in order to execute the buttons functionality. 

Conversely, when a server receives a request, it has no context about the request. That's why you send a session ID for authentication and the full context of what you are trying to do in the request body. The server then blindly executes your request, but it doesn't know anything about its context except what is supplied in the HTTP request.

All this metadata can be analyzed (and altered) in Burp Suite. 

So when approaching any hacking challenge, make sure you understand that what you see in the browser is just the tip of the iceberg, and the underlying data provides a treasure trove of information. Understanding the inner workings of the Mendix client is essential for hacking it.

#### Understand the JavaScript API
Once you understand the client – server relationship, you can start to dive into the functions that the browser has available. Most of this is done through the [Client API](https://docs.mendix.com/apidocs-mxsdk/apidocs/client-api/). You should be able to write and execute Client API JavaScript.

It also helps to have a repository of common scripts, for which I use my own [Docs](https://www.mariusvanderknaap.nl/docs/).

#### Understand cryptography fundamentals
Many security challenges involve an encoding, encryption or signatures of some sort. All of these were used in one or more challenges this year. You don't need to be an expert in these, but understanding how they work and their flaws might just lead you to a flag. 

If you want to practice with these, you can use [Hack This Site](https://www.hackthissite.org/) which offers traditional coding hacking challenges.

### Conclusion
With this blogpost, I hope to give some insight into the fundamentals that go into solving the CTF challenges. I hope this helps you prepare for next year. Until then!