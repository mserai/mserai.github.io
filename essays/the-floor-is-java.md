---
layout: essay
type: essay
published: true
title: The Floor is Java(script)!
date: 2017-09-01
labels:
  - Javascript
  - Tutorials
  - WODs
---

<img class="ui medium left floated image" src="../images/javascript.png">

## The Floor is Java(script)!

I associate the learning of programming languages with learning how to run before you walk. The FreeCodeCamp Javascript modules are a fantastic tool to get you started and have prepared me with the vernacular of Javascript. I am not truly a beginner when it comes to coding, I have had some practice with Java for two semesters and C/C++ for another, but it is always nice to have a refresher of sorts. When studying programming languages, I try to think of them as foreign languages, where I wish to convey expressions and emotions rather than memorize specific words.

<hr>

## Swimming through Java(script)

Although I have never touched Javascript before, I found it to be rather welcoming. Almost like a friend from down the street that you haven't seen in 10 years. You want to know how they've been and what they've been doing since you last spoke. With Javascript, I feel a sense of familiarity, yet I know that I will need to make an effort in conveying the same coding practices I've learned in this programming language. As with every learning experience, treading by and allowing the current to drift you, won't get you anywhere in software engineering. You need to make an effort in going from a beginner, to a veteran, and to a master. To acclimate us to our new environment, we have been given small WODs(Workout of the day) as exercises to develop our minds to becoming better learners. This technique is administered approximately 4 times a week, as far as I can tell. It seems daunting, to have something due almost every day, as these WODs are not the only things assigned for the class, but everything that I have truly loved learning about has required me to truly live the material, and this technique funnels you into that experience. Our first WOD asked us to find the sum of all the multiples of 3 and 5 below 1000 using JSFiddle.   

```
function projectEulerOne(value){
  let solution = 0;
  for(i = 0; i < value; i ++){
  	if (((i % 3) ==0) || ((i % 5) == 0)) {
  	solution += i;
  }
  }
  return solution;
}
console.log(projectEulerOne(1000));

```

<hr>

## I Java(script) you!

Ranges of completion times are provided
```
function projectEulerTwo(value){
let preTerm = 1;
let curTerm = 2;
let nexTerm = 0;
let total = 0;

	while (curTerm < value){
  	if ((curTerm % 2) == 0){
    total += curTerm;
    }
    nexTerm = preTerm + curTerm;
    preTerm = curTerm;
    curTerm = nexTerm;
  }
  return total;
}
console.log(projectEulerTwo(4000000));
```

## The foolproof way to get ignored.

While there are decent questions that benefit everyone, there are those one can ask to create an entirely different effect. In the following example, a user asks how he would, in short, create a desktop application with Facebook.

```
Q: Facebook Desktop Notifier

I am a beginner programmer that have never used anything other than what's included in a language.

I am trying to create a desktop application that notifies me anytime I get an update onfacebook. 
How should go about doing this? Thanks in advance.

edit Sorry I was not clear. Is there any way to make a DESKTOP application with facebook?
```

A simple “yes” would have answered the question, but we know that’s not the sort of answer he or she is looking for. Fortunately, someone kindly responded with a link to Facebook’s developer website. The asker should have done more research on his or her potential project. Then further down the road, he or she could have asked more specific and detailed questions that wouldn’t require a thousand-paged response for a sufficient answer.

## Conclusion

When we rely on others’ generosity and expertise to provide answers to our questions, it should hold that the question we ask should be one that leads to efficient and effective help that not only benefits us, but also the people we ask and others who might ask the same question in the future. Thus, if you have a question… make it a smart one! Asking questions may not always get you the best answer, but asking them in a way that will make others want to answer them will increase the success of finding a good solution and make it a positive experience on all sides.
