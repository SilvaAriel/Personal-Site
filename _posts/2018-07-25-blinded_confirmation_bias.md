---
layout: post
title: "Don't get blinded by the Confirmation Bias"
ref: blinded_confirmation_bias
date: 2018-07-25
categories: cognitive_bias
lang: en
---

You know when you (think) know how to solve a bug, but somehow you spend ~~hours~~ a long time on it? Only to realize you were wrong all the time and that the solution was other?

Well, you can thanks the <a href="https://en.wikipedia.org/wiki/Confirmation_bias">Confirmation Bias</a>.

### It's a trap!

I am creating a <a href="https://github.com/SilvaAriel/presente">Nodejs CRUD with TDD</a> for learning purposes. And I got to the database test. 

The test creates a fake data, saves it using Mongoose and runs the test using that data created. After all the tests, the collection (where all the data is) is erased automatically.

I successfuly did everything above except for the part of erasing the collection. Somehow the fake data created at the beginning of the test was being erased before the end of the test.

Mocha (a test framework) has a hook called "after()". And it does exactly what it states: it runs after all the tests. But in some way, the collection was being erased before the end! So I thought "I probably don't know how Mocha hook works".

For that, I went stray to the <a href="https://mochajs.org/#hooks">hook documentation</a> but it took me nowhere. Don't get me wrong, the documentation is great, but I couldn't find much about "after()". It only stated the obvious: it runs after all tests.

I began to think there was a bug on Mocha. I mean, the chances of the framework being wrong are higher than we being wrong. (We all have thought that before, right?)

After more than an hour (I timed it) trying to solve that, I got tired. I don't know how, but I began to thought that maybe the problem wasn't in the hook, but in the Mongoose function.

I found that function in a <a href="https://stackoverflow.com/questions/10081452/how-to-drop-a-database-with-mongoose">StackOverflow question</a> and I remembered there was two ways of erasing the collection. 
Then I adapted the second one to my test and it worked! Simple as that. My tests were running smoothly without any error.

### Conclusion

I came to one conclusion: I'm freaking dumb! No, I'm just kidding. The answer is not that easy.

### What happened?

I got blinded by the Confirmation Bias.

I was so sure the problem was the "after()" hook that I turned shortsighted. I could not see anything but that problem. And the more I searched (without finding anything) the more I closed my self to other solutions.

Now it's all clear. The problem was that the function I used was async:
```javascript
//classes is the collection's name
mongoose.connection.collections["classes"].drop((error)=>{
    if(error){
        console.log(`Drop collection error: ${error}`)
    }
})
```

No wonder the database was erased before the test ending! And I knew that Mongoose returned Promises! But again, I was too focused on solving what I thought it was the problem that I missed even that.
I even thought the problem was Mocha's fault.

<span style="color: gray">Sorry Mocha, you are awesome!</span>

**When we are blinded by the Confirmation Bias, it's always somebody elses' fault. Never ours.**

If this story resonates with you, you're not alone. I think we all programmers face that problem frequently. So, to help us not falling in that trap again I've come up with 4 steps to follow while debugging. I hope they really help you.

### Preventing the Confirmation Bias

The steps are:
1. Break the function down.
2. Choose 2 parts you think might be causing the problem.
3. Set a countdown timer to search fot their solution.
4. Search.

# Explaining
1. Break down the code's logic to be easier to understand it.
2. This part is the most important one to prevent the Confirmation Bias. You are trying to solve a bug and you probably have thought about a possible solution. In order to prevent you getting stuck on it forever, you'll choose another possible solution to try as well.
3. This one complements the last point. Set a countdown timer to avoid searching forever for the one solution you think will solve the problem. I could be one <a href="https://en.wikipedia.org/wiki/Pomodoro_Technique">pomodoro</a>
4. Go search!