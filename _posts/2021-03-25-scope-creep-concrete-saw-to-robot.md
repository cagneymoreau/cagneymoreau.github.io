---
layout: post
title: "Scope Creep: From Automating a Concrete Saw to Building a Robot"
date: 2021-03-25
---

*Originally written in 2021 on my old blog, with a few ideas from a 2018 post on construction robots. Revised.*

Scope creep is when a project's goals keep expanding. Here's the most complete case of it I've ever lived through.

## It started with a concrete saw

In 2016 I was running a construction business, and one of my personal goals that year was to learn robotics. I had no education or experience in it. Some would argue I still don't.

The idea was practical. I was paying people $20 an hour for simple, repetitive work, like pushing a walk-behind concrete saw down a cut line. Surely a machine could do that.

## Then it grew

First I had to learn to code and learn how motors work, so I built a CNC machine from scratch as a warm-up.

When I was ready to tackle the saw, I realized a Segway-style balancing robot could push not just the saw but any walk-behind tool. It only made sense. So I built one. It was heavier than a Buick. It worked well enough, but it obviously needed arms.

Once I realized how hard arms would be, I figured I might as well give it legs too. So the plan became a general-purpose robot that could do basic tasks: pushing things, stacking things. I designed a strong, lightweight frame, the gearboxes, and the motor controller boards, then built an arm and a head to try some simple tasks.

## Then it grew again

How do you program something like that? Piping sensor data from the robot to my desktop and motor commands back out was the easy part. The hard part was that I'd have to explicitly program every situation the robot might ever encounter.

Machine learning to the rescue. All I had to do was write software that maps concepts into vector space, links CNN filters and state transitions to that space, pushes everything into a latent space, and uses bagging, binning and Gaussian process regression so the robot can learn and act on voice commands.

So I was pretty sure I was almost done.

## Why I still think about it

The ambition wasn't random. I'd spent years learning and teaching construction skills, and I kept noticing how much work on a job site breaks down into simple, repeatable pieces. The hard part isn't any one task. It's moving people and setup from one spot to the next, and having an expert step in the 5% of the time something unusual happens. A robot that could handle the routine 95%, with one person supervising many of them remotely, seemed close, and it still does.

What I wanted was cheap, modular hardware and software that's easy to repair and upgrade, broad enough to be useful in more than one trade, and with a person in the loop for the hard cases.

## Lesson learned

I should have just paid the guy the $20 an hour.

I don't regret it, though. That one saw turned into a CNC machine, a balancing robot, an arm, custom motor controllers, a video pipeline, and years of machine learning experiments. Almost everything I've built since traces back to it.
