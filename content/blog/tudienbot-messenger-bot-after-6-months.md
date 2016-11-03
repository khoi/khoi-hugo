+++
date = "2016-11-01T12:10:02+07:00"
draft = true
title = "#6 Tudienbot - A messenger bot after 6 months"
slug = "6-tudienbot-messenger-bot-after-6-months"
+++

At the F8 Conference in April, Facebook introduced the Messenger Platform API, opened the new era for messaging and conversational bot.

The Facebook's presentation was phenomenal. The API interface is dead simple, with rich content enabled to enhance the users' textual experiences. The ability to reach 900M monthly active users seems really promising. And I just couldn't wait to try that out.

For those of you who're too lazy to read the whole post, try sending some English to [Tudienbot](https://www.facebook.com/tudienbot/?fref=ts). The source code is also available on [Github](https://github.com/khoiln/tu-dien-bot)

<center>![westworld](https://media.giphy.com/media/l0MYAIq2BLGmORX1u/giphy.gif)</center>
<center>*In pursuit for my own Dolores* 😂</center>

### Finding The Idea

I wanted to start with something not to difficult to implement in order to understand the platform API first. After given it some thoughts, I decided to build a version of English Vietnamese dictionary so when the users send the bot a word or a sentence preferably in English, it would respond with the translated content.

### Building the bot

- First we need to setup the Facebook Page and App. *I wont go in to detail on this since Facebook has an pretty thorough tutorial [HERE](https://developers.facebook.com/docs/messenger-platform)*

- Now it's time to actually doing some coding. First we need the database somehow, luckily there is [The Free Vietnamese Dictionary Project](http://www.informatik.uni-leipzig.de/~duc/Dict/) that provides some popular dictionaries in Opendict format. Converting the file to JSON files that are later used for MongoDB is trivial enough with the open [Dict Protocol](http://www.dict.org/links.html)

- I quickly put together an ExpressJS app that serves as the API server for the platform API. At first, it looks up for the explaination in the dictionary and returns the output, simple as that.

<center>![tudienbot-lookup](/images/tudienbot-1.png)</center>

- Then I doing some test runs and quickly found couple problems, if the returned text is longer than 320 characters, Facebook will simply reject it and users get no response. So I have to put together a `smart split` functions that explode long text in to < than 320 chunks with `newline` taken in to account.

<script src="https://gist.github.com/khoiln/ec7c9c126ba4e1f1d7815761e61579f5.js"></script>

- Problem solved right? Not quite, now I noticed that the chunks would come in random order making the text unable to comprehend. That made sense since we're just sending the chunks to Facebook without and didn't care about the order. So we have to put everything in to a queue somehow. Luckily, [async](https://github.com/caolan/async) comes to the rescue, just wrapping our current `sendMessage` function and we are good to go.

<script src="https://gist.github.com/khoiln/1db7cc9bca909fc0cdc0c43a27b3e0fc.js"></script>

- At this time, I thought the bot is pretty solid now, so I submitted the bot to Facebook for review. It was 3 days after the Messenger Platform API announcement. Facebook said it would take 1 week to review, the bot got approved after 4 days. I checked the inbox of `Từ Điển Bot` and saw the Facebook's reviewers actually test out the bot just like normal users.

<center>![tudienbot-review](/images/tudienbot-2.png)</center>

- Now it's officially one of the first Messenger bot that is public, ready to be abused by the great humanity. I composed a quick instruction post, then put it on [Launch](https://www.facebook.com/groups/launchpad/) (an amazing group of Vietnamese entrepreneurs). The feedbacks were great, people liked it. Tudienbot got overwhemedly by thousands of queries. Watching your new born baby bot get abused by the people gave me a very strange feelings indeed.

<center>![tudienbot-review](/images/tudienbot-arabic-3.png)</center>
<center>*People even test out Arabic*</center>

- Sometimes, I and Quan Nguyen (another friend that helping me manage the page) personally monitor the conversations and also jump in to provide the correct and proper translation for people :).

<center>![tudienbot-review](/images/tudienbot-4.png)</center>


