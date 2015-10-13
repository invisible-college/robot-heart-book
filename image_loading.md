# Image Loading

The visual appearance of your app is the primary way most users will grasp it with their brains and touch it with their fingers. You can get pretty far with text, but eventually, you will want to include images, either those that you create yourself or that you find or acquire elsewhere on the internet.

A Note About Copyright
======================

In this radical age of information exchange, it's pretty fashionable to appropriate content on the web and think you are sticking it to the man. Fucking fat cat media companies, am I right? While it's fine to enact your anarchist agenda by using the socialist structure of the internet, let's first be aware of all the rules we are breaking, and of all the different rules we can agree to in order to share content and reward content creators.

When I was a poor student, I felt like the world owed me their content. It was an abundant resource, and who was I hurting if I scraped some pictures off Google Image Search. However, with age I've had time to develop a sense of morality. My current moral code is that I want to reward content creators by sending honest signals, so that they will create more awesome content. I am 

When I use the term media, I'll mean any image, sound clip, MP3 song, video, font. In short, any kind of digital asset that is passive data that is created and transmitted. This is to distinguish it from code, or active data, data that is meant to be interpreted. [Is this distinction really necessary?] This is a fine line to draw, and it's one that many developers make simply due to the way files are stored, organized, and loaded in an Android project.

One of the most common licenses of media on the web is written by Creative Commons. Creative Commons is a non-profit organization started by Lawrence Lessig (fact-check this) to evolve and safeguard our civil liberties while keeping up with our modern technological age, where reproduction is easy and a culture of sharing on the internet is assumed.

The Creative Commons Sharealike License (non-commercial attribution) lets artists and content creators share their latest artwork online.

Static and Dynamic Images
=========================

We don't mean here ``dynamic`` as in moving images, those would be movies right? Or those animated gifs which used to be totally lame in the early web of the 2000s but have since been repurposed for technical howto screenshots and giphy.

Images themselves can be included directly into your app. That means they can be compiled into your APK, checked into GitHub, and uploaded along with your code to the Google Play Store. As a result, you want to be judicious about your use of these images to keep your app slim and agile, easy to download and transfer. The advantage of these images is that are available immediately to your users when they run your app, even if they don't have a network connection at the time. They usually include all the icons in your app, which are, after all, just little images. These are called *static* because they are fixed as part of your app's image. (Image in this case refers to the binary output file, APK).

Images that are not included directly in your app need to be loaded afterwards. These are called *dynamic* because rather than being available once and always when you load your app, they need to be requested over the internet.

Just like the terms static and dynamic mean elsewhere in computer science.

Here would be a great place for a sidebar or table summarizing the differences.

| 0:0 | Static | Dynamic |
| --  | ------ | ------- |
| Uses | Icons, logos, splash screens | Product images |
| Advantages    | Available immediately on app download. | Can scale with your data, change after compilation. handle future cases.  |
| Disadvantages | Can make APK large | Can be slow, more complicated to load. |

In the following sections, we'll discuss icons and static assets, where to include them in your Android project. 

Picasso
=======

Picasso was a great artist, one of the leader of the movement called Cubism. He also had a renowned sense of personal flair, was a well-known womanizer, and a fiery temperament.

It is somewhat appropriate that a library which makes it easy to load beautiful and interesting images into your Android app would also be named Picasso. Although to be totally appropriate, it would skew the images into interesting angles and render a non-representational artistic view, perhaps colored by the horrors witnessed during World War I.

Picasso is an open source project contributed by Square, makers of the phenomenally-successful credit card reader that plugs into your smartphone or tablet's audio jack. This may seem strange, like Amazon going into the web services business, but I'm sure in retrospect it will make a lot of sense.

Picasso is an example of a third-party JAR file. The way we include it in our project is the same as any other third-party library. These were not created by Google, the original creators of the Android platform (these would be first-party) nor were they commissioned by Google specifically for their platform (these would be second-party). So now you know all the different kinds of parties there are in software creation and distribution.

Adding a Third-Party Library
============================

1. Download the jar file (in this case, picasso-2.5.2.jar) from Square's github page: http://square.github.io/picasso/
2. Move it into your main module (usually called app) into the lib directory.
3. Add it to your build.gradle.
