---
title: "6 Expo UI Tricks That Save You Hours of Debugging"
source: "https://www.youtube.com/watch?v=dhN7eeqOVeE"
author:
  - "[[Code with Beto]]"
published: 2026-03-07
created: 2026-05-10
description: "🚀 Build and compete in the TestSprite Hackathon starting March 9th: https://www.testsprite.com/?via=codewithbetoExpo UI in SDK 55 is powerful, but a few non-obvious properties can make or break you"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=dhN7eeqOVeE)

🚀 Build and compete in the TestSprite Hackathon starting March 9th: https://www.testsprite.com/?via=codewithbeto  
  
Expo UI in SDK 55 is powerful, but a few non-obvious properties can make or break your app's feel. I share 6 tips I learned building production apps like AI Tattoo and the upcoming Platano template. From ignoreSafeArea and matchContents to platform colors and the React Native host view — these are the things I wish I knew from the start.  
  
Master React Native alongside me https://cwb.sh/rn  
AI Tattoo App (Inkigo): https://cwb.sh/inkigo  
  
📬 Newsletter: https://cwb.sh/newsletter?r=yt  
💬 Join the Discord community: https://cwb.sh/discord  
  
For other ways to support my work, please consider:  
\- Become a Code with Beto channel member: https://cwb.sh/join  
\- GitHub Sponsors: https://github.com/sponsors/betomoedano  
  
🐦 Follow Beto on X: https://x.com/betomoedano  
💼 LinkedIn: https://www.linkedin.com/in/betomoedano  
💻 GitHub: https://github.com/betomoedano  
📸 Instagram: https://www.instagram.com/codewithbeto  
🎵 TikTok: https://www.tiktok.com/@codewithbeto  
🧵 Threads: https://www.threads.com/@codewithbeto  
🦋 Bluesky: https://bsky.app/profile/codewithbeto.dev  
  
⌚️ Timestamps ⌚️  
00:00 Intro  
01:24 Tip 1: ignoreSafeArea Property  
03:51 Tip 2: matchContents Property  
06:21 Tip 3: React Native Host View  
08:49 Tip 4: Platform Extensions  
10:46 Tip 5: Centralize Your API Logic  
12:13 Tip 6: Platform Colors  
14:22 Recap  
  
#expoui #mobileappdevelopment #reactnative

## Transcript

### Intro

**0:00** · I've been using Expo UI since the alpha days and now with the beta in Expo SDK 55 it's come a long way But there are still a few things that aren't obvious And if you don't know them your app just won't feel polished I've been building production applications with Expo UI and today I'm sharing six

**0:16** · tips that will save you hours of debugging and make your application feel way more native Oh and before we get into it this video is sponsored by TestSprite If you haven't heard of TestSprite yet it's an AI-powered testing agent that automates your entire software testing workflow from generating and executing tests to diagnosing issues for both front-end and back-end parts of your project So you don't have to write and maintain tests manually They just released TestSprite 21 with some great new upgrades like visual test modification

**0:47** · where you can click on a snapshot of a test step and tweak it without writing selectors by hand And GitHub integration so your tests run automatically on every pull request Also there's an online TestSprite hackathon starting March 9th that runs for a whole week with prices up to grabs You can build something real use TestSprite to generate tests and submit your project All the details and the hackathon links are in the description below And honestly them sponsoring this video helps me keep making content like this for you So if you're curious about TestSprite or want

**1:17** · to join the hackathon go check it out Make sure to use my link and now let's get into it All right let's dive straight into the tips When I'll be using my AI Tattoo application code base it's using a bunch of Expo UI so it's a great example And then Platano which is a new template that I'm working on to create basically nano banana wrappers super fast And it's also using Expo UI for iOS and Android The

### Tip 1: ignoreSafeArea Property

**1:41** · first tip that I want to share is the safe area that by default comes with Expo UI components Let's navigate to the playground Let's say that I want to try on this tattoo So let's press use tattoo It's kind of like breaking the UI The space between the keyboard and the input is very big So if UI it's going to try to move things so that they are not covered by the keyboard So in this case I had my input

**2:10** · and I'm using a sticky view by the way from React Native Keyboard Handler This is position absolute Everything looks correct These measurements are correct But somehow when I open my input it's still taking more space that I would like to This is why you need to be aware of ignore safe area property that comes in the host component This view controls the safe area regions the SwiftUI hosting view should ignore

**2:40** · Because sometimes you want to have this functionality but sometimes you don't So you can ignore all the safe areas or just the keyboard So if I tilt this view that it should ignore the keyboard then just like that it fixes it

**2:57** · So this is actually pretty painful if you are not familiar about this ignore safe area property and yeah just like that it's fixed It's basically ignoring and it's not going to try to avoid the keyboard by default Here's another example on my AI Tattoo application I'm using in this case ignore safe area all And this is a button that you can see at the bottom right of the image If I don't use this ignore safe area all

**3:23** · look what happens when I open and close the keyboard The view is somehow trying to avoid the keyboard and it's actually not working but the button is still moving a little bit So to prevent that you can just ignore all the safe areas in this case because I don't care about the button being covered in this case because the user can always swipe down to dismiss the keyboard

### Tip 2: matchContents Property

**3:51** · Right the second tip the property match contents so match contents what it's doing it's basically automatically giving a width and height to the swift ui view so that it can actually be rendered correctly on your component so right now i deleted the match contents property in this host view which is the input controls and just like that i broke it if i even if i

**4:16** · do flex of one and provide a border width of one just in color red just to see where it's at You can see that we are actually not providing enough space And you can think of the host as a window for me to

**4:31** · access the SwiftUI view So here's my inputs And in order for the inputs to be accessible to the user you need to create a host view to render it But right now my host view is only like this size So we need to give it a width and height What you can do instead of using flex of one it's give it a width of a hundred percent but this actually I don't think it's gonna work because you have to actually provide a number So if I give it a height of 40

**5:05** · and I think we can delete the height the width there Now this is accessible as you can see here But how do I know the height of my content that I have down here which is the input right I would need to somehow try to match it perfectly because I set 40 right now but it would be 30 And

**5:29** · now the window is smaller than the actual size So of the native view we could actually not register some presses Like right there I'm pressing just outside the window So the way to fix this just it's actually very easy Just delete the entire style and pass the match contents which is gonna give it the exact size it needs

**5:50** · So right now I would need to refresh my screen and let's try it again And right now it's just gonna work No matter where I press it's going to register my touches so what that is doing is basically just adding the host width and height to match exactly the width and height of the inner SwiftUI view and this is the host view by the way this is way cleaner this is what what is happening

### Tip 3: React Native Host View

**6:21** · Tip number three it's about React Native host view This is actually a component that you can use from Expo UI and it allows you to host a React Native view within an Expo UI view All right let me explain how this works React Native by default uses UI kits but when we are trying to use Swift UI the way we instantiate these views

**6:44** · is using the host view right So we can create a host view and add native components from SwiftUI and Jetpack Compose But the thing is that when we are adding these buttons inside this host view this host view only allows native components from Expo UI So if you try to use a UIKit view

**7:05** · here this is actually going to break your application So in order to have a normal view from React Native we need to create a host view right This is my host view And this will allow me to use my normal views from React Native Inside this technically we are inside a Swift UI view or Jetpack Compose view but we can still use React Native primitives So let me show you this in action So for Platano we want to provide a fully

**7:35** · native settings screen for iOS and Android So this entire settings screen it's a single host view So I'm just writing Swift UI here And for Android what we're doing it's the same thing It's a host but all the components are coming from oops Jetpack Compose right So these are fully native screens Now the thing is that I wanted to showcase this preview of how the UI is

**8:03** · going to look depending on the settings that the user is selecting here So it could be the roundness and all that So for that I wanted to use a view from React Native And here you can see it This is an RN host view that is coming from Expo

**8:20** · UI Swift UI And since this entire view is Swift UI in this case I cannot use directly views from React Native which is what I'm doing here This is coming from React Native Super simple Just host a React Native view inside your Swift UI view and then you can use React Native stuff Very important component to be aware of when using Expo UI for sure

### Tip 4: Platform Extensions

**8:49** · Tip number four use platform extensions for components or routes Now platform extensions is a concept that is actually not tied to Expo UI but it's very important when working with Expo UI because you are either using Swift UI or Jetpack Compose to render components So if you implement this naively you're going to break your application for other platforms when you are using you know specific things for a platform So what I recommend here it's always to create

**9:19** · a platform extension when you are using Swift UI or Jetpack Compose So in this example The input controls this is coming from Platano by the way Navigate to the screen these input controls um if you notice here this is my default component it doesn't have a platform extension this is because you actually

**9:39** · need to have a normal named component but for other fallbacks you can add the platform so in this case this is for android but you could be could be ios as well and for each platform extension you're going to need to implement the fallback that you want to use so in this case for the inputs I wanted to use liquid glass I wanted to

**10:00** · use SwiftUI so I can go ahead and import all the modifiers and all the components that I want to use in this component and it's going to be okay it's not going to break Android because Android is going to use this component just by creating this platform extension when you compile your application this is going to be loaded for Android and at the moment I'm just using normal views from React Native but I'm planning to implement Jetpack Compose in the following days you can use androidnative for iOS

**10:32** · and Android webios but remember that you always need to have at least one normal name like input controls like in this case tip number five is going to be centralized your API so when working with expo UI you need to avoid duplicating code

### Tip 5: Centralize Your API Logic

**10:54** · and logic on each screen because a naive solution here for example I'm inside you know iOS implementation a naive solution here would be to do my fetch request to do my state update and all the things that doesn't have to do with expo UI it would be naive to do it here because i would need to reutilize the same logic on my android implementation right i need to also handle this

**11:21** · so it's a good idea to abstract starting from the types all the things that these two views are gonna use and then the actual logic the way you do that is by lifting the state and by lifting the state i mean creating a context for example so in this case let's take the spacing for example this is coming from this context and it's being used in both native views but i don't need to implement it again because it's coming from the context right so the spacing if i go to the

**11:49** · android implementation you can see that i'm also accessing the spacing and it's the same api i'm reusing as much as possible that's the goal so what i recommend when working with Expo UI and doing this kind of abstractions is to think of them as a mini package or mini library that you are creating and you need to ensure reusability and compatibility all

### Tip 6: Platform Colors

**12:13** · right tip number six is going to be to use platform colors so in case you didn't know expo router in the latest version of Expo UI SDK 55 now comes with a utility color that you can use to graph the platform colors of each platform colors for android and ios and the way you access them is just by saying coloriossystem

**12:35** · background and then for android you can actually use dynamic surface colors and material colors which is really cool you can access it by saying colorandroiddynamicsurfacecontainer but honestly my favorite part of using native colors is android because

**12:52** · android takes the colors and all the color palette for the entire theme from the wallpaper so if i go back let's close that let's change my wallpaper so if you notice every time that i press one of these colors the entire ui system ui changes right so let's use this kind of like purple and now my system theme it's like purple

**13:16** · right so if i go out and navigate across my application everything it's like with this color scheme so when i go to my app now my app is going to adapt to the life to the platform colors in my opinion this is absolutely amazing and it's also compatible with light and dark mode automatically so you don't have to worry about anything else one other thing that I wanted to mention especially for

**13:45** · Jetpack Compose let me show you the settings screen so for Jetpack Compose I'm using all these components but let's grab a button as example you can pass modifiers and on the modifier you can pass a background from Jetpack Compose and in here you can pass native colors directly and you can take them from Expo Router so I can say color android dot system surface or what's the name

**14:15** · dynamic dot surface yeah and that is going to take the color from the background and the system these are the small things that make a massive difference when working with Expo UI from handling the keyboard properly by ignoring the safe area to using match contents correctly to bring in React Native views using the React Native host view inside Expo

### Recap

**14:36** · UI views Add platform specific extensions centralize your API logic instead of duplicating it everywhere and use native platform colors Most of these aren't obvious when you first start with Expo UI but once you know them everything just clicks If you are serious about building polished React

**14:52** · Native and Expo apps or maybe you're interested in the Platano template that is shipping soon which will allow you to ship your own application production ready It's going to be massive Check out the links in the description Also thanks to TestSprite for sponsoring this video Make sure to check them out The link is in the description as well Thanks for watching Like subscribe comment and I'll see you in the next one