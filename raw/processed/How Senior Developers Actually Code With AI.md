---
title: "How Senior Developers Actually Code With AI"
source: "https://www.youtube.com/watch?v=t1bWyk9qVa4"
author:
  - "[[Jan Marshal]]"
published: 2026-05-08
created: 2026-05-10
description: "In this video, I walk through my complete AI coding workflow by building a real feature inside an existing codebase. We’ll use Cursor and a modern coding LLM..."
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=t1bWyk9qVa4)

## Transcript

### Intro

**0:00** · Most AI coding demos are complete fantasy. Someone opens cursor, writes, "Hey, build me a SAS." And 2 minutes later they somehow have authentication, billing, a dashboard, database tables, a landing page, perfect UI, zero bucks, and probably a small coffee shop in Berlin.

**0:22** · Nice. very inspiring and also complete nonsense.

**0:28** · Because in the real world, coding agents forget your database schema, create duplicate components, import libraries you do not use and don't want to use, break your offflow, ignore half of your instructions, and then confidently say, "Hey, everything is working."

**0:46** · And that's the problem. Most people don't have an AI coding workflow. They have a prompt, a dream, and a very large give. So in this video, I want to show you how I actually use coding agents to build software in a way that is controlled, maintainable, and of course, production ready. So are you ready?

**1:09** · Well, let's go. All right. So before we now dive into the actual AI coding workflow and start VIP coding, I want you to first of all look at the foundation. But what do I even mean by foundation? Well, there are three very important things that you have to look at whenever you want to VIP code the right way, the most secure and scalable way. The first thing of course is your workflow. We will look at it in a second. The second thing is your model choice.

### Best LLM for Coding (What We’ll Use)

**1:40** · What model or in other words models should you use? And the third thing is your agent harness interface choice whatever you want to call it.

**1:50** · Let's first of all start with your model choice. What model should you use?

**1:54** · What's the best model out on the market?

**1:57** · What model will we use in this video?

**2:00** · And do you want to know the honest truth? Well, it does not matter and there is no best model out on the market. Now, I talked about this already in quite big detail in a previous video.

**2:12** · Nevertheless, let me give you a quick TLDDR. Most modern LMS are good enough and they will get you a good enough result. Now, yes, sure, every model also kind of excels in a different area. What I mean by that is Opus 4.7 is great at the front end. GPT 5.5 is great at the back end. Gemini 3.1 Pro. I guess it's great at something. I don't know. I don't use the model, so let's just forget it. But in general, most modern LMS are good enough.

**2:43** · And it does not really matter if you use a premium model like Opus 4.7 or some opensource model created by a Chinese lab like GLM something or Miniax. All of that does not matter. And also a second thing you should know is that your model choice will evolve quite a bit with time. If you would have asked me 1 month ago what models I use, then I would have said, "Hey, GPT 5.4 is great. It's my favorite backend model."

**3:13** · And Opus 4.6, I guess it's good for the front end, but I don't really use it heavily anymore. Now, 1 month later, I must say I hate GPT 5.5. It's a bad model in my opinion. At least it does not work for me. My workflow does not work with this model. And Opus 4.7 on the other hand works very well for me. So everything will evolve with time. Please don't marry the provider.

**3:41** · Don't marry inropic open AI. At the end of the day, you should be neutral. Choose whatever works best for you for your workflow and most importantly for your use case. Because here's a quick side note. Sometimes people say in the comments, "Hey, Gemini 3.1 Pro is a great model. What are you talking about?" If this is the case, then great. For some people, this model might work.

**4:04** · For me personally, it does not work. And that's again because I maybe have a different workflow compared to you guys.

**4:11** · But now going back to the original question, what model will we use in this video? In this video, I will use Opus 4.7 because in my opinion right now when recording this video, it's the best allrounder model out on the market. GPT 5.5 is a okay model. It works quite well when doing backend work, but it's quite sluggish whenever doing front-end work.

**4:37** · So, yeah, I don't know. I will use Opus 4.7, but you can use whatever you want to use. Let's now continue with the second thing which is which agent interface or in other words harness should you use. And here the answer is again the same one as with models. It does not matter and there is no best tool out on the market. It fully depends on you your workflow and most importantly your use case. I would highly recommend you to test everything out.

### Best AI Coding Agent: Cursor, Claude Code, Codex, and More

**5:06** · This means the editor category, cursor, wind surf z whatever the cli or in other words tui category cloth codeex open code etc and of course also the cli wrapper category. So the codeex desktop application open code desktop application cloth code desktop application etc. All of these interfaces have their pros and cons. The end goal for you should be to remove friction as much as possible.

**5:37** · If that means that you should use cloth coat, then do so. If that means that you should use some sort of seal eye wrapper, then go ahead.

**5:46** · Please don't forget it fully depends on you. It does not depend on some sort of Twitter hype and whatever some influencer is saying. But going back to the question, which interface, which agent will we use in this video, well, we will use cursor. And the reason for that is somewhat simple. Cursor is a great allrounder. It offers all of the models needed. It has pretty much all of the capabilities that you would want, skills and stuff like that. So that's why we will use it in this video. I want to just be as open as possible.

**6:16** · But again, if you want to lock yourself into one specific model, then it's also totally fine to go with the tool provided by the provider itself. And with that out of the way, we can finally get started. And now you might ask me, hey Jan, should we now just open cursor and go ahead and prompt away? No, not so quick, my friend. This is a huge mistake. Our workflow is very, very thorough.

**6:45** · And this means we have to also think about a lot of things before committing. What does that mean for us?

**6:51** · Well, what do we want to even do? What feature do we want to ship? How should the feature look like? This is the very first step in our AI coding workflow.

**7:01** · This means I want you to define the idea. I want you to ask yourself a few questions. Who needs this? And what's missing or painful for them today? This means your customers. What's the simplest version that is still genuinely useful? In other words, MVP. What's the minimal viable product? And what's in V1 versus later? Then how does it fit with what's already in the application of billing permissions existing UI?

### Defining the Idea: Questions to Ask Yourself

**7:29** · What does success look like from the users's perspective? From the customer's perspective, how will they know it worked? And then finally, what does not belong in this feature? What's tempting to add but actually out of scope? What is not needed? This is very important.

**7:48** · You need to have a clear understanding of what you are going to build and what you are not going to build. This is very important. A lot of people often skip like thinking through things which I guess I kind of understand but it's a big mistake. Again, we are not vibe coders. We are engineers and you engineer the right way. You need to also understand the problem and that's the only way how you can understand the problem and get the correct solution. if that makes sense. So, what are we now going to build?

**8:20** · Well, I already have an application. I will show it to you in a second. And essentially, I want to create an invitation flow. So, members should be able to invite new users, new members. And this means that owners and admins can invite teammates by email and pick their role. Owner, admin, or member. Then the person that got invited will get an email with an accept link that works whether they are already signed in, signed out, or don't have an account yet.

**8:52** · Pending invitations show up in the organization settings alongside members and can be revoked at any time.

**9:00** · Planned seat limits count current members plus pending invitations together, so the limit can't be sidestepped. Essentially, I have billing setup and I have seatbased billing setup. This means if a user is subscribed to a plan that allows a maximum of five members, then the invited users also count to this limit even if they haven't accepted the invitation yet. And then finally, invitations expire after a set window and can only be accepted by the email they were sent.

**9:33** · This is essentially what I'm trying to build. This is what I want to have. I listed out exactly what should happen. Also, right here, you see I thought about side cases. This means billing. Most people would probably forget that. And this means your agent would pretty much assume a lot of things. You want your agent to pretty much assume nothing. You should provide as much context as possible so that your agent is able to make smart and informed decisions.

**10:02** · So since we now know what we are trying to build, I will also quickly show you the application. So right here, this is syntax kit. This is my personal starter kit that I have been already building for about 6 months or so and it will be finally released in 2 weeks which is super super cool. Nevertheless, if I now click into the dashboard, you will see in the sidebar that I have an organization settings button. And if I now zoom out a bit, you will see here that there is no form to invite users.

**10:34** · And I want to fix that. I want to essentially render another form, another card. And in this card, I want to have a form. And this form will allow me and I guess other users to invite members, change the role, remove invitations, and do all sorts of fancy stuff. So now you might say, okay, Jen, understood. So we want to have an invitation flow. We want to create one. It will be rendered in the organization settings. It will be another form. We already talked about the core primitives, the core features, what should be implemented.

**11:06** · So should we now get started with the implementation?

**11:11** · Should we head over to cursor and say hey create an invitation flow for me?

**11:16** · No. No. No. No. Not so fast. Again, we are engineers. Take things slow. Before doing anything, you want to provide as much context as possible. Again, we already talked about the feature idea. But does our LM have a general understanding of our application? No, not really. And this is a big problem.

**11:38** · Therefore, I would highly recommend you to always create a PR, product requirements document. And a PRD, yes, kind of sounds boring. I mean, who wants to create a product requirements document? nobody to be honest. But it's super super essential for your agent to have a clear understanding of what your application is, what it will do, what it's doing right now, and in other words, what it won't do. Because again, these questions were for our feature idea itself.

### Why a PRD Is Essential

**12:08** · We now scoped down the feature, but our agent does not have any understanding of our already pre-existing application. And to create a PR, I want you to again ask yourself a few questions. What are the target users? Developers, engineers, coders, VIP coders, normal people, marketers, who knows? What's the MVP scope of your application? If you already have a fully featured application, then list out the general scope of your application.

**12:40** · What's the primary user flow? Should the user first of all land on the landing page or maybe already authenticate or land in the dashboard? How does the primary user flow look like step by step? Then what are the key features?

**12:54** · Authentication, billing, maybe per seat billing. What about an invitation flow?

**13:00** · What are the key features and how should they look like? Then also what are the functional requirements? What has to work right away? And finally, what's the target technical shape? NextJS, Remix, Tanstack, start MySQL, Postgress, who knows? But your agent has to understand the technical shape to not introduce, I guess, packages or dependencies that you don't want to use. And that's exactly what I did.

**13:28** · I asked myself all of these questions and then created this product requirements document. Right here, I have an executive summary. Then stack at glance. This is pretty much my target technical shape. Again, I don't want my agent to introduce new technologies. I want to use what I already have been using the whole time. Then, for example, product vision and positioning. What else? Personas, product scope and module map. Then, key configuration files and to end user journeys.

**13:59** · I listed out everything. And this here is beneficial both for you and your coding agent. you now have a full understanding of your application and your coding agent will have the same understanding. You will be on the same page which is super important and a game changer. Another thing I want you to realize is that it's way harder to go from zero to 100 than from let's say 80 to 100. Now you might say, "Okay, Chen, yeah, sure. I'm not stupid."

### From 0–100 vs. 80–100: Building a Rock-Solid Foundation

**14:30** · Um, so what am I trying to say by that? Well, what are we trying to do?

**14:35** · We are trying to implement a feature into an existing application into this starter kit. Now this starter kit has a very very solid a rock solid foundation authentication billing I guess eslint uh tests everything everything has been set up everything is production ready and therefore adding a feature into this rockolid foundation building on top of this rockolid foundation is super easy

**15:02** · especially for the agent because the agent can already reference specific files can understand how things should be implemented what should be done, what should not be done, how my code style looks like, etc. And I'm not saying that you can't go from zero to 100. It's totally possible. And there are rare cases where I have to also do that for some weird reasons. But would I recommend it? Definitely not. Will it be easy? Oh, hell no. Will it take forever?

**15:32** · Yes. You will spend a lot of time on just setting up the foundation.

**15:36** · Authentication, billing, rate limiting, security tests, perceived billing. This takes forever and getting it right is even harder. Will your agent hallucinate and assume things? Yes, because again there is no foundation. There are no rules. The agent is starting from scratch. So I would not recommend starting from scratch at all. I mean, if you have to, then do so. But if you have the ability to use some sort of foundation, some sort of solid foundation, a starter kit, then please do so.

**16:06** · And I'm not trying to sell my starter kit right here or say, "Hey, it's the best out on the market." I mean, it is the best, but at the end of the day, I want you to just use a foundation which is secure, scalable, and most importantly allows your agent to ship also secure and maintainable code. That's the most important thing in the long run. And of course, the biggest benefit is that you can ship in no time.

**16:31** · Going from 80 to 100, as mentioned, is easier and faster and more secure and more scalable than going from zero to 100. But with that out of the way, we can now finally continue with step three. And step three is to generate a plan, right? No, no, no, not so fast, my friend. Step three is to create a high quality prompt. Now you might say prompt. Okay, high quality prompt. How should we create a highquality prompt?

**17:02** · Should we just use this voice input and say hey I guess generate a plan for me.

**17:06** · Uh I don't know I use NexJS. Uh maybe check out my P. No, this is not a highquality prompt. And that's also not what I meant. You want to use your agent specifically to create a prompt. And this prompt will then instruct the next agent to generate a plan. But now you might say, Jan, why do we need a high quality prompt? Because at the end of the day, you just said, hey, this prompt will instruct the next agent to generate an implementation plan.

**17:34** · Why can't we just say, hey, generate an implementation plan to implement feature XYZ? Well, again, you want to have as much context as possible. And that's something that I have realized over the last few months while testing it quite thoroughly. The better the prompt was, the better the plan was. And the better the plan was, the better the end result was.

**17:58** · Because the agent hallucinated less, it assumed less and it rather stuck to the plan which got generated and which it used to build out the feature. So my biggest recommendation would be to spend less time thinking about features, your next feature, the

### Why High-Quality Prompts Matter: Better Prompt → Better Code

**18:16** · next groundbreaking AI feature, and rather spend more time thinking about your feature, thinking about your idea, thinking about all of the risks associated to it, all of the you could say problems, and spend a lot more time on generating a high quality prompt, and also spend more time reviewing the end plan. This is way more beneficial than you might expect and it will give you a way bigger output and with that hopefully way bigger MR.

**18:45** · So now you might say okay Jan you know what this makes a lot of sense. We now took quite a deep dive into the theoretical side of things and I guess it's now time to get started with the practical side of things. But how should we get started?

**19:03** · Because as you already know we want to create a high quality prompt. But should we do everything in one pass? H. So let's go back to our feature. What do we want to do? We want to invite members.

**19:17** · Is this a simple feature? Some might say yes, some might say no. In my opinion, this is not a simple feature because there are a lot of moving pieces. We have better off that we have to kind of configure. Then we need to connect our email provider to better off to send an email. Then we need an accept invitation page. Then we need the form itself. So there are a lot of moving pieces. And what am I trying to say by that? Well, I wouldn't recommend doing everything in one go.

**19:48** · And the reason for that is quite simple. Every LM has a specific context window in terms of tokens. And since this is a lot of work implementing this feature, the LM will just fail at some point. It will hallucinate. it will probably autoco compact and also LMs are quite linear in terms of performance to token usage. This means the more tokens you use the worse your LM becomes.

### Token Falloff Explained

**20:14** · Therefore, my recommendation is to always keep the features or the requests bite sized. Don't overwhelm your LM. It's still like imagine it's a small child. It can't do everything at once. And therefore we will actually do everything in three steps. Our invitation flow will now pretty much be broken down into three features. First of all the data model and contracts.

### Breaking Features Down into Bite-Sized Tasks

**20:41** · Then back and wiring. And finally front end and polish. And this is the procedure I would always recommend. Never start with the front end. The front end should build on top of the back end not the other way around. And since we now know that we can also continue with the prompt and again we will now start with the data model and contracts. This will be our foundation.

**21:06** · On top of the foundation we will then build the back end. And once we have the back end we can do all sorts of fancy stuff. So let's go back to cursor.

**21:16** · Inside of here for the model I will select opus 4.7. Then for the reasoning effort I will select extra high. And the reason for that is quite simple. From my experience and from my testing in general, this always gave me the best results because this gives me a nice balance between I guess performance or speed and reasoning. Medium reasoning effort, for example, is yes, very fast, but it does not reason enough. And max on the other hand is the complete opposite. It's super slow and it reasons too much.

**21:48** · So extra high is the golden middle. And then for the context window, I would recommend 1 million tokens. And that's because from my experience and also from the research that I saw, 1 million tokens work quite well with Opus 4.7, Opus 4.6 or Opus models in general.

**22:08** · The fall off isn't that bad. Now, here's the thing. This does not apply to every model. If you use GBT 5.5 or GBT 5.4 or I guess in the future GPT 5.6, six, then you will realize that the fall off with these models is quite big as soon as you surpass about let's say 200,000 tokens.

**22:29** · So, if you don't use an Opus model, I would recommend you to use the smaller context window. In this case, 272,000 tokens. It will give you a better result and it will also force you to create small byte-sized tasks. But let's go back to Opus 4.7. I will use again extra high reasoning and a 1 million token context window. But now you might ask me, Jan, how should we even prompt our agent? How should we articulate our thoughts?

**23:01** · Because at the end of the day, this here is a very important task and our agent should have as much information as possible. Right? Well, if you remember, I told you at the start, create a PR. It's a lifaver because if we now go back to my directory, this here is my PR. Then you will see here that I listed out this feature because it's a core requirement. So member invitations planned. It hasn't been implemented yet.

**23:31** · So the goal owners and admins of an organization should be able to grow the team by inviting people via email. Functional requirements invite by email. Persistent invitation record, pending list with revoke, email delivery, accept flow for signed in users and also signed out users, email mismatch protection, expiration, seat limit enforcement, literally everything is listed right here. And this gives our agent all of the info that it needs.

### Step 1: Creating and Reviewing a High-Quality Prompt

**24:01** · So that's why I said at the start, yes, PRDs are boring. Nobody wants to create them. But once you spend the time to create a good, and I really mean it, a good PRD, you will see how well it will pay off. It will allow you to ship faster than I guess this car going from 0 to 100, if you understand what I mean.

**24:25** · But yeah, let's now go back to cursor and I will get started with the prompt. And here's a quick tip. I would always recommend you to use this voice input or in other words, dictation feature. And that's because your voice or using your voice as an input is a clear winner.

**24:41** · It's way faster. It removes all of the friction and it also allows you to express yourself quite easily. Hey there, I want you to help me with a highquality prompt for my coding agent.

**24:55** · The end goal is to create an implementation plan. And the feature I'm currently working on is an invitation flow so that members are able to invite new members to their organization. Now, here's the thing. Right now, I want to only work on the data foundation. So, we need the database table for invitations, the matching Prisma model, and then also the shared schemas that define what a valid invitation looks like.

**25:20** · Now, for more context, I want you to check out my PR and specifically section 6.12 because it maps out how I want my this whole feature to look like. The member invitations feature and currently there are also already a lot of things in place. So, the invitation email template, the analytics event, the i18N strings and then also the permission slots on the owner and the admin roles.

**25:51** · Now, here's the thing. I want you to only focus on the data foundation for now. The API endpoints, the UI, the email sending logic, all of these are out of scope. Again, we want to focus on the data foundation. So, what I want from you right now is a highquality prompt that instructs my agent to create an implementation plan with all of the details that I just mentioned. As you see here, this is now my prompt.

**26:17** · It's quite big and this is something I would never actually ship and that's why we are using our agent to refine this prompt. So what I will now do is select agent mode the default one and I will click on enter again. Our agent will now take this quite detailed but not a very structured prompt and it will instead create an even better prompt and then we will use the even better prompt to then instruct our agent to create a plan.

**26:44** · All right, as you see here, cursor is now finally finished. So, let's review the prompt. Task implementation plan for the invitation data foundation. Produce an implementation plan only. No code changes for the data foundation of the member invitations feature in this repo. Do not start writing code. Correct.

**27:11** · Source of truth. Read the pr then the functional requirements table. reusable scaffolding already in the repo. What the rebuild must add back. Sounds good to me. Also, read the workspace rules on Prisma conventions and migrations before planning the schema shape in scope for this plan. the invitation database tables, then the matching invitation Prisma model and also the shared sort schemas in the schemas folder that describe what a valid invitation and the

**27:44** · inputs outputs that operate on one look like on the wire. Sounds good to me. Explicitly out of scope, no OPC procedures, any UI, the email sending logic, billing math updates. That's also correct because again we want to only set the data foundation then already in place. This all looks good to me. Current state. Yep, this is also all fine. Plan deliverables structure.

**28:10** · Current state, target database, target Prisma model, and then migration strategy. This all looks great to me. So what I will do is copy this prompt. And one thing that you have probably also realized by now is that I did not really go through everything line by line. And that's because you don't have to. It takes too much time and you need to just have a general understanding of what is being laid out right here and what is being requested later on from your agent.

**28:37** · You want to just make sure that there are no big bucks or I'm sorry not bucks but big problems that are incorrect or wrong assumptions. But if the general flow, the general prompt looks good to you, then you can just go with it. So I will now copy the prompt.

**28:53** · And what I will do is create a new agent. Yes, you heard right. I won't reuse the agent. The agent we just used is now our prompt engineering machine.

### Step 2: Creating and Reviewing the Implementation Plan

**29:04** · And to now execute this prompt, or in other words, to generate a plan, we will start off fresh. So this is a new session. I will paste the prompt inside of here. And I will switch into plan mode. Now, here's the thing. I want to add even more context. So what I will do is head over to better off and inside of here they have a section on invitations.

**29:27** · So what I will do is copy everything right here that is related to invitations. Now one thing you will realize here is that I just copied what is actually needed instead of just scrolling to the top and copying the markdown. And that's because I don't want to bloat the context window. Again you want to be kind of frugal if that makes sense.

**29:49** · So you don't want to just bloat your context window but rather try to be smart about it because again the less tokens you use the better your LM will be the performance the knowledge but also the less you will actually pay.

**30:04** · So let's now again go back and I will paste it down below. So I will say here documentation from better off. I probably made a spelling mistake but that's fine. I will now click on enter and our agent will get started with the implementation plan. It could also be that the agent will ask us a few questions later on. But hey, let's wait for everything to finish and then we will see.

**30:28** · All right, as you see here, cursor now generated the plan which means we can finally review it. scope is limited to the invitation postquest table. The Prisma model plus enum shared sort schemas in this folder and then procedures UI email sent and stuff like that are explicitly out of scope.

**30:49** · Correct. So current state audit migration da da da done. Okay. Then what do we have here? Processor migration history done. Invitation Prisma model done. Okay. So what's the end result?

**31:03** · Net effect all DB and Prisma side work is already committed. The only missing pieces are the packages shared schemas tests plus index reexport. So why do we already have all of the tables generated? Well, it's because the invitation model gets automatically generated whenever using the organization you could say plugin. So if I now open the off.ts config file, if I even find it.

**31:31** · So this one then you will see here that I use the organization plugin at least somewhere here organization and whenever you use the organization plugin it also automatically creates all of the necessary tables including for invitation flows. So that's correct. That's good. Let's continue. Target database shape already realized by this migration. That's fine. We can now skip over this. We don't really have to dive into it. No further DB changes are required for the data foundation.

**32:04** · Anything implied by future work is intentionally deferred. All right. Target Prisma model. This has already been set up. So let's continue. No addits to the generator are required.

**32:16** · only PNPM of generate rerun if better off CLI is upgraded then migration strategy the existing migration already matches the target shape we can then continue shared schemas net new work lives entirely in this folder a new file is the right call here because the invitation service has its own input plus output schemas correct plus an enum is similar volume to organizationts it avoids ballooning organization TS.

**32:46** · So we don't want to really like bloat the file if that makes sense. At the end of the day, you want to still kind of split by responsibility if that makes sense. And then imports of organization ro enum du from d are cheap and already used in the file. Good. That's nice. File placement. New file inside of here. New test reexport. That's also all fine. Let's continue.

**33:12** · Conventions confirmed against existing files. This also is fine. The invitation statuses const pupil plus type plus enum trio mirrors this right here. Okay, let's continue. Tests new file inside of here. Mirror the structure and assertion style of the organization test file at minimum invitation statuses. Invitation status enum invitation member schema.

**33:38** · This is also all fine. verification checklist the run in order PNPM of generate DB validate PNPM Prisma migrate this is also all correct so as you see here this plan is very detailed and the reason for that is because a we are using a quite good model opus 4.7 but also because our prompt was very very high quality and it answered a lot of questions so mostly agents fly blind as

**34:07** · you already know but since our prompt was very detailed and already pinpointed all of the you could say solutions because our initial prompt already said hey check out the PR the PR mentions this and that here's a general idea nevertheless research yourself as well and that's why our agent was able to produce such a high quality plan and

**34:29** · such a detailed plan then right here open questions and risks flag for resolution before next slice invitation expiry policy See right here, it gives me two options. Stick with better off default or pin a window. Now, you could of course answer all of these questions, and that's probably what you should do. Though, I will be super honest with you. I pretty much never do it. And that's because the agent, the LM is not stupid.

**34:56** · It will find the correct answer. It will find the best possible answer and it will try its best. So, yes, I could now say, "Hey, stick with the better of default. then I want this shape and I want this and I want that. But I won't do it. The agent will be able to pretty much imply everything by itself by looking at the PR. So there's no reason for me to right here intervene and answer all of these questions. So the plan is very good and I think we can now get started. So for the model I will again select Opus 4.7 and click on build. There is nothing to edit.

**35:28** · All of this is fine. So let's wait for everything to finish and then we will review the code together. All right, cursor is finally finished with the code generation which means it's time to review the code. I will click on review and let's see. So this is the off.generated Prisma file. In other words, the Prisma schema. We now have an enum invitation status. Okay, this here's a one to many relationship.

**35:56** · That's also fine. This is the invitation model. also looks good to me. This is the migration file. Let's see. ID, organization ID. That's all great. There's nothing really to get wrong. It's a relatively simple task. Then we reexport everything from this file. That's also nice. This is the invitation.

**36:18** · file. Let's see. So, describe invitation statuses. It contains exactly pending, accepted, and cancelled. Okay, that's fine. What else do we have here? Lower cases, mixed case email. Let's see.

**36:33** · Okay, that also looks fine to me. Trims surrounding white space before validating. That's also fine. Let's then continue. These tests are somewhat simple. So, you don't have to like look at every test though a general overview idea is quite um important. So, owner, admin, member, accepts, organization role. Let's see. There is already a thing that I don't really like and I will dive into it in a second. Nevertheless, let's for now continue.

**37:02** · Maybe you can already see the problem. Then let's maybe close the tests file.

**37:07** · What else do we have here or test file?

**37:09** · So, invitation statuses. And this is what I don't like. It's hardcoded as you see here. But this does not make any sense in my opinion because again, if we scroll to the top, we right here have an enum. This means it would make a lot of sense to use our enum, our database as the source of truth because there's a very important concept in programming which is don't repeat yourself dry. And right now what are we doing? Well, we are repeating ourselves. So this is what I don't like. Let's see.

**37:42** · Is there anything else that is not done very well? Well, no, not really. This all looks good to me. So this is now our invitation schema file. So this defines how the organization invitation will look like and the shape and we will use this for input and output validation. So here's what I will do. I will again use this dictation feature and I will say the following. So this looks good in general. Nevertheless, there are a few issues or one specific issue and that's that you repeat yourself.

### Step 3: Finding and Fixing Bugs

**38:11** · We have this invitation status or statuses and you pretty much redefine all of the statuses. So pending, accepted, cancelled. This does not really make any sense because our database is the source of truth. And you can use the Prisma schema, in other words, the enum invitation status enum, and you can use it inside of all of the other files. This will give us a source of truth without having to redeclare everything.

**38:42** · And this will just cause a drift in the long run. As you see here, I won't generate any plan. I won't generate any prompt. And that's because this here is a somewhat simple fix and the agent already has a lot of context. So it does not really make sense to now have a perfect prompt or a perfect plan. This year is good enough. Agents I guess sometimes are stupid but they are not as stupid as let's say 2 years ago. They understand this.

**39:10** · They will be able to pretty much digest everything and then fix the needed code. So let's wait for this to finish and let's see if the agent understands the issue and is able to fix everything. So it seems like our agent is now finally finished. The Prisma schema is now the single source of truth for invitation status. So let's quickly again review the code. What do we have here? So health enams. All right. Interesting. This is our enum.

**39:38** · We already checked that this is the migration file. Let's go to our actual file. So right here, invitation status from syntax kit database enums. This is exactly what I wanted. So instead of now reinitializing the constant in pretty much every place, we now use it or we now have a single source of truth, which also means we won't cause any drift in the long run. Then let's maybe also quickly check out our test file. So this is the P. This is the off schema.

### Step 4: Verifying the Changes

**40:09** · That's all fine. So invitation tests. So what do we have here? Uh D invitation status from invitation. Invitation status from the database. So now we also import everything from a single source of truth inside of here which is great. Now to verify that everything is also working. I will start the def server. So PNPM rundefs.

**40:39** · Everything is working which is what we wanted. So what I will now do is go back to cursor, click on review and inside of here I will click on this create branch commit and push button. This will then instruct cursor to create a new branch. Then it will commit everything and push everything because later on once we are finished we will create a PR and you can only create a PR if you have a branch.

**41:05** · So I will click on the button and the agent will now do everything needed. And while our agent is pushing all of the code, we can also continue by creating a new prompt. So if we go back to Excal or Teal draw, then you will see here that we are now finished with step one data model and contracts. And the next step is to continue with the back and wiring.

**41:30** · So I will head over back to cursor and I will reuse the session that we already used previously to create a prompt. And that's because this session, this agent already has a quite good understanding of our project, which means we don't even have to now reprompt this agent with so much detail. Again, this agent is now quite smart. So, I will say the following. Hey there, great job on this prompt. I want you to now help me with another highquality prompt for my coding agent.

### Creating and Reviewing the Prompt (Phase 2)

**42:02** · And the end goal is to again create an implementation plan for me to review. Now, here's a bit of context.

**42:10** · I'm now finished with phase one. I set out the data foundation, which means the database table, the Prisma model, and also the shared schemas now exist. And it's now time to continue with phase two, which means the back and wiring. So specifically we need the API endpoints or in other words procedures to send an invitation list pending ones cancel them and of course accept them. We also need seat limit math to count pending invitations against the plan limit.

**42:41** · In other words, we need to make this whole billing thing work. Then the abuse protection rules so people can't spam invites. And then we need to also wire in this whole sending functionality. So we need to be able to send an invitation email whenever someone is invited. Now here's the thing for even more context. I want you to again check out the PR specifically section 6.12 which lists out all of the requirements.

**43:15** · Now what is already in place? Well, specifically the invitation email template, the analytics event, the I18N strings, everything we already talked about previously, plus of course the data foundation, pretty much phase one.

**43:29** · Now, what is out of scope? I don't want you to set up the UI at all. Again, right now your task is to only wire in the backend functionality. So what I want from you right now is a highquality prompt which will instruct my coding agent to create an implementation plan.

**43:48** · Now I know I said hey we don't have to be super specific. Nevertheless, hey why not? Again using your voice as an input is a gamecher. It removes all of the friction and it makes it super easy to express yourself and that's why this prompt is now so big. But that's totally fine. So I will click on enter and the agent will get started. Let's see if our other agent is finished. And yes, it pushed everything. The first push attempt was rejected. That's all fine.

**44:17** · It fixed it as you see here. And now this is all fine. We could of course create a PR, but that's not needed yet.

**44:24** · We will create a PR once everything is finished. For now, we will just leave it as a branch or we will leave all of the changes on our local branch. So let's head over back to our other agent. It's currently working on the prompt. So let's wait for the agents to finish and then we will review the result. As you see here, our coding agent is now finished with the prompt. So let's review it. So task implementation plan for the invitation backend wiring phase two produce an implementation plan only.

**44:58** · No code changes for phase two. Then prior phase completed. You are on branch cursor invitation data foundation. That's all correct. Then D. These are all of the files that have been updated. Source of truth. Read the PR section 6.12 and also section 9.3 abuse protection. Then wall hierarchy email mismatch protection expiration seat limit must count pending invitations.

**45:26** · That's all correct. FK cascade on orc user delete that's also correct then scope back and wiring only in scope OPC procedures seat limit math abuse protection email and wire up analytics and then DTO's and tests so data transfer objects this is also a quite important concept I created a lot of videos on nexjs security I know this does not really have to do anything with this video but if you want to learn more please research Dell L data access layer and DTO data transfer object.

**45:59** · These are very core concepts that a lot of people don't know about even though they are super essential. Then explicitly out of scope do not include any of these in the plan. Anything in the app or in other words web folder on boarding anything in the docs schema or migration changes that's also correct. Then current state audit verify the phase one artifacts above that's also fine. Plan deliverables. Write the plan as a single markdown document.

**46:29** · Procedure design, input schema, output schema, middleware chain, underlying call, pre-post checks.

**46:37** · Then error mapping, analytics call site and wiring into this index file, which is pretty much the file that reexports all of the procedures. DTO layer, limit math, abuse policy update, extend the abuse surface, new policies, entry with two rules. That's fine. And tests to add inside of here. Then send invitation email call back show the exact registration on the organization plugin in the off config file.

**47:05** · Then URL composition nice render via this right here and error semantics. Throw versus fire and forget plan unit tests, integration tests, billing tests and off tests. Open questions. There are no open questions. That's because our PR is so good. And then style site every claim about existing code. So this is a perfect prompt. This is even better than the first prompt. And that's probably because the prompt or my personal prompt was even better, even more detailed.

**47:39** · Nevertheless, I will now copy this prompt and I will create a new agent session. I will paste the prompt inside of here. I will switch into plan mode. I will also head over to better off to the documentation because I want to add more context. I will search for the organization plug-in and then inside of here in the sidebar I will search for invitations. This looks correct and I will again copy all of this content because I want to add as much context as possible and I don't want the agent to just assume random things.

### Creating and Reviewing the Plan (Phase 2)

**48:11** · I will copy this and then down below I will say better of organization uh plug-in invitation docs something like that again I made a few spelling mistakes so we are now in plan mode we are in the correct branch as you see on the top and then for the model I will again use opus 4.7 that's it I will now click on send and let's see if the agent has any questions for us all right our

**48:42** · coding agent is now finished which means it's time to review the plan. Conventions used below. BA stands for better off. PR D refers to the following lines. Phase one audit migration present correct. That's good. Prisma schema present correct one naming nuance. Uh-huh. Naming nuance to flag. The inviter relation field on the invitation model is user user at relation da da da not invitation.inviter inviter the DTO needs to read row user

**49:18** · not a defect just an explicit reminder for the DTO step okay I guess then generate of schema present correct present correct one cosmetic nit interesting and what's the cosmetic nit so email normalization equivalent to specs no drift okay we exported through the schemas are on the public shared surface so what's exactly the nit I'm not sure but I guess. Okay, let's continue. Present broad coverage. That's good. Net audit verdict.

**49:48** · All phase one artifacts are present. The only thing to remember during phase two is that the Prisma relation field for the inviter is user not inviter. No redesign of phase one is required. Then step two procedure design. All four procedures live in this file. What better off 1.5.5 already in forces. Read end to end against the installed plug-in source. Then create invitation permission check. That's correct. Invalid email rejection. That's also good.

**50:19** · Then this all looks fine to me. Accept invitation. Expiration check. Important. Bad request invitation not found. Pending status check. Email mismatch check. This also all looks good to me. Implication. Our procedures are fin rappers. That's correct. Then invite member input. This is the schema output.

**50:39** · This is also a schema. This is the middleware chain delegates to and that's also fine. So ro hierarchy mirror what we have right here. Read the actor's role from the context. That's correct. And then this arguments better off's own owner only check at quat invites mjs.

**50:59** · Nice. Then what else do we have here?

**51:02** · Post call project the better off return value through this here. This requires reading the inviter user. That's also correct. Error mapping. Forbidden. Forbidden. Forbidden. That's all good. Then what else do we have here? List invitations. This is our input schema. Output schema. Middleware chain delegates to. That's also fine. Let's continue. Cancel invitation. Accept invitation. Let's check the middleware.

**51:29** · Authorize no with permission. Okay, this makes sense to me. Then what else do we have here? wiring into the index file. It will just reexport all of the procedures. That's correct. DTO layer add to organization invitation DTO inside of here mirroring the two organization member DTO. That's also nice to see. Seat limit math. That's needed for billing. Then assert within member limit. No body change required. It already reads usage.curren.

**52:00** · So consumer audit. That's nice. Test changes. Add invitation count to the hoisted mock. Uhhuh. Interesting. Then abuse policy update. What do we have here? This looks correct to me. PD update. This is all still centered around our abuse protection. Then send invitation email call back. This has to be registered in the off config file.

**52:26** · And to be specific, we have to pretty much update the organization plugin as you see here. So there's nothing to complain about. Call back signature verified enforce of email abuse policy and then URL composition. Let's see. Get app base URL process enval accept invitation invitation ID. That's exactly what I wanted. Analytics wiring. So this will use post talk. That's because my starter kit uses post talk. It will use an event. So this one organization member invited.

**52:57** · That's also exactly what I wanted. And then test plan unit tests. So what do we have here? Invite member rejects when actor admin tries to invite an owner. Of course, this shouldn't happen. And then also integration tests.

**53:13** · Full invite list except flow persist a member row. That's great to see. Billing tests. This will pretty much just extend the tests that we already have. And then off tests, we will just extend them even further. As you see here, we also have a few open questions. or in other words risks. Now looking at them there they are like valid questions.

**53:34** · So here decision needed stick with en or infer the localal from the request headers or for example hey this is the current rate limit should we maybe ruin different thresholds. So does it make sense to go through all of these questions and answer them kind of but at the same time as already mentioned our agent is not stupid and it will at the end of the day try to make the best and the most correct decision.

**54:02** · So would I recommend you to go through all of these question uh through all of these questions through all of these risks? I would yes but it's not fully required because again in most cases the agent will assume the correct things. I want to save some time in most cases and that's why I skip most of the time these questions. Is that not the smartest move? Yes. But hey, I like to live at the edge and I'm right here sharing my personal workflow how I do things. This does not mean that you should do it one to one as I do it.

**54:33** · Though it is what it is. So what I will now do is click on build and just hope that the agent assumes the correct things. No, I'm joking. We will of course review all of the code which also means we will find any bugs if there are any bugs or other words mistakes. This will now probably take a few minutes 10 or so because this is quite a big task. So let's wait for it to finish and then we will have to review the code because this here is a very very important task. It's a very detailed task.

**55:03** · There are a lot of moving pieces. And yes, this is still bite-sized. It could be that the agent gets everything right, but it could also be that it makes a few mistakes that it hallucinates. And that's why reviewing code is so essential and important because yes, shipping features with AI is easy. Reviewing code is annoying.

**55:24** · It's boring and it's hard because you have to understand the fundamentals. But it's very essential for your codebase to be scalable in the long run. And that's why I also said at the start, hey, it's important to use a starter kit that is actually done the right way. If you use a starter kit that has just been thrown together using some sort of coding agent, then you can just start off from scratch. It does not make any difference. You will just ship slop into production.

**55:50** · So if you use a starter kit, use a high quality one with the correct, you could say presets and with the correct fundamentals already defined. But yeah, that's enough. Let's now wait for the agent to finish and then we will review the code together. All right, the agent is now finished and it integrated everything. So implementation summary, new abuse surface one. Okay, added off.invitation invitation email to abuse surface union and policies map then seat

### Code Review (Phase 2)

**56:23** · limit math get member usage now counts nonexpired pending invitations in parallel with members this is what I wanted dto data transfer object new better off invitation and invitation inviter types plus two organization on invitation DTO mirroring to organization member DTO That's also nice to see. We now have procedures which is wanted. We need procedures again.

**56:51** · Um right here I'm using OPC and procedures essentially are API endpoints. Uh this is quite similar to TRPC. Then of server registered send invitation email on the organization plug-in with two enforce of email abuse policy calls preuser ID post email. That's also nice to see. As you see here, the agent also pinned invite link local to EN and that's what I wanted.

**57:21** · And this is quite interesting because when the agent generated the plan, it had like this questions and risks section. And inside of that said, hey, should I pin it to en the localal or should we read the localal from the request headers? I said, hey, I want to have EN as a default. But as you all know, we did not really tell that the agent. That's what I told you. And the agent nevertheless still was able to pretty much do the correct thing. It hardcoded en that's the primary reason why I stopped answering the questions.

**57:53** · The agent understands my style. The agent has pretty much access to my whole P to my whole starter kit with a very good foundation as already mentioned and that's why the agent is able to assume things so easily and that's also the reason why the agent is 99% of the time correct. It's that simple. We also have a few new tests. As you see here, unit tests, integration tests. What I will now do is review the code. As mentioned, this is probably the most essential thing that you have to do as an actual engineer. So, package.json.

**58:25** · This looks fine to me. Organization.ts. We import the type. Then what do we have here?

**58:33** · Export type better off invitation. Better offs invitation routes. All return raw adapter rows. Ro is typed string on the API path but the underlying Prisma column is nullable. Mhm. So we accept both. Status is a string on the better offs API surface. We narrow it via the schema at the procedure boundary. Okay. Interesting.

**58:56** · Then inviter projection used by two organization invitation DTO. Selecting only the four public fields keeps the DTO's surface aligned with this right here and avoids leaking sensitive user columns. So that's why a data transfer object is so important. We don't want to return everything. We only need to return the most essential fields. We don't want to leak anything. Then let's continue. Project a better off invitation role plus its inviter user onto our public DTO mirrors this right here. Uh-huh.

**59:29** · So this is the DTO interesting let roll organization invitation roll equals to null. If row roll is not equal to null then we use this. That's all fine. And then we return the data. Nothing to complain about. Then we have our test file invitation count v.fn. Okay. Invitation count. Mox invitation count. Then default to no pending invitations. So existing seat limit tests can keep mocking only. Member count. That's correct. What else do we have here?

**1:00:00** · So if counts pending invitations toward current usage get member usage base billing or one expect result to equal current three members two. Uh-huh. Mhm. Okay. Let's continue. So as you see here, I'm pretty much just trying to get a general understanding of the code.

**1:00:20** · What else do we have here? Throws when members plus spending invitations reach the plan cap. So mock result value 2 one code conflict that's all correct. Let's continue. Returns the orcs effective seat usage against the plants max members. So what are we doing right here? Member count pending invitations promise.all. That's good to see. You want to always have code run in parallel if possible. And in this case it is possible. Then what else do we have here? We just export everything.

**1:00:48** · So this is our index file that exports all of the procedures and then is able to mount them as API endpoints. Then invitation integration tests. What do we do here before each after each harness cleanup invitation flows integration full invite list accept flow persists a member row. So this is a full-on integration test. This is very essential and important. Invite cancel removes the row. That also all looks good to me. Let's continue.

### Finding and Fixing Bugs (Phase 2)

**1:01:19** · What else do we have here? Then organization.ts maps the better off API error from the organization plugins invitation routes onto the matching OPC error. Mhm. Function map better off or error. So if it's not an API error, we throw an error. Then constant API error equals to error body switch code. Uh-huh. I see. I see. I see. This is interesting.

**1:01:46** · Interesting. Do I like this? Yeah, this looks fine to me. Member invitations. So this is our procedure route. Then input validation dot use dot use. So this is our chaining middleware chaining. What else? Handler. Then constant actor member. We get this from our context. Uh-huh. What do we do here? Constant billing. Get billing state. This also all looks fine to me. We catch an error.

**1:02:13** · Then we use also post talk to track everything. Cancel invitation.oute input validation dot use. There's no output validation. That's because we don't return anything. So return null. That's what I want to see. Of API. So as you see here, this is a very simple wrapper. We just wrap the off API. That's it. But that's fine. That's what we wanted. Accept invitation.input. We have input validation.output. That means we have output validation.

**1:02:42** · And when we throw errors, do we use this? Yeah. O RPC error. That's good to see. And you know what? Looking at this code, I actually see a problem. Something that I don't like. Throw new OPC error. Now, here's the thing. You're not super familiar with this codebase.

**1:03:00** · Maybe you are also not super familiar with OPC. That's totally fine. But essentially, the problem is I have a base middleware. And this base middleware already defines all of the errors. unauthorized, forbidden, bad request, etc. And currently what we are doing is instead of using the space errors, the code defines new errors and that's not good because this creates inconsistency which you never want.

**1:03:23** · Let's see. Is there anything else missing? So I will scroll again to the complete bottom. What else do we have here? Integration test D promise. Okay, local host 3001. That's also fine. Environment variables, that's all fine. I think this is the only bug I really have. So here's what I will say. Hey, this looks good in general.

**1:03:44** · Nevertheless, you made a mistake. So in the procedures, you said throw new OPC error. But this is not what I wanted because here's the thing. I have a base middleware and this base middleware already defines base errors.

**1:03:59** · Unauthorized, forbidden, bad request, etc. And now what we have is pretty much a drift between our base errors that have already been set up and now the errors that you throw manually. This is not wanted. This is not good. At the end of the day, we need one single source of truth and then we have to use this single source of truth. So what I want you to do is again check out the base middle where look at the base errors.

**1:04:24** · You can also extend the base errors if there are not enough. But always um remember that one single source of truth is super important and that we don't want to repeat ourselves. Also looking at this map better off orc error what do we do here? We also throw new RPC errors. This is not good. Again we want to use the base middleware uh and then throw errors in or from this base middleware. Yeah please go ahead and fix that. So again let me give you a quick TLDDR. I have this base middleware.

**1:04:53** · The space middleware already defines errors and I want to reuse these errors because they already have a message. Some of them expect data. So at the end of the day, this is how clean architecture looks like. And that's why it's so important to review code. If you would not review code, then you would just ship this into main. And yes, this is not necessarily bad code. It works.

**1:05:15** · But in the long run you will have a lot of issues because then some errors or yeah at some places you will throw errors using the base middleware and then in some other areas you will throw errors manually. This will cause a lot of problems in the long run and that's why it's so essential to review code and also make sure that the code is scalable. So I will now click on enter and our agent will get started and hopefully fix everything.

**1:05:44** · So let's wait for it and then we will review the code once again. All right, it seems like our agent is finished. We factor summary the four invitation procedures and map better off orc error in this file no longer construct fresh new oc error code instances. They now use the typed errors constructor map produced by base errors in this middleware file.

**1:06:11** · So what else do we have here? map better off or error now takes errors as a parameter and throws via errors.conlict errors forbidden etc. Then the base errors type is derived once from type of base and via OPC's exported OPC error constructor map. Interesting. So let's review the code quickly. For that I will scroll to the bottom. So what do we have here?

**1:06:41** · Export type base errors. So with that we just get the base errors from the base middleware file. Then what do we do inside of here? Throw errors conflict.

**1:06:50** · Yes, that's exactly what I wanted. And then inside of here we should do the same throw errors forbidden. Now we dstructure the errors object from the handler which means we automatically get access to the base middleware. So this is totally finished which means we can now also commit and push this. For that I will go to the top right and click on commit and push. And we will reuse the branch that we already created. So invitation data foundation.

**1:07:17** · And since this is now finished, we can also finally continue with phase three which is the front end UI implementation. So I will now mark this as done. And how should we now continue with the front end? Well, it's quite simple. The workflow is simple. We will create a prompt. We will create a plan. We will review the plan and then let the agent implement the plan. It's that simple. So let's head over back to cursor. I will open the sidebar and I will again open my prompt engineering machine.

**1:07:49** · In other words, the session that we have been using to create new prompts. And inside of here I will say the following. Hey, great job on this prompt. Now I want you to help me with another highquality prompt for my coding agent. The end goal is to create another implementation plan. Now for some context, we are now finished with phase one, the data foundation, the data layer foundation, and we are also finished with the back and the wiring.

### Creating and Reviewing the Prompt (Phase 3)

**1:08:18** · And now it's time to continue with phase three, which is the front end UI and polish in general. So here's what I want you to do. I want you to bring the feature to the screen. So, we need a form to send an invitation in the organization settings. We need a list of the pending ones of the pending invitations in the organization settings. Then, we need the page the recipients will see when they click on the link that they got to their email.

**1:08:48** · So, pretty much like the accept invitation page. And then, I guess we could also make a small few polishes, improvements. We could for example update the onboarding route and nudge or suggest the user to maybe invite a team member and then we can also maybe create like an invite team members shortcut in the dashboard something like that a simple nice polish in general now for more context I want you to again check out the p and specifically section 6.12

**1:09:19** · which already lists out all of the requirements and core details. Now again what is already in place you probably already know it but in general the I18 strings then also the analytics event the of course data foundation the backend wiring everything we already talked about. So what do I want from you right now? Well I want to get a highquality prompt which instructs my coding agent to create an implementation plan.

**1:09:46** · And again, the goal is to now take the backend wiring built on top of it and create the front end UI so that users can finally invite members. Please get started. So as you see here, this again is a very detailed prompt and you already know why it's so detailed. The more context you provide, the better your agent will perform. It's that simple. So I will click on enter and then cursor will get started and create a highquality prompt for us.

**1:10:14** · All right, cursor is finally finished with the prompt which means let's review it. So task implementation plan for the invitation front end and polish. So produce an implementation plan only no code changes prior changes completed you are on the following branch and it carries phases one and two ahead of main. So right here add invitation data foundation and then wire invitation back end.

**1:10:46** · Then verify phase 2 by reading all of these files and the wire shape phase three will consume input and output source of truth read PD section 6.12 before planning. So right here all of the requirements are again listed.

**1:11:05** · That's why PRs are so important and then scope front end UI and polish only. In scope invite member form render inside of the organization settings gated on the invitation create permission. Sounds correct. Then pending invitations surface alongside the members list with revoke. Accept invitation page. add this route right here. So again, we have the localal and then we will have the dynamic invitation ID sign up login invitation ID query handling.

**1:11:38** · That's quite important because here's the thing. If the user is not authenticated, we will redirect the user to the off page to authenticate to the signup page or to the login page. And in the URL, we will append a query parameter to be specific the invitation ID.

**1:11:55** · This means then once the user authenticates we will redirect the user to the accept invitation route and then the user will be able to accept the invitation because accepting an invitation is an offgated I

**1:12:11** · guess you could say feature procedure only authenticated users are able to do so and if the user is not authenticated we have to authenticate the user so that's a very important step then local aware get accept invitation path Local invitation ID helper proxy entry inside

**1:12:30** · of here should be added to get localized entry path robots decide whether except invitation should be let's see excluded from indexing I guess we should probably exclude it there's no reason to index an accept invitation route this is core logic that does not need to be indexed it's the same thing with the dashboard route you also want to pretty much never index Next dashboard routes. These are internal routes, but marketing routes should always be indexed.

**1:13:00** · Then on boarding checklist, we add the invite a teammate step. Looks nice. Quick action.

**1:13:09** · We add the invite members shortcut and then tests for new components and accept route mirroring patterns already established. So, as you see here, having a strong foundation is a gamecher because now my agent can easily add new tests by just looking at all tests. And it's even better because it can now mirror them. So, it does not have to think through things so much, which again saves tokens and also keeps the LM smart. Then explicitly out of scope anything inside of here.

**1:13:40** · New O RPC procedures I18N keys and marketing pages already in place. Do not recreate and then current state audit. Yeah, we can skip over that. Plan deliverables. Phase 2 audit. Component map. Invite member form. Specify the path. Form library. Permission gate. RO options. Empty state versus populated state. Mutation.

**1:14:05** · Pending invitations list plus revoke row UI revoke confirm dialogue. Then cache invalidation. Server component wiring for the settings page. Accept invitation route. File layout behavior matrix. This means signed out. signed in. Signed in when the email does not match and when it matches expired, not found. So, wow, this prompt is quite good. As you see here, this prompt has pretty much thought of all of the site cases. And that's why I love generating highquality prompts.

**1:14:38** · Let's be honest, we both are probably quite smart, right? If you watch this channel, you are a smart viewer. You're not a slopp viewer. And the thing is I I would say that no one of us would be able to create such a good prompt that thinks of all of the side cases. At least I would forget it. Signed in, email mismatch, signed in, email matches, signed out, expired.

**1:15:02** · These are side cases. Then lock in and sign up, invitation ID, plumbing. I already talked about this. This is a very important feature. Get accept invitation path helper proxy update robots indexing on boarding checklist and then quick action update test plan unit tests and it wants to skip and to end tests. So this looks perfect to me and what I will now do is copy this prompt. So I will scroll to the top.

**1:15:29** · Let's create a new agent. I will paste it inside of here. I will switch into plan mode. And there is no real reason to add extra context inside of here. I guess you could again just copy paste the documentation from better off but it's not really needed since the backend wiring is already set up and this here is just front end related UI and the agent will be smart enough to figure everything out. So again I'm in plan mode opus 4.7 extra high reasoning and I will now click on enter.

### Creating and Reviewing the Plan (Phase 3)

**1:16:00** · Cursor will now get started with the plan generation. It might ask me a few questions, but hey, let's see. As you see here, the agent now has a question for me. Packages i18N currently has no test setup. Where should get accept invitation path unit tests live? Hm, interesting. Add tests inside of the web folder.

**1:16:26** · No new tooling in packages i8N. bootstrap the test in packages i18N and put helper tests there. Either is fine. Pick whatever is less intrusive and document the choice in the plan. So this is a quite interesting architectural decision. And to be super honest with you, I'm not quite sure what to choose though I would probably go with option B. Bootstrap the test in the packages i18N folder.

**1:16:57** · And the reason for that is because I want to separate or separate concerns and I feel like this would make the most sense. So I will select option B. And then the second question is how should invitation ID survive the O of round trip on off/lo and off/ignup. We use the existing syntax kit post login redirect session storage key.

**1:17:27** · Uhhuh. encoded in the callback URL. So better off carries it through the provider redirect. Add a new dedicated session storage key. So here's the thing. A session storage key is an option. It's valid, but it's not the best option at all. It's quite, let's say, frugal. It can be removed or deleted quite easily. So I wouldn't go with that option.

**1:17:53** · I think option B encoded in the call back URL is the smartest possible solution because it's not easy to lose this call back URL key because it will be passed through better off and then through the ooth off provider and so on and there are no storage keys that we have to think about. So this is the way smarter option. So I will select B and click on continue. After 30 minutes or so cursor finally created the plan. So let's review it. Phase 2 audited.

**1:18:23** · Before adding any code, verify the phase 2 wire surface and the I18 keys. This plan depends on every artifact below was inspected on cursor invitation data foundation. So the branch schemas, yep, that's correct. OPC procedures in the API folder. Invite member list invitations. cancel invitation implementations and the better of error helper right here live inside of here.

**1:18:53** · Correct. DTO in the API folder. Seat math in the API folder. Email sent plus URL composition. Invite link local is hardcoded to en 18N keys present in both local. No new keys required. That's always good to see. drift gaps surfaced by the audit. Open questions, not silent fixes, no copy for the accept page itself. None of the organization invite or organization members covers the accept invitation card prompts. You've been invited to ORC XYZ.

**1:19:33** · Interesting. See section 15 plan reuses this right here for the error toasts and reuses the better of error message returned by this right here. Then packages i18N has no test run script. Mhm. And then no list organization members test file exists today. The users brief references it as a pattern to mirror. Mhm. All right. Then component map. Let's see. Accept invitation. New directory. Invitation ID. Page.tsx. New server entry. Read session. Renders client dashboard layout.tsx.

**1:20:11** · Uh-huh. Edit, mount, accept, invitation on land, organization settings, page.tsx, prefetch. Mhm. Mhm. Mhm. New client UI. New render state matrix. Small client effect. Mhm. Mhm. Then new react hook form Z resolver. That's fine. Wrap contents in tabs. No existing test today. Extracted child render inside the invitations tab. I like the component map. So no edits in the API folder or folder, no backend changes, just front end changes. Then invite member form.

**1:20:49** · Okay. Form library use forms resolver. So it will use weap took form for client side validation. Server side validation is already handled by uh OPC. So input validation and output validation. Then permission gate pull active member ro the same way as inside of here. Let's see of client organization check wall permission roll permissions that's correct. Then wall select we use organization roles plus wall rank. Let's continue. Mutation use mutation. OPC this is the correct pattern.

**1:21:20** · This is something also that LMS often hallucinate with. OPC has a very specific way on how to interact with tan stack query and often LMS hallucinate and do it the incorrect way. But since I already have predefined patterns, since my starter kit already has a solid foundation, the agent is able to grasp the concept quite easily. And that's why it right here instantly added the correct, you could say, way on how to do everything.

**1:21:50** · Then on error is defined error switch error code case forbidden toast error. This looks correct. Pending invitations list plus revoke tabs in list organization members. Grab the existing card body of this with a tabs d containing two tabs content panes. That's fine. First split pull the new pane into this. So list doesn't bloat past the current 450 lines. Uh-huh. Row UI each pending invitation renders the email row. Yeah, this is also good.

**1:22:23** · Let's continue. Server component wiring. Addit the following inside the if branch currently D conditionally prefetch. This only when the active members can issue invitations without this gate. The procedure rejects with forbidden. Let's see. Query client prefetch query. Yes, this is how you do it. Computer actor wall from the prefetched active orc. Let's see. Duh. Ensure query data. Okay. Okay. Yeah, this looks correct to me.

**1:22:53** · Promise.all. all to do everything uh in parallel then mount inside hydrate client. This is important since we want to prefetch our query. We need to also then you could say hydrate the client so that we are able to access the data from the serverside storage. So let's continue. Accept invitation route file layout. This is a dynamic route server entry exports metadata. No new layout file. The default one already wraps uh children in the local provider. Let's continue.

**1:23:25** · Implementation notes signed out state card with title is the wrong key. Mhm. Not good. Signed in mutation runs on mount. Use oneot use effect guarded by a ref. So yak 19 strict mode double invocation doesn't fire twice.

**1:23:43** · Okay. Then lock in and sign up invitation ID plumbing. The user confirmed strategy is to bake invitation ID into the call by QRL query string so it survives every post of path. So perform changes lock in form. As you see here we will get the invitation ID from the search params because this will be a query parameter and we will do the same thing with the signup form and all of the necessary forms. Well there are only two the login form and the signup form.

**1:24:14** · Then accept invitation onload. This is a new component. Small client effect mounted in this page. What do we do inside of here? Use W. Use search params. Use path name. Use router. Um, let's see. Use mutation. This is correct. Use effect. So I see this is like a small client side effect. Side effect. I think we can leave it as is.

**1:24:36** · Then toast key choice. Yep. Get accept invitation path helper add it inside of here. Let's see. This is correct. Then proxy update edit the proxy. So unproxied accept invitation ID redirects to the localal route. This is of course important. Then robots indexing two layers both required. Page level metadata. And then inside of here what will we disallow? We will disallow all of these routes. This is what we want because there's no need to index the accept invitation route.

**1:25:05** · Then on boarding checklist update extend the props with member count number. Insert new step between organization and billing in the use memo array. So this will look as following. This is nice to see. Then quick action update. Add invitation members to the ID union. This looks correct to me. Test plan. New unit tests. What else? Duh. Uh-huh. Okay.

**1:25:30** · Okay. Get accept invitation path test new file cover all helpers. Currently untested at the package level, which is not good, but we will change that. Proxy test extension addit this redirects off and on boarding entry routes. Let's see. Accept response away to proxy. Huh. Ah, this is to test it. Ah, this makes sense. Okay, let's continue. Skip play right E2E. There's no reason for that. And that's already it. So, open questions and risks. Except page copy.

**1:26:02** · No existing I18N keys cover the accept card prompts. Not great, but okay. Distinguishing sign up versus login origin for toast keys. Okay, that's important. Serverside permission check in this file. Users of client from a server component which works because the helper is pure no fetch. Confirm this pattern is acceptable or prefer importing the same role permissions table from syntax kit of server side and calling it directly. Yes, we should probably go with that.

**1:26:36** · Then get accept invitations path adoption in phase two refactoring to use new helper would remove the inline the d constant and is the natural cleanup but the user excluded backend packages. So let's do the following. Um look we can get started with the implementation now in regards to your open questions and risks. Let me quickly go through them.

**1:27:00** · So for step one or for the first question accept a page copy please update it add the necessary keys. Then in regards to distinguishing signup versus lock in origin for toast keys just go with the update. So yeah it's worth doing worth updating it. Server side permission check inside of the file. So point three yes it would make sense to update this whole check to be on the server side.

**1:27:23** · So you can use or you can import the same role permissions table from syntax kit off server side and then call it directly in regards to get accept invitation path. Yeah, refactored. It's fine. Then revoke row removal mechanism. Let's see what should we do right here.

**1:27:45** · Yeah, go ahead. Update it. Then accept invitation route. Should it require email verification?

**1:27:54** · No, I don't think so. Then yeah, you can create uh the test setup. And then finally 4.80 80 of off call back URL stripping some IDPS reject very long state parameters the invitation ID is a short better off ID yeah this is all safe this is fine so please get started

### Code Review (Phase 3)

**1:28:12** · with the implementation as you see here in this case I answered all of the questions and I know at the start I said hey in most cases I skip over it and that's true but in this case we have a very very important task and it's not an easy task like for example this plan generation took 30 minutes. Again, this is a very, very complex task. There are a lot of moving pieces, a lot of pages that have to be updated. And that's the reason why I also wanted to answer all of these questions. I want my agent to make correct decisions.

**1:28:44** · And in this case, I don't really want the agent to assume things and make mistakes because again, the more the agent knows, the better the result will be and also the less hallucinations will happen. So I will now click on enter and our agent will get started. As you see here, we also still only used up 17% of the context window. So 170,000 tokens.

**1:29:10** · That's already quite a bit for a plan generation. Nevertheless, since Opus has a quite small falloff, it's fine enough to continue here. But if you use GPT 5.5, GPT 5.6 six or something like that.

**1:29:24** · I would highly recommend you to also create a new session. And inside of here, I got a warning. That's because I'm still in plan mode. I now switched into agent mode and the agent will get started with the implementation. This will probably take 20 minutes or so. So once finished, I will come back and we will review the code together.

**1:29:46** · Hallelujah. Kasa is finally finished. So let's quickly check out the summary. So what did the agent do? I18N and path helper new get accept invitation path local invitation ID. Inside of here we exported from syntax kit I8N the package. Then added the test config test one script and 11 passing path tests.

**1:30:12** · Great. Then new of accept invitation block inside of here. D. That's also correct. Then back and refactor small scope expanded with your approval. Then send invitation email now composes the link via get accept invitation path.

**1:30:30** · Let's continue front and route. Then this right here now has also the following metadata export and then this uh covers all five states of form plumbing. What do we have here are the query parameter you search params. This is fine. Then settings page. Now conditionally prefetches list invitations using a serverside permission check. You want to always favor serverside data fetching, serverside mutations, serverside checks over client side checks.

**1:31:00** · They are way more secure and I would even say that they scale way better in the long run because there will be less side effects and bugs. Then let's continue. proxy and robots added this to the get localized entry path. So unprefixed inbound links redirect to the cookie preferred local then tests right here we have a few and that's already it. So let's review the code together. We first of all now have this accept invitation page.

**1:31:31** · So this is a server component as you see here. We export metadata. This here is a non-index route. Interesting. Then interface accept invitation page props. We expect two things from our params.

**1:31:48** · First of all, the local and then the invitation ID. Since this is a dynamic route, we can access this data. And then this here is a normal server component async function. And we get our params which are awaited. That's a change with I think next JS15 or 16 that got introduced. And then we have a client component. Then let's continue. This is our organization settings page. Inside of here, we get the invite member form, the roles, and then get organization role. And what do we do inside of here?

**1:32:19** · We first of all pretty much fetch all of the data using promise.all. This means everything gets fetched in parallel. And then we get the actor ro can view invitations and stuff like that. And finally, we render the form. So I can collapse this. Let's continue. Then this is our dashboard page. We just render this form. So accept invitation onload and this is not the form. I mean this is the component and it's a side effect mount.

**1:32:45** · So I think this component probably just has a use effect hook inside of it and then it will check if the user is authenticated and if we can just auto accept it. So we can collapse this. Let's continue. This is our robots.ts. This is fine. We can continue. Then what do we have here?

**1:33:03** · This is a test file. So v.hoisted hoisted replace signed out session. This looks correct. V do mock next navigation replace mox.replace. Okay, I think we can collapse this. This all looks correct to me. Then let's continue. Accept invitation client. This is a client component. What do we do inside of here? Accept invitation client props.

**1:33:27** · We expect an invitation ID. Error state mismatch expire generic. Uh-huh. Then we get the invitation ID. We use the use translation hook. Then use session. Use state. Mhm. Okay. Okay. Okay. Fired. Use ref. What do we do here? Use mutation on success on error. How do we throw errors? Let's see. Mhm. Okay. This is also fine. Then let's continue. Use effect. This is a side effect. What do we do inside of here? Auto accept once the session resolves. Let me also make this a bit bigger. Then let's continue.

**1:34:02** · handle sign outs start sign out this is correct let's continue if our state mismatch and we render this empty state okay I will collapse this then this is our accept invitation onload test file so it tests if everything works again inside of here we use the test and then we mock everything so we can collapse this then this is the accept invitation on load file again this is a client component what do we do inside of here.

**1:34:32** · Let's see. Reads invitation ID from the URL and fires O RPC organization accept invitation exactly once on dashboard mount. The query param is stripped via router place. Mhm. Interesting. Constant fire use ref mutation use mutation account just created. Uh-huh. This is interesting. Invalidate queries. This is done the right way. That's good to see.

**1:34:59** · Then what do we do inside of here?

**1:35:00** · account just created error messages.

**1:35:03** · Fine, fine, fine. This is interesting code. What do we do here? Consume account just created flag boolean if type window undefined raw Windows session storage get item. Hm. With that, we check if the account has just been created. This is interesting code, but let's continue for now. Then lock in form. Let's see. Use memo. Use search params. Build the post of callback URL with the optional invitation ID. So this is a helper function. Is a helper function needed? Not really. We can just inline it. But hey, it is what it is.

**1:35:36** · It's fine. Then let's continue. Search params. Use search params. Invitation ID. Use memo. Now this is interesting. The use memo and use callback and all of these hooks are not really needed because we have the React compiler. And I think I also set up the React compiler. So normally I would also instruct the agent to strip this code.

**1:35:55** · But I I mean it does not hurt. It's not like that. This now breaks the React compiler or something like that. It's just code that in theory is not needed anymore, but it is fine. So, let's continue. What do we have here? Build post of callback URL. This uses the helper function. And then inside of here, we do the same thing. Interesting.

**1:36:15** · So, the general code looks good. What I will now do is continue and review everything because I know it's kind of boring. Nobody wants to watch it. And once finished, I will come back. So, I now went through 2,000 lines of code, and what should I say? In general, the code is clean and good. Yes, there are cosmetic things that I don't like, but is that something that hinders us at chipping this into production? Not really.

**1:36:39** · Like, yes, in a production scenario, I would probably also update these cosmetic things just to have the peace of mind, but it does not really matter. So, since the code is fine, we can now continue by testing out the feature. For that, I will go back to my starter kit to the dashboard. And inside of here, we now have a new form, invite team member, email address, ro send invitation. And inside of here, we already see the active members and the invitations. Currently, no pending invitations. So, let's test it out.

**1:37:10** · I will invite myself right here. The role will be, let's say, admin. Why not? And I will send the invitation. And do we get any toast? Let's see. It's still pending. Pending. Pending. And it says invitation sent successfully. So, I will open Gmail. Interesting. I just checked my email and I did not get anything.

**1:37:35** · That's quite interesting. So, here's what I will do. I will go to the invitations and I will revoke this one again. This will now take a second. We should again get a toast. And then I will show you something. If I now go back to my terminal and scroll to the top, you will see here that we got an error. Hm. Off. Ause protection unavailable. Surface of invitation email face preverification reason missing config. So better off failed to run background task.

### Finding and Fixing Bugs (Phase 3)

**1:38:03** · Error sending invitations is temporarily unavailable. Now this is kind of weird. I did not expect this error. So let's debug it. I will copy this and let's head over back to cursor. Inside of here I will now say the following. Hey there.

**1:38:21** · So, I just reviewed the code. In general, it looks fine. Sure, there are small things that could be changed, but for now, it's fine enough. The UI also looks good. Nothing I want to update right now. Nevertheless, we do have a problem. Whenever I add an email and invite a user, I do get a toast, a success toast, and I can also see the user in the active invitations or in the pending invitations, but I get an error.

**1:38:46** · So, the email never arrives. And in my terminal, I get a better off error. So the error is now pasted down below. And what I want you to do right now is analyze the error and try to find the cause. I don't want you to fix the error, but rather again find the cause and explain the problem and then also maybe quickly how to fix it. So as you see here, I did not ask my agent to instantly fix the problem. And the reason for that is because I don't want the agent to just test random stuff.

**1:39:14** · I want the agent to try and pinpoint the exact problem because if I would now just say hey fix it the agent might try I don't know solution A B C D E F G and maybe they are all wrong. So instead of just randomly guessing I want the agent to verify explain the problem. All right so what's the cause? The error is the fail closed abuse protection check firing and send invitation email because upst isn't configured in my local ENV.

**1:39:49** · It's that simple. So as you see here that's kind of a security you could say configuration made by me. So I have a fail closed abuse policy. So if the environment variables for upst everything fails and upsted it enables rate limiting. So that's quite good to see that the agent was able to figure everything out. So to fix that, all I have to do is add the missing environment variables. The env keys have now been updated.

### AI PR Code Review: Final Code Review

**1:40:17** · I will restart my dev server right here and I will now try to invite myself again. So I will add my email. Then for the role I will select admin and I will click on send invitation. This is pending. And again in a second we should get a success toast. And as you see here, invitation sent successfully. And if I now click on invitations, you will also see right here, invited as admin. And if I now go back to Gmail, you will also see right here, you are invited.

**1:40:49** · Jan has invited you to join Jan's organization.

**1:40:56** · Wow. Groundbreaking stuff. So I will now open this in a new incognito window where I'm not authenticated. And now we have this page. You've been invited. So what I have to do is now create an account because I don't have one. And please look at the URL. As you see here, we now have the invitation ID, which is super cool. I will now continue with Google. I'm now signed in and invitation has been accepted. This means if I now go to the organization settings, you will see that I will be a new member.

**1:41:30** · And yes, members too, owner and admin.

**1:41:33** · And I'm an admin. And if I go to the invitations, there are no pending invitations anymore. And the thing is, as you see here, I can't do anything with the actual owner. But if I go back to my owner account, you will see here that I can update the admin role. I can now change the role of this invited user. So I can say, hey, you are now a member or something like that. And that's quite powerful. And since this is now finished, we can finally push the code and create a PR.

**1:42:01** · For that I will go back to cursor and then inside of here I will say commit and push. As you see here everything has been pushed. So I will now head over to GitHub and this is our branch. So what I will do is click on compare and pull request. Inside of here we now have a title. The description is empty. And in theory if you want to really follow best practices you should add a detailed description if not done automatically.

**1:42:29** · But since I'm a solo developer and since I work for myself, there is no real reason to add a description because I know what every PR is doing. So there's no need for me to reference or add any description. So I will now create a pull request and this will then get started. Now as you see here, as mentioned, one thing I would always recommend you to do is to add AI reviewers. What do I mean by that? In this case, I have cursbot set up. By the way, this video is not sponsored by Cursa. I pay for everything myself.

**1:43:00** · But the reason why I like Cursa Buckbot or in general AI review tools is because they catch things that I missed. Again, this PR is quite big. How many lines do we have here? 4,600 added lines. There is a lot of code to review. And I'm very certain that I missed something. You probably also missed something. That's fine. That's why AI review tools are so powerful and so essential. Yes, they are not free.

**1:43:28** · Yes, they cost something, but you will be thankful, especially if you want to ship something into production and make some money. I often catch myself not reviewing everything and then cursor buckbot says, "Hey, you missed this and it's a valid buck." So, trust me, use some sort of AI review tool. Another tool I can, for example, recommend is called Devon Review. I think it's now also paid. It was free back then. It's also very good. I use it myself. So I personally pay for both cursors buckbot and then also devon review.

**1:43:59** · They then catch most of the valid errors. I of course also review them and then I just again interact with my LM and say hey this is a valid bug. Please fix it yada yada yada. So this is how my AI coding workflow looks like. So let me again give you a quick recap on my AI workflow. Everything starts with the definition of the idea.

**1:44:21** · I ask myself these questions, sometimes even more questions to fully understand what I'm trying to do because that's the most important thing. You need to understand what you want to do and what your LM should do for you. Secondly, I then continue by defining bullet points. Hey, these are the core requirements. Once that's done, I continue with the PR if I don't have one already.

**1:44:46** · In most cases, I already have a PR set out because a PR, as mentioned, is fundamentally the most important thing in your codebase whenever dealing with AI coding agents.

**1:44:59** · Having a well ststructured PR that actually explains your product, your features, your requirements is a necessity in my opinion. Once that's done, I continue to actually break down the feature into small chunkable pieces because again, we right here added 6,000 lines of code. One agent will hallucinate. One agent is not able to add 6,000 lines of code reliably, but breaking it down to 2,000 lines of code per agent is manageable. Or maybe 1,000 lines or 1.5,000.

**1:45:32** · At the end of the day, keep things bite-sized. Your agents will thank you and you will thank yourself.

**1:45:40** · And as you see here, cursus buckbot even now gave me an error or a warning. Hey, assert within member limit runs before the code determines whether create invitation will refresh an existing invite. This is a valid bug that I missed because again we reviewed a lot of lines of code. So what I would now normally do is copy this, go back to cursor, say, "Hey, this is a valid bug.

**1:46:04** · Please fix it." But now I think you all know how my workflow looks like. I hope you could learn a lot in this video.

**1:46:10** · This was a very very detailed and thorough video. I don't think anyone is sharing so much actual free sauce with you guys. But hey, that's the benefit that you get when you are subscribed to my channel. Nevertheless, I hope you enjoyed the video. Please don't forget to like and subscribe. It would mean a lot to me and my heart. So, please do it. And without any further ado, see you in the next video. The next video will probably be about shared CN UI or something like that. But yeah, that's it. Over and out. Bye-bye.