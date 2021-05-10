---
title: "Get Started."
slug: getting-started
---

Congratulations! You just got hired at a new firm. Your first assignment on the job is to create the initial version of an app that rates movies. As the firm grows, more iOS developers will join the team, so you've been asked to make the project easy to understand and scalable.

**Your mission:**

Use what you’ve learned so far about iOS networking to create a networking layer that will make the code scalable while adhering to MVC


# Why is this important?

If you ever want the app you're building to interact with APIs, or be able to communicate with them, then you need to know how to build a network layer, as well as how to make your code scalable and easy to understand. This is common functionality that iOS engineers should expect to do in their careers, so learning the fundamentals around it now will make you that much more prepared for that upcoming gig.

This project is also a great opportunity for you to practice working on an existing codebase and utilizing new libraries. 

# Learning Outcomes

By the end of this tutorial, you should know...

1. How to work with APIs.
1. How to build a network layer in Swift.
1. How to decode JSON into Swift models.
1. How to handle error and response.
1. How to display data in custom UI.
1. How to implement POST requests to authenticate the user using the third party authentication flow that TMDB's API has available.
1. How to use Apple's AuthenticationServices API to handle URL schemes.

# Technical Planning

Here's what we need to do to get this project up and running:

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. Work with Swift API Client
1. Handle network errors
1. Create HTTP methods and routes
1. Configure the request
1. Implement Encoder
1. Handle the response
1. Make the call
1. Display the data 
1. Additional Starter Challenge
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches

# What We're Building

![Preview final product](assets/00_final_product.png)

## User Stories

**As a user...**

- I can browse movies trending today on TMDb by scrolling through the app’s main screen.
- I see each movie's cover photo, title, and release data.

# Implementation Plan

We're going to building this app outside in; starting with the UI of the app and ending with the networking layer that communicated with the TMDb API.

This makes it quick and easy to build out the app and test some of its features before making requests to the API.

# Using Git/GitHub

As you go through this tutorial, you will also be making commits after completing milestones. **This is a requirement, you must make a commit whenever the tutorial prompts you**. This not only further enforces best practices for software engineering, but also will help you more easily figure out where a bug originated from if you break your progress up into discrete, trackable chunks.

When prompted to commit, you'll see a sample commit message. Feel free to use your own message, so long as it clearly and concisely covers the work done.

Lastly, the commit prompts in this tutorial should be the **minimum** amount of times you commit. If you want to do more commits, breaking your chunks into even smaller chunks, that is totally fine!
