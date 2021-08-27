---
slides: ""
url_pdf: ""
summary: A collection of amusing, unhelpful, and sometimes annoying Twitter automations.
url_video: ""
date: 2021-08-21T00:00:00.000Z
external_link: ""
url_slides: ""
title: Twitter bots
tags:
  - twitter
  - social media
links: null
image:
  caption: ""
  focal_point: Smart
  preview_only: true
  filename: featured.png
url_code: ""
---
A collection of amusing, unhelpful, and sometimes annoying Twitter automations. Most of these are not currently running (because I’ve let them lapse, not because they were banned).

<!--StartFragment-->

# [dorf_bugs](https://github.com/RyanGoslingsBugle/dorf_bugs)

## [@DwarfBugs](https://twitter.com/DwarfBugs)

Create your own Dwarf Fortress bugs with machine learning.

This is a little toy project designed to generate sample Dwarf Fortress bug texts using a pre-trained neural network. Uses Tensorflow 1.14 and the GPT-2-simple package to do this in as few steps as possible.

![dorf_bugs](https://ryangoslingsbugle.github.io/files/twitter-bots/dorf.png)

# [album_generator](https://github.com/RyanGoslingsBugle/album-generator)

## [@YourNewAlbum](https://twitter.com/yournewalbum)

Creates randomly generated band names/album titles/covers.

I built this dumb utility to support an album generator Twitter bot. It generates artists/album names/covers according to the following schema, which I originally saw as a dreadful chain letter on Facebook:

To Do This:

1. Go to “wikipedia.” Hit “random” or click http://en.wikipedia.org/wiki/Special:Random The first random wikipedia article you get is the name of your band.
2. Go to “Random quotations” or click http://www.quotationspage.com/random.php3 The last four or five words of the very last quote of the page is the title of your first album.
3. Go to flickr and click on “explore the last seven days” or click http://www.flickr.com/explore/interesting/7days Third picture, no matter what it is, will be your album cover.
4. Use photoshop or similar to put it all together.
5. Post it to FB with this text in the “caption” and TAG the friends you want to join in.

I threw in some PIL automation, and viola, a joke that was no longer all that funny.

![album_generator](https://ryangoslingsbugle.github.io/files/twitter-bots/album.PNG)

# [seagalbot](https://github.com/RyanGoslingsBugle/seagalbot)

## [@seagalbot](https://twitter.com/seagalbot)

Uses the Imgflip API to attach a semi-randomly generated Steven Seagal film title to a Seagal-related meme image. Also includes some management code for Twitter - following back follows (DO NOT DO THIS, IT’S BANNABLE), etc.

No, I’m not sure why either.

![seagalbot](https://ryangoslingsbugle.github.io/files/twitter-bots/seagal.PNG)

# [amazinganimals](https://github.com/RyanGoslingsBugle/amazinganimals)

## [@endangeredbot](https://twitter.com/endangeredbot)

This one is quite nice really. It grabs a species listing plus an image from arkive.org, then tweets it.

Generates a single image and link, checks new followers and follows any not currently being followed with a welcome message every time it executes (NOW BANNABLE, DON’T USE), so hook it up to a crontab and go wild.

![amazinganimals](https://ryangoslingsbugle.github.io/files/twitter-bots/animals.PNG)

# [unseentng](https://github.com/RyanGoslingsBugle/unseentng)

## [@unseentng](https://twitter.com/unseentng)

Smashes together various sentence fragments and nouns to create silly-sounding but semi-plausible plot summaries for episodes of Star Trek: The Next Generation.

![unseentng](https://ryangoslingsbugle.github.io/files/twitter-bots/tng.PNG)

# [theory_bot](https://github.com/RyanGoslingsBugle/theory_bot)

## [@amarxisttheory](https://twitter.com/amarxisttheory)

Another simple one, just semi-randomly picks a noun from a txt file and tweets “Towards a Marxist theory of <noun>”.

I may have done this during a night shift, it feels like a very 4AM kind of idea.

<!--EndFragment-->