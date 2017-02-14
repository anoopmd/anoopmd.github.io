---
layout: post
title: Why I chose eslint over jshint
---

It all began when I wanted to add a rule in jshint which would throw an error upon encountering trailing whitespaces.

So I googled it which led me to this [SO Link](http://stackoverflow.com/questions/23767225/what-should-i-do-about-trailing-whitespace-in-jshint-2-5-0) which stated that this functionality has been removed from Jshint and that [Jscs](https://github.com/jscs-dev/node-jscs) is a better tool for this.

When I visited JSCS, I found out that it has been merged with eslint.

From my search in the limited time I had, it seems that jshint's main goal was to look for error prone code and JSCS was more interested in ensuring style convention.
And [eslint](https://github.com/eslint/eslint) seems to have both. (JSCS is now merged with eslint).

I thought to give it a try and was amazed by it in the first 15 mins of using it.

Here are top 5 things which I liked about eslint and why you should be using it.

<b>1. Elegance and Consistency matters</b>

The above mentioned attributes are as much of importance to me as much as the problem the code is intended to solve.

I do not want trailing spaces, I do not want unecessary spaces in between lines. I do not want any line in the code to be more than 100 characters long and the list goes on.

Eslint solved this problem for me. When I switched from jshint to eslint, I got to see an extra 50 errors in my code and it was fun correcting them, tweaking eslint rules wherever required. That feeling when a sculptor chisels out fine inconsistencies in the statue.

<b>2. Time matters </b>

I get to review code from my peers, superiors and sub ordinates. I do not want to waste my time in checking the style errors. When integrated as a commit hook in your workflow, I can ensure that the code is according to the standards when I get a PR.

And then I do not have to rejct a PR because it had a trailing whitespace. And then I have to sent it back, they have to correct it, and then they resend it to me, And I have to check it again and GOD save me if I see that another agreed upon convention was violated.

Just try eslint. Thank me later.

<b>3. Extensibilty</b>

I know that you could extend stuff in jshint, but not sure if the below feature exists.
In eslint you could add the google's node eslint config (https://github.com/google/eslint-config-google) style guide as a dependency in your package.json
and then extend it in you eslint.rc I dont think you could do that in jshint. I may be wrong though.

<b>4. Because software is an art</b>

Its hard to explain this part. All that I can say is that when I write a piece of code, I want it to be modular, extensible, scalable, consistent, simple and most importantly beautiful.

How can code be beautiful? Well, its beautiful if you genuinely feel respect towards the programmer who wrote it.

I can attest for myself that eslint helped me more than jshint in ensuring that my code was beautiful.

For example every function in the enitre codebase has a single space between the closing paranthesis of the argument list and the opening paranthesis of the function body.

I cannot attest for you, You need to go and find it yourself.

Little things matter.

<b>5. ES6</b>

Again, I am not sure, but it seems eslint has much better support and style checks for ES6 code when compared to jshint.

This is my intuition. I do not have time to check whether jshint is really better than eslint at ES6 error and style checks. I am a ES6 amateur BTW.

(Not to sound like an egoistical asshole here, but most of the times my intuition is right, and when it is wrong I do apologize and correct myself instead of taking a defensive stand to prove my own point)

Last but not least, go checkout the github stars and npm downloads per month.

I agree that these stats are do not guarantee the number of people who are using it, but is definitely a metric that you can see to check the popularity.

(I agree that jshint has more stars, but its been there for long time and eslint has traction)

To end this blog,

There are a lot of existing projects using jshint. I do not advice to make the move to eslint instantly.

I am not a fan of switching technlogies when you come across a new fancy tool.

It would be better to first try it out, weigh the pros and cons of migration and then proceed.

Thanks for reading. Good day!