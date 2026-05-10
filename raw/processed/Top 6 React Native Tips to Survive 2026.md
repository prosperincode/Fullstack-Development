---
title: "Top 6 React Native Tips to Survive 2026"
source: "https://www.youtube.com/watch?v=zMM0d1d1_X4&t=1s"
author:
  - "[[Code with Beto]]"
published: 2025-12-22
created: 2026-05-10
description: "🚀 Level up your mobile dev skills at https://codewithbeto.dev/learn! Use code HACKTHEPRICE25 for 25% OFF!AI Tattoo App → https://apps.apple.com/app/ai-tattoo-try-on-generator/id6751748193AI Tatto"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=zMM0d1d1_X4)

🚀 Level up your mobile dev skills at https://codewithbeto.dev/learn! Use code HACKTHEPRICE25 for 25% OFF!  
  
AI Tattoo App → https://apps.apple.com/app/ai-tattoo-try-on-generator/id6751748193  
AI Tatto Source Code → https://codewithbeto.dev/resources/aiTattoo  
Master React Native alongside me → https://codewithbeto.dev/learn  
  
👨🏻‍💻 🌟 Be the mobile expert on your team 🌟 👨🏻‍💻  
Learn mobile development with courses, templates, and full-stack codebases built to help you ship better apps:  
  
\- React Native Course → https://codewithbeto.dev/learn  
\- React with TypeScript Course → https://codewithbeto.dev/learnReact  
\- Git & GitHub Course → https://codewithbeto.dev/learnGit  
  
For other ways to support my work, please consider:  
  
\- GitHub Sponsors: https://github.com/sponsors/betomoedano  
\- Become a Code with Beto channel member: https://www.youtube.com/channel/UCh247h68vszOMA\_OWpGEa5g/join  
  
⌚️ Timestamps ⌚️  
00:00 Intro  
01:38 Prefer Pressable over TouchableOpacity  
03:59 Use platform file extensions, not runtime checks  
06:12 Avoid modals when a sheet works better  
08:53 Prefer FlatList over ScrollView for large lists  
11:53 Keep /app focused on routing only  
13:08 Recap  
  
⭐️ If you want to learn more about me, check this links:  
  
Code With Beto → https://codewithbeto.dev  
🦋 → https://bsky.app/profile/codewithbeto.dev  
X → https://x.com/betomoedano  
Github → https://github.com/betomoedano  
Linkedin → https://www.linkedin.com/in/betomoedano/  
Discord → https://discord.com/invite/dbYfWFw862  
Medium → https://medium.com/@betomoedano01  
Figma → https://www.figma.com/@codewithbeto  
  
#reactnative #expo #mobileappdevelopment

## Transcript

### Intro

**0:00** · Hey welcome back to Code with Beto In today's video I wanna share with you five tips that will help you survive 2026 as a React Native developer These tips will help you simplify your components and screens and write better code more scalable easier to understand for you and your teammates and also follows best practices This is gonna be a short video Make sure to stick till the end You don't wanna miss any of these tips If you like this type of video don't forget to give it a like and subscribe And without further ado let's dive in If you wanna become a master in React Native

**0:30** · check out my course at codewithbeto.dev We have courses on React Native TypeScript React Git GitHub Livestore for local first applications and more In case you didn't know pro members at Code with Beto get access to a private GitHub organization where you can find production-ready examples and applications that some of them are in production some of them are ideas and examples that you can use to actually implement something similar in your application or just take inspiration from the UI or just to learn how you can implement a specific AI feature or a specific technology

**1:04** · One of my favorite projects and the one that I've been working the most is the AI Tattoo application that I'm super proud to share that it's actually a real application that you can check out in the description in case you're curious And it's actually making money already $49 per month And we're close to 500 customers which is really exciting Definitely one of the best resources that we have right now for you to take as a reference

**1:26** · and learn how to implement nano banana for example for image generation and many many more things I'm going to leave the link in the description with a nice promo code for a nice discount for you Now let's get back to the video Tip number one guys prefer pressable over touchable opacity All right So to showcase

### Prefer Pressable over TouchableOpacity

**1:46** · these tips I'm going to be using my AI Tattoo application repo And the first thing that I want to mention is that please guys stop using touchable opacity As you might know touchable opacity is a component that comes by default with React Native and you can import it to handle press events

**2:04** · But actually no one recommends using touchable opacity nowadays Instead please use pressable That also comes with React Native and you can do actually more events and you get access to on press in for example that's one You get access on press out on long press and it's more versatile You can style it as you need And personally what I've been doing recently is just use this amazing package Presto Presto is a React Native library package

**2:36** · that you can use from Enso one of my friends He's well known in the React Native community And he created this abstraction from a pressable that you can just install Here are the instructions Personally I use it in my AI Tattoo application And it's great because you don't have to worry about haptics or animations when you press a button an image whatever you need to be pressable

**3:02** · You can just wrap it like this and use it And that's what I use in my AI tattoo application For example when you press let's say one of the images here you notice that nice animation when i press it in and then when you release it it nicely animates back then when i press it in a physical device i will get a haptic feedback and you can

**3:26** · configure this in the entry point of your application by configuring the haptics that you want to use you can even use a different haptic engine if you want to but in this case i'm using expo haptics this configuration it's you know at the entry point of my application and then all the principles that i'm using inside the application will have a nice haptic feedback of course you can also disable it if you don't want it in some cases as well as the animation this honestly saved me a lot of time so highly recommended for 2026

### Use platform file extensions, not runtime checks

**4:02** · tip number two use platform file extensions instead of runtime checks so if you've been developing react native applications for a while you might be familiar with the platform api that you can import from react native and then have validations like os equal to then validate the operating system that you

**4:21** · want to run this specific code that works great but as your application grows in complexity and also if you are implementing native functionality for a specific platform which is what i'm doing here in my ai tattoo application i want it to go very deep native into the ios apis

**4:41** · so i'm using expo ui a lot that means that some of the things that i'm using here are only going to work on ios and instead of having platform validations in line checks for the platform that i want to run this code i would recommend that instead you use platform extensions for the files on the left you can see that i have a profile file screen this is like the default for

**5:05** · other platforms that are not ios and then i created my profileiostsx screen for ios only and in here as you notice i'm using a bunch of stuff from expo ui swift ui which will only work on ios at the moment you can do that for components but it's actually also possible to do it for a specific route so for example let's say that i wanted to create a specific index file in my home route only for ios you can create an indexiostsx

**5:39** · and have the implementation of ios here and then when you compile your application the ios it's going to be used for ios platforms and then other platforms needs to do it's going to default to the normal indextsx you can use ios or android or you can even say native only for ios and android

**6:01** · or web if you plan to support web in the future and you want to keep the implementation separate it's really nice and easier to understand very scalable to just have different platform extensions

### Avoid modals when a sheet works better

**6:16** · Tip number three and this is actually more like a personal preference but you know it's totally okay if you don't want to follow this tip React Native comes with a modal that you can use to present you know modals and views like on top of other content And that's totally okay Now the only disadvantage of that is that you need to implement the logic yourself and be very careful when you are defining the

**6:41** · modal because you want it to be reusable You want it to look good You want it to look to use to look native but you know personally I would recommend that instead of using the modal use the presentation form sheet to present quickly context on top of the screen that you

**6:59** · are working on For example let me sign out of the application What I'm doing in AI tattoo is that of course I allowed the users to go and navigate to the application at any time but then when you press new tattoo you need to sign in and let me switch to main so that it looks it's because i'm working on a feature but

**7:19** · let me again select this is how it looks right now in production so pretty cool ui now the cool thing about using the form sheet instead of having a modal view here is that on ios 26 you get this beautiful blur background with liquid glass that looks absolutely amazing and in this case i'm constraining the detents to 45 of the screen but you can even allow

**7:44** · the user to move this right so for example if i allow one then i can you know expand it like this even if you are just presenting some options for the screen behind the sheets i would recommend that you use form sheets instead of a modal it just feels better and the form sheet i think also works on android if i'm not mistaken or

**8:09** · on android what you can do is just present it as modal and then set the presentation animation to be slide from bottom and this is going to present the modal on android from the bottom and just to add one more thing before we move on to the next step i've seen applications like chat gpt to use form sheets to present modals to add more context to a chat with more options to

**8:36** · add an image or add more context a file to the chat and you know it works great instead of having a modal that at the end of the day looks more like web stuff i recommend this tip at least for ios um because you know it really takes advantage of the native form sheet implementation

### Prefer FlatList over ScrollView for large lists

**8:56** · Tip number four prefer flat list over scroll view when it makes sense React Native comes with a scroll view that you can use like this and you know it works really nice but in some cases especially if you're rendering data that is coming from an API or it's a long list you should use a flat list For example let's take a look at the home screen in my application Since I know that this is going to be a pretty short list I only have rows here

**9:24** · one two three four rows This is totally okay being a scroll view And by the way another pro tip that I wanted to squeeze in here I also recommend using content in set adjustment behavior property set to automatic instead of wrapping the view in a safe area view So if you say safe area view you can import it and this is kind of works

**9:48** · but you can actually just have the main component in the application be a scroll view And if you actually do that this is how it looks right The content is behind the header that looks pretty bad So some beginners or some naive solution would be to just use a safe area view

**10:09** · And by the way these are mistakes that AI makes a lot So let me wrap this in here like that now everything is inside the safe area but still it's not respecting the header because i'm using a large header on ios

**10:25** · so to prevent that you can just remove this or maybe keep the safe area view for android but i don't think it's needed on android because we don't have a large header and just have this property to automatic and this will make sure that the content fits nicely within the scroll area you can use this property as well on a flat list

**10:45** · cool thing about flat list over the scroll view is that flat list comes with many other things that you can reutilize and helper properties like for example empty list component when the array of items that you are passing it's an empty array the component will render this component just like that you can just pass a component here you don't need to have a validation like in this case i can just say you know no body parts found and that's it you can also use header components and the goal is

**11:15** · to try to keep the flat list so in this case i'm using legend list but the properties are basically the same if you're just using flat list you can just pass the same properties and you can use like i said header components you can also have a sticky header there are so many properties that you can use and the goal is to try to keep the list as the main entry point and the only component that you are rendering for the screen that way you can again still use the behavior content inset behavior to automatic

**11:46** · and this will help you have everything inside the safe area view with the nice animation as you scroll as you can see here tip number five and this tip applies if you are using expo router or just bare react navigation keep your files inside the app folder only focus on routing stuff as an example here i

### Keep /app focused on routing only

**12:08** · have my index file which contains a screen right this is my onboarding and this is a component that i'm importing you know you might be tempted to instead of importing this component start doing your logic here having user state fetching data in this screen and this is a bad pattern because it makes refactoring the navigation and moving the layout around very complex because you need to update the imports and stuff like that so keep this routes as lean

**12:38** · as possible right So for example here in my paywall the only thing that I'm exporting here is just this component that is coming from my components screen paywall This allows me to quickly refactor at any time and also reutilize this screen in multiple routes if I need to and present it in a different way if I need to as well because everything related to router is gonna be handled within these components This helps refactoring maintaining and really makes it easy to scale

### Recap

**13:08** · That's it for this quick video guys I hope you like it I hope you learned something new Don't forget to give it a like and subscribe Let me know in the comments if I missed something important and also let me know the one that you're gonna be using the most in 2026 Don't forget to check out codewithbeto.dev There is a promo code in the description and I'm happy to announce that we also offer purchase parity power Please send me an email at beto at codewithbeto.dev and I'm happy to help Thanks for watching and I'll see you in the next one