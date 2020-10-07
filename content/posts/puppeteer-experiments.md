+++
title = "Puppeteer Experiments"
date = 2020-10-03T09:07:29+05:30
draft = false
+++

I presented my first public tech-talk last week at [Wroc TypeScript](https://www.meetup.com/WrocTypeScript/events/sjzhvqybcmbfc/). Due to the pandemic situation worldwide, most meetups have become virtual. So, I had the opportunity to present at a Poland-based meetup, from India!

The title of my talk was: `Cross-browser testing and automation with Puppeteer and TypeScript`. It was a code-walkthrough of sorts. The mini(some even micro)-projects I presented were:
- Hello Puppeteer : Screenshot & Image blocking demo
- Testing DOM elements using Jest + Puppeteer
- Tracking DOM value changes + GraphQL event notification (homegrown discount notification service!)
- Cross-browser and [Playwright](https://github.com/microsoft/playwright)

I had a lot of fun putting this together. Some of the things I learned in the process:
1. TypeScript in a bit more detail
2. Writing tests with Jest
3. Setting up a server running a Sendgrid email notification service
4. Setting up a Hasura event trigger, and hook it up to #3

The full talk is available to watch-
 {{youtube Mmnwv5kr7No}}

All of the project code is available in [this repo](https://github.com/meerasndr/puppeteer-experiment). The repo for the Sendgrid + NodeJS + Express based email notification service is [here](https://github.com/meerasndr/sendgrid-node-express-emailservice).

This was overall a great experience. Thanks to my colleagues Aleksandra & Marion for the encouragement and Wroc TypeScript for having me present.