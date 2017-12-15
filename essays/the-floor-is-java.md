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

<img class="ui small left floated image" src="../images/javascript.png">

# The Floor is Java(script)!

   I associate the learning of programming languages with learning how to run before you walk. The FreeCodeCamp Javascript tutorials are a fantastic tool to get you started and have prepared me with the vernacular of Javascript. I am not truly a beginner when it comes to coding, I have had some practice with Java for two semesters and C/C++ for another, but it is always nice to have a refresher of sorts. When studying programming languages, I try to think of them as foreign languages, where I wish to convey expressions and emotions rather than memorize specific words.

<hr>

## Swimming through Java(script)

   Although I have never touched Javascript before, I found it to be rather welcoming. Almost like a friend from down the street that you haven't seen in 10 years. You want to know how they've been and what they've been doing since you last spoke. With Javascript, I feel a sense of familiarity, yet I know that I will need to make an effort in conveying the same coding practices I've learned in this programming language. As with every learning experience, treading by and allowing the current to drift you, won't get you anywhere in software engineering. You need to make an effort in going from a beginner, to a veteran, and to a master. As such, I am a beginner, and at this time cannot make any judgements towards it being a great or terrible programming language. To acclimate us to our new environment, we have been given small WODs(Workout of the day) as exercises to develop our minds to becoming better learners. This technique is administered approximately 4 times a week, as far as I can tell. It seems daunting, to have something due almost every day, as these WODs are not the only things assigned for the class, but everything that I have truly loved learning about has required me to truly live the material, and this technique funnels you into that experience. Our first WOD asked us to find the sum of all the multiples of 3 and 5 below 1000 using JSFiddle.   

<hr>

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

   For each WOD, ranges of completion times are provided to test your efficiency as well. For the first WOD I shot for the average time of (4-6 min), as I had stitches sewn into my finger the night before from an unfortunate incident at work. I ended with 4:47.80 and called it quits. As for the next WOD, we drew on the wonderful Fibonacci and had to not only map his sequence, but to find the sum of all even-valued terms up to the given value. I chose not to settle for the average time range and mustered on until I completed it in 2:40.26 from scratch.  

<hr>

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

<hr>

   Time limits may seem stressful behind its connotation, but I truly love the drive it gives you as long as it doesn't consume you. As a cook, my experience tells me that rushing to make the fastest time possible often leads you into making mistakes. My goal is to always better myself into becoming a more efficient worker, and ultimately, a more efficient programmer. I love the time limitations because it forces me to gauge where I need to be at a certain time. I like to look at the clock, and instead of panic, really dial myself into what I am doing.
	
<hr>
	
## Conclusion

   In conclusion, I believe that the WODs and the "athletic software engineering" routine is beneficial in that I am always doing something relating to software engineering. Creating pockets of time everyday is a challenge when working and going to school full-time, but I feel as though I will learn more, as the topics are always in the back of my mind. As of my first week with Javascript, I would have to say that I enjoy the language because it seems short and sweet. I look forward to gathering more experience with it and say I can truly become proficient in its nomenclature. 

<hr>
