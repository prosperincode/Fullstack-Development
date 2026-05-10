---
title: "Stop Writing React Native Styles Like It's 2022"
source: "https://www.youtube.com/watch?v=J8hmOaA5uzc&t=315s"
author:
  - "[[Code with Beto]]"
published: 2026-04-09
created: 2026-05-10
description: "Master React Native with me → https://cwb.sh/rn?r=ytFive built-in React Native style properties — Linear Gradient, Filter, Box Shadow, Gap, and Mix Blend Mode. Even AI agents consistently get wrong."
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=J8hmOaA5uzc)

Master React Native with me → https://cwb.sh/rn?r=yt  
  
Five built-in React Native style properties — Linear Gradient, Filter, Box Shadow, Gap, and Mix Blend Mode. Even AI agents consistently get wrong.  
  
Resources mentioned  
• Blog - Agent Rule: https://codewithbeto.dev/blog/react-native-styles-you-didnt-know-existed  
• This Week In React Newsletter: https://cwb.sh/twir?r=yt  
  
My Products  
• Pro Access — get access to everything: https://cwb.sh/pro?r=yt  
• React Native Course: https://cwb.sh/rn?r=yt  
• Platano — AI app template: https://cwb.sh/platano?r=yt  
• Book — From Idea to App Store with Claude Code: https://cwb.sh/book?r=yt  
• Inkigo — AI Tattoo (iOS): https://cwb.sh/inkigo?r=yt  
• Quick Push — test push notifications (macOS, $4.99): https://apple.co/4tvT4wF  
  
Free Resources  
• Newsletter: https://cwb.sh/newsletter?r=yt  
• Discord: https://cwb.sh/discord?r=yt  
  
Support My Work  
• Channel Membership: https://cwb.sh/join  
• GitHub Sponsors: https://github.com/sponsors/betomoedano  
  
Socials  
Follow Beto on X: https://cwb.sh/x?r=yt  
LinkedIn: https://cwb.sh/in?r=yt  
GitHub: https://cwb.sh/gh?r=yt  
Instagram: https://cwb.sh/insta?r=yt  
TikTok: https://cwb.sh/tiktok?r=yt  
Threads: https://cwb.sh/threads?r=yt  
Bluesky: https://cwb.sh/bsky?r=yt  
Facebook: https://cwb.sh/fb?r=yt  
  
Timestamps  
00:00 Intro  
00:42 #1 Linear Gradient (backgroundImage)  
02:14 #2 Filter  
03:14 #3 Box Shadow  
05:05 #4 Gap  
05:56 #5 Mix Blend Mode  
07:17 Bonus: Free Agent Skill  
  
#coding #mobileappdevelopment #reactnative

## Transcript

### Intro

**0:00** · There are five React Native styles hidden in plain sight that most developers never use And if you're using AI to build your application your AI is definitely missing them too So knowing about them will instantly level up your UI your code quality and you'll get more polished results without installing any third-party library Hey if you're new here I'm Beto I've spent years building mobile applications at Walmart then at Expo as a developer success engineer and now I run Code with Beto full-time where I help developers master mobile development in the AI era If you

**0:31** · want tips like this every week check out our newsletter and don't forget to join our Discord community Link's in the description This is gonna be a quick one so make sure to stick till the end I have a surprise for you Let's dive in I know I know If you come from the web Linear Gradient it's been available for ages You lucky

### 1 Linear Gradient (backgroundImage)

**0:50** · But previously in React Native you had to install a third-party library like Expo Linear Gradient or React Native Linear Gradient But thank God now it's available on there the experimental background image style property And you can use it like you would use it on the web with CSS Just pass the string with the Linear Gradient that you want to use And one thing that really annoys me is that agents always miss this property and they try to install extra libraries

**1:18** · So you can actually just do it like this Super easy But this API it's actually pretty powerful because it's completely compatible with web I actually took this example from the Mozilla website It's documentation So you can do pretty crazy things like starting from red 20% of the space but you can always tweak this let's say 30 or 3%

**1:39** · And now you can see we get the fade Then you can define the next color like orange from 20% to 40% but you can also change this to be maybe 30 like this And now you get this fade effect But if you define exactly where you want the color to end so we want red to be 20% and then from 20 to 40

**1:59** · we want orange Then yellow from 40 to 60 green from 60 to 80 And you get the point Very versatile very complete And it works on Android Here's an Android It looks the exact same way Filter landed in React Native 76

### 2 Filter

**2:17** · along with the new architecture This is the syntax You just pass the filter and then you can pass the string like blur You can also do crazy things like invert change the brightness and opacity for the views And here I have an example Now the only thing about filter is that it's actually pretty limited on iOS which is funny iOS always gets the latest and greatest but actually filter only supports brightness and opacity on iOS And the rest like saturate invert blur

**2:47** · it's only available on Android So with Android we can use anything that we want like filter blur with eight pixels This is how it looks We can invert and get these amazing effects You can see the original on the left and then with brightness on the right So pretty cool especially the blur effect but you would need to have an extra library for iOS That's the annoying part but I think blur should land on iOS soon

### 3 Box Shadow

**3:14** · Next one box shadow This one guys it's pretty annoying when you are generating code with AI and it's using the old syntax So if you've been using React Native for a while you know that we have the shadow color shadow offset all these properties that at the end of the day it's pretty hard to code and remember all these properties And they also look different on iOS and Android because you have the past shadow elevation I think for Android

**3:44** · which is pretty weird And what's annoying is that AI agents use this all the time But let's pull out ChatGPT quick here And I'm gonna ask it let's say how to add a shadow in a view in React Native If this gives me the old syntax I'm going to explore yeah

**4:00** · see this is what I'm saying You can just simply say box shadow and pass the string Here I'm actually iterating over these shadows This is how it looks The cool thing about this is that it looks seamless on both platforms Here we have it on Android effortless right Just one line amazing And you can even do multi-layer shadows like this one right here If you want to learn more about some of these properties you can just go to the MDN documentation

**4:27** · Everything that you find here it will also work on React Native And real quick by the way if you want to stay on top of everything that is happening on React and React Native which is a lot it's actually pretty overwhelming Everything is changing every week New features are dropping And to keep up to date I actually use this week in React It's a newsletter that I recommend you to check out Everyone is using it to stay up to date with the news on

**4:53** · React and React Native And shout out to Sebastian because sometimes he includes links to my videos so definitely highly recommended in case you want to stay on top of everything Link is in the description Make sure to check it out Again this has been available for the web for years It's basically space between items I

### 4 Gap

**5:11** · know it's crazy I get excited for these basic integrations but not too long ago you actually had to handle spacing manually So when you had multiple items you would end up adding like a margin right or margin left or adding bottom And it was pretty awkward Now you can fix everything just with adding a single property gap

**5:32** · For example zero here React Native also supports row gap and column gap So for example let's change this to be zero And you can see it here at the bottom in case you want different spacing Well here and then the column it's 28 but let's remove it Now they are together And yeah you can play around with these values And of course this works on Android as well

### 5 Mix Blend Mode

**5:56** · And finally Mix Blend Mode I bet you didn't know about this one but you can actually use it on React Native as well to apply effects like this So for example here I have an image You can see that I'm using a bunch of effects here like Multiply Screen Overlay

**6:12** · Darken And I'm also passing a color orange to the overlay You can maybe change this to be red for example So the property is called Mix Blend Mode And as you can see we have a bunch of them So for example Color Burn Let's hit Save And now this is gonna apply it to everything But I have here an array of the

**6:32** · blend modes that we're using So we can just pass it directly here and see the difference Again if you want to learn more you can reference to the MDN documentation And here we have a better explanation by the way how an element's content should blend with the content of the element's parent and the element's background Here we can see the difference and we can try this like difference right Let's check this out here

**6:57** · That's the difference And it also has to do of course with the background color that we are applying here So in this case red But if I remove it nothing is going to happen right Because we don't have anything to blend But we can change this to be orange and you know you can create really crazy effects here

**7:16** · like white If you made it till the end congratulations You just won an agent skill that will prevent your agent from making these mistakes and always use these React Native styles It's available in my blog I'm going to leave the link in the description but if you come here and scroll all the way down you'll find it Just copy this give it to your agent and it will never make the same mistake For more React Native pro tips check out this video