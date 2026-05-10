---
title: "How React Native Builds Actually Work (APK, AAB, IPA, APP)"
source: "https://www.youtube.com/watch?v=1o0pEjYGUWM"
author:
  - "[[Code with Beto]]"
published: 2026-04-30
created: 2026-05-10
description: "Master React Native builds, learn the difference between APK, AAB, .app, and IPA artifacts, and how to create them locally or in the cloud with EAS.Master Re..."
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=1o0pEjYGUWM)

## Transcript

### Intro

**0:00** · I recently made a post explaining how to create an APK and a app for iOS from your computer using the native toolchains Gradle and Xcode build And it has come to my attention that many React native developers have no idea they can actually create these artifacts locally And I actually got a lot of requests for this video So this is it By the end of this video you'll be an expert in

**0:21** · release artifacts You'll know the difference between them how to produce them when to use which one of them And if you stick till the end you'll get a Claude skill that will help you create release artifacts just by prompting Let's get into it Before we dive in this video is sponsored by me If you want to become a master in React Native or just support the channel and my work consider becoming a pro member at codewithbeto.dev You get access to everything including our latest and most capable React native template called Platano Already comes with payments works on Android iOS revenue ready Just run

**0:54** · this command and get started Some of the early users of Platano are sharing already really nice feedback about it Most engineers are actually using it just as an example or to ship a completely different application not an AI image app And I completely agree I'm actually using Platano for any new real project that I'm shipping In case you're new to mobile development and you are using AI check out my book From Idea to App Store with Claude Code All the links are in the description Now let's get into it Okay so how React Native builds work React Native allows you to create iOS and Android apps fully native and each platform has its different

### How React Native builds work

**1:27** · type of builds and artifacts So we first need to understand how that works Basically an artifact is the file that you build process spits out These are the four type of artifacts For Android you have apk which stands for Android package and it's a self-contained installable

### The 4 artifact types (APK, AAB, .app, IPA)

**1:47** · Drop it in any device and it runs Then we also have the aab file Android app bundle This one is used by Google Play So you give the aab to Google and they take that to generate a smaller per device APK

**2:05** · at install time And iOS works the exact same way You get a app it's called iOS app bundle And that's the compiled app that runs on the simulator or on your device through Xcode And then when you are ready to ship that to production it's called a ipa It's basically a app but signed with

**2:28** · certificates So those are the four types of artifacts Now you might be wondering how does it actually look right These are type of files So I took a screenshot This is Platano the template that I just showed you It's not signed And I think that's why you get this icon here And an APK APK that's how it looks 138 megabytes And this is the real thing This is the IPA also known as the archive of your build and the aab So for Android is 90

**2:57** · megabytes and this one is 195 megabytes That's how it looks okay So a quick mental model to understand because you might be wondering oh gosh 200 megabytes for a simple application That's a lot but that's not actually what users installed The archive it's the source of the root right And the archive can be used to generate the aab file or the APK

**3:19** · that is installed on the real device at install time So when a user presses the install button Apple and Google are going to look at the main artifact and just grab the piece that is compatible with the device that is requesting the application So let's say in an iPhone 17 Pro it's gonna be around 40 megabytes once you install the application So the archive is the source of the root for every variant Okay now let's talk about

### Why your machine decides what you can build

**3:46** · how you can create one of these builds right One of these artifacts Well your machine actually decides what you can build This might be obvious for a lot of you but you might be surprised of how many comments and questions I get every day people asking if they can build an iOS application

**4:06** · on a Windows machine And the answer is no Apple requires Xcode for iOS and Xcode only runs on Mac OS If you don't have a Mac you cannot build an iOS application locally right You can still use the cloud to build your Expo app using a service like EAS and we are gonna talk about it

**4:30** · But if you want to develop an iOS application I would highly recommend that you get a Mac That's step one That said if you're just targeting Android you can use Windows or Mac Android Studio is available for Mac OS Okay so there are two ways of creating these artifacts You can create the build locally using your computer or you can use the cloud and services like Expo Application Services So when you are building locally you're gonna be using the native toolchains For Android you use Gradle For iOS you use Xcode The

### Local builds vs cloud builds

**5:02** · advantage of local builds is that it's extremely fast It runs on your computer but you need to have the setup already done Those are the two ways of building Now let's take a look at the native Android project that you get when you pre-build

### Inside the native Android & iOS folders

**5:17** · your application So a React Native Expo app is going to look like this This is the Platano template that I was showing you before And if you have been using Expo you know that you can run this command npx expo pre-build When you run this command the Android and iOS folder are gonna be generated This native project is generated

**5:39** · by Expo based on the dependencies that you are declaring in your package JSON based on your code And this is just a native Android project You can think of your Expo React Native application as a monorepo with multiple projects the Android and iOS folder The Android folder and the

**5:59** · iOS folder are the folders that make release builds possible because that's the native code that you compile Without it you cannot do it So how you can build Android locally It's very easy You just cd into the actual Android project

### Building Android locally with Gradle

**6:16** · by opening your terminals cd Android and boom you are inside the native project The Android project actually comes with some tooling like Gradle Gradle So Gradle it's a tool that allows you to compile the application And Gradle you can install it globally on your machine but I actually don't have it installed but that's okay Because if you pay attention here the Android folder already comes with its own Gradle

**6:44** · And it's called Gradle wrapper which means you can you should call it with a W here Gradle wrapper And then you can use this little artifact that comes here If you take a look at the wrapper properties you're going to see the version It's nine in this case And then for example I can

**7:03** · say version hit enter This is just going to tell me oh yeah it's version nine which I already knew here So you get access to this just by sitting into the Android folder You can use Gradle to create APKs and aab artifacts To

**7:21** · generate the APK you just use Gradle wrapper running the command assemble release Once a command is done you'll find the APK inside the app build outputs Here's APK And I actually just realized that this is a debug debug build that's why it's showing me these

**7:40** · developer tools from expo to connect to the server and this is because i'm inside the debug folder but if you go to the release you also get an apk which is the one that you should use for a release build this one is the actual standalone one so expo is not going to install the expo dev client

**8:00** · when you have a release build so this is going to reinstall it let's open it again and now this is the actual application let me allow permissions here and boom this is a standalone application i can close it reopen it everything works just great it's super

**8:17** · fast because it's the real thing right this is great for testing and for sharing quickly to generate the dot aab just just run gradle wrapper bundle release that will generate the signaab for the play store so let's move on to the ios folder this is again a full xcode project for mac only i'm going to

### Building iOS locally with Xcode (.app)

**8:37** · minimize my android folder let's take a look at the ios folder it comes with a pod file and all the native stuff that you need for this specific project depending on your dependencies depending on your code this is the native stuff So again you can open the terminal cd into the iOS folder and start you know using for example Xcode build So once you install Xcode that actually installs Xcode

**9:08** · build which is a CLI tool that you can use for building your application Now this is a little more verbose And I actually created a blog recently on how to build your React Native app locally So for iOS this is a little more verbose you need to pass Xcode build and then the workspace the scheme of your app the configuration that you want to use in

**9:31** · this case is release Otherwise if you create a debug build it's going to include it's going to include the Xcode dev client which is going to wait for the server to be running Otherwise it's not going to work But it needs to be released you need to set the SDK

**9:46** · as iPhone simulator and then code signing needs to be no let me show you that in practice so once you have the you know the command you can put it into a script and run it and this will generate it now this is for creating a dot app release right this allows me to install it on a simulator

**10:06** · as a standalone this is good for end-to-end test i recently made a video on how to use maestro for end-to-end test and i use this dot app to fully test my onboarding flow make sure to check out the video i'm gonna leave that in the description in case you're curious yeah this is the command so you can just run something like this with the values of your project the command has completed you will find your app file inside the ios folder build again build products

**10:37** · release folder and then platanoapp let's open this in the explorer Like I said before it's going to look something like this and then you can drag it into any simulator So I'm going to remove this just to show you that once you drag it it's going to install it

**10:59** · and you can open it And here we have it So this is a real application The first time that you open it this is how it looks This is the onboarding You enter your name and all that good stuff This is actually the template Make sure to check it out It's amazing It's really going to save you a lot of time Okay So that's a build release build for a simulator It's

**11:20** · not signed right It's easy to create It's fast and you can install it on simulators It's great for end-to-end tests You can check out my blog I'm going to leave the link in the description where I teach you more in depth and give you the code examples that you can copy paste I also created a Claude skill that helps you create the scripts with your project name So you don't have to manually type it So Claude is going to generate the scripts for you You can just run them and then you get the APK and dot

**11:48** · app locally without doing anything So make sure to check out the skill but this is only the dot app right So for iOS it's a little more complex because iOS requires you to sign your application when you are ready to deploy it right To install it on real devices you need to distribute it through a test flight or the app store And that's the way you create a dot IPA It's by compiling first your application and generate the dot app bundle

### Creating an IPA for TestFlight & App Store

**12:18** · Once you have that you need to sign it Once you sign it it becomes the archive okay And then you need to export it as a dot IPA It's basically a dot app but sign That's the IPA Now you can also create the IPA using Xcode build from here Actually that's more complex I would say It needs way easier just to use Xcode Once you have Xcode installed on your computer you can run this

**12:49** · command xed -ios Basically I'm saying hey Xcode open the iOS folder And Xcode is going to open it This is how it looks So this is my Platano application It comes with pods and then the actual app here

**13:05** · It has actually two targets one for the share extension that I have And here you select your team to make sure that the signing and the artifacts are working correctly Just select your team with your Apple account And that's how you sign the build And then once you're ready to deploy this to TestFlight you can select any iOS device here from the dropdown and then go to the product There it is And then archive So archive is going to generate

**13:36** · the archive that I just mentioned here the Xcode archive ready to export for TestFlight So once you run this command I'm not going to run it because it actually takes like a couple minutes But then once you do that you can go to window and then select organizer And this organizer it's going to show you all the Xcode archives that you have So I

### EAS Build (cloud) — pricing & workflow

**13:59** · compiled this previously This is my archive You can open it if you want in the finder And this is how it looks I showed you before This is the real thing This is the archive And you can send this to Apple So to send it you can just press this distribute app Select app store connect And I'm going to cancel it

**14:21** · because I'm not ready to publish this yet But this is actually how I release my AI tattoo application For example I just compile it locally and distribute it through Xcode And then once you submit that to TestFlight you can install it or any testers in your team Okay So that's how you create the ipa Now let's talk about EAS As you might know there's many services One of them is EAS build

**14:45** · Basically compile and sign your Android and iOS application in the cloud The way it works is simple You have your project trigger a new build using the EAS CLI And then that uploads your project to the cloud where Expo can build your application on a Mac machine And then it gives you the artifact So to build for iOS you can run the command EAS build platform iOS EAS build platform Android Now the killer feature

**15:11** · here is that if you don't have a Mac but you want to compile your application for iOS you can actually trigger this command from a Windows machine Once you trigger these builds you basically will get the same files that I show you then you can distribute them or you can also use Expo to submit the application It's a different service but we're talking about builds right now Now Expo is actually free to get started You can just create an account and by default you will get 15 Android builds and 15 iOS builds per month In my

**15:44** · opinion that's more than enough for a side project right but it depends on how much you're building If you build more than that you might consider upgrading to this starter plan which is $19 per month and includes $45 on credits Um the way it works is that if you build an android bundle on a medium worker meaning a machine that is medium size that cost one dollar larger machine means the build is

**16:15** · going to finish faster but it cost two dollars for ios the medium worker cost two dollars and a larger worker four dollars per build so if you you know if you want to use a large worker it's very fast but it costs four dollars so if you build 10 times that's 40 So this is something to consider if you're using eas build now the good thing about expo is that you can use the 15 builds and then you can build locally as well

### EAS Build with the --local flag

**16:40** · expo provides a flag for running these commands eas build platform ios with the local flag and that will use your computer to build the application and that's free it doesn't count over your usage and it's basically like running it using the native tool chain just expo wraps everything

**17:05** · into one command and you get the same artifact locally you can do that as well um i personally recommend that you do that especially if you don't want to use all your builds you can build locally and then once you're ready that you're up once you know that your application compiles and works nicely and you're ready for production maybe just use eas to build and submit So overall there are mainly three ways of building your application You can build locally It's the fastest iteration once your machine is ready And if

### The 3 ways to build (recap & recommendations)

**17:34** · your machine is capable if you have a good machine you know it's faster building locally And it's free There's no queue no waiting time full control over the native tooling And I would say that this is best for solo developers especially if you have a nice Mac and that's personally what I do most of the time Now the second option is using EAS with the local flag Like I said you

**17:56** · can build locally It basically runs the same workflow but in your machine So still you need a Mac if you want to build for iOS it has the same credentials handling no cloud minutes consumed great when you want EAS conventions but have the local horsepower And then the third option I would say

**18:15** · is EAS cloud Especially if you're on a team you are not going to be paying for it Just you just might as well just use Expo It's easier It's just one command Again you can trigger iOS builds from a Windows machine and a CICD integration And I recommend that you use EAS builds especially if you have a large team I would say

**18:31** · three or more people because as a team grows you know you need to run end-to-end tests trigger builds make sure that nothing is breaking So EAS definitely will save you more time than having to juggle all the builds locally That's all I have for today I hope this video was helpful and informative Make sure to check out my courses Platano the template to faster in my book All the links are in the description I'll see you in the next one