---
layout: essay
type: essay
title: "Adventures with Typescript"
# All dates must be YYYY-MM-DD format!
date: 2024-09-04
published: true
labels:
  - Software Engineering
  - Learning
  - JavaScript
  - TypeScript
  - Athletic Software Engineering
  - Skill Development
---

<img width="500px" class="rounded mx-auto d-block" src="../img/typescript/FreeCodeCamp.png">

## Introduction to JavaScript

Before taking the FreeCodeCamp course to learn JavaScript and TypeScript, I knew little about how the JavaScript and TypeScript languages functioned. My prior experience in programming languages consisted of Java and Python. I learned Java in the introductory Computer Science courses at Arizona State University and the University of Hawai'i at Mānoa. Due to my experience with Java, learning JavaScript was not that hard. The FreeCodeCamp course taught me the necessary diction and syntax changes that I needed to make to adapt to writing code in JavaScript. The experience of learning JavaScript was not too difficult considering how similar the language is to Java. The introductory course in JavaScript helped to prepare me for my next challenge: learning TypeScript.

<img width="500px" class="rounded mx-auto d-block" src="../img/typescript/Typescript.png">

## Learning TypeScript

After learning JavaScript, TypeScript was fairly easy to learn. TypeScript seemed like a more precise version of JavaScript. It makes more use of the ability to declare static types to variables and functions. This allows for the code to be easier to understand by displaying the intended function of each variable and function. I enjoyed learning TypeScript and believe that it will be very useful for a future career in software engineering due to the versatility of the language since it can be compiled to run on any browser, device, and operating system. I also believe that TypeScript will be useful in future development projects due to the ability to point out compilation errors at the time of development. This feature is useful because it helps when writing code and makes getting a runtime error less likely. Being able to understand and write code in TypeScript will enhance my skills for many different types of software engineering projects. I'm excited to be able to put my newfound skill to the test and start new projects that can further my understanding of TypeScript and software development as a whole.

## Athletic Software Engineering

Putting my skills to the test using Athletic Software Engineering and the Workouts of the Day (WODs) has caused me a lot of stress. Athletic Software Engineering tests my ability to solve problems by creating functions within an alloted timeframe. The idea of this type of practice was very offputting at first. I didn't believe that I had enough experience to be able to solve problems and write functions in a short period. I couldn't have been more wrong. Timing myself and my ability to create a function to solve a specific problem has helped me to understand where I struggle to be efficient. I struggled with being able to recognize what algorithms could be used to solve a problem. I also learned that I am capable of writing and structuring code properly with minimal errors once I knew what algorithms were needed to solve the problem. Due to the timed aspect of the WODs, I have been able to focus my ability to write functions that are efficient and can solve the problem accurately. I also started to practice my ability to recognize problems and understand how to solve them. I believe that Athletic Software Engineering is a very efficient style of learning and I will be able to enhance my problem-solving and critical thinking skills along with my ability to write code.

## Example WOD

This is a practice WOD from the beginning of my ICS 314 course that finds the sum of all numbers below 1000 that are divisible by 3 or 5. Using Athletic Software Engineering, I was able to solve the problem within one minute.

```

function eulerHelper(num: number) {
    let sum: number = 0;
    for (let i = 0; i < num; i++) {
        if (i % 3 === 0 && i % 5 === 0) {
            sum += i;
        } else if (i % 3 === 0) {
            sum += i;
        } else if (i % 5 === 0) {
            sum += i;
        }
    }

    return sum;
}

console.log(eulerHelper(1000));

function projectEulerOne() {
    return eulerHelper(1000);
}

```
