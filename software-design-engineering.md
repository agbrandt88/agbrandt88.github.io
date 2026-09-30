---
layout: default
title: Software Design & Engineering
---

# Software Design & Engineering

## Description

The artifact I chose for category one enhancement comes from previous coursework conducted in CS 360: Mobile Architecture and Programming.  Called Event Tracking App, this was one of the final project options we were given to pursue.  Event Tracking App is an Android application designed to allow users to create an account and track life events via an easy-to-use interface.  Created using Android Studio, with Java as the programming language, Event Tracking App leverages Room for local storage.  While fully functional, this project’s architectural setup and basic SMS implementation provides a large area for category one related improvements.

## Justification

I chose this project for improvement as it provides a great starting point for architectural/organizational enhancements.  Its initial form maintained a lot of app functionality on only a few class structures and did a poor job of organizing classes by specific capability.  To improve on this, I have applied a Model-View-ViewModel (MVVM) structure to Event Tracking App and broken up each function within those three categories.  Rather than each activity class maintaining multiple cross-application functions, they have been limited to UI view functionality.  Meanwhile, I have added three ViewModels for authentication/validation and event activity logic (loading, saving etc.).  While activities fall into View, ViewModels are the bridge between View and Model areas.  My intention by separating application functionality into MVVM categories has been to demonstrate skills in object-oriented design (OOD)/object-oriented programming (OOP).  Additional improvements have been made to remove direct database interaction from activity classes and create multiple threads supporting asynchronous work/responsiveness (Android Developers, n.d.).  Finally, I used category one as an opportunity to implement a functional worker class for SMS notifications as previously, while some of the WorkManager capability had been set up, notifications were not running in the background properly.

[Link to Software Design & Engineering Enhancement](https://github.com/agbrandt88/CS-499/tree/main/Category%20One%20-%20Software%20Design)

## Reflection

Category one enhancements strongly support outcomes four and five.  Demonstrating the ability to use innovative techniques, skills, and tools was accomplished through researching and implementing tried and true ways of making an application more architecturally sound.  MVVM architecture is a commonly employed technique that directly supports Event Tracking App’s readability and efficiency.  Not only does this improvement separate out areas of responsibility within the application, but also it allows for asynchronous work for a better user experience.  This is also true for applying the correct implementation of WorkManager with a worker class, a well-founded technique that allows Event Tracking App to perform one of its core functional requirements of sending the user notifications.  Security was improved moderately in accordance with course outcome five in that data validation was heavily implemented.  For both event and account information, error handling has been much more heavily enforced, and database access was moved away from activities that handle UI.

This enhancement process showed me how different it can be to improve already working software vice starting a project from the beginning.  It required careful effort to ensure any plan I implemented didn’t break another part of Event Tracking App.  Planning properly and following a precise implementation strategy is something I focused on during these enhancements vice previous coursework as I wanted the application to be able to run each step of the way.  This can be challenging as in some cases changing one class can break others, however incremental development allowed me to constantly test and troubleshoot.
	
Previous projects were often complete once we achieved a base level of functionality, however improving Event Tracking App allowed me to learn a lot more about the implementation of tools that support UI and application efficiency.  For example, the combination of asynchronous programming tools with LiveData observers makes it so certain Event Tacking App operations don’t interfere with one another.  This ensures things like database operations don’t hinder UI changes.  As application performance is more difficult to measure than whether it runs, ensuring that operations are separated appropriately and not causing bottlenecks is a challenge.

## Reference

Android Developers. (n.d.). Asynchronous work with Java threads. https://developer.android.com/develop/background-work/background-tasks/asynchronous/java-threads

[Previous Page](index.md)
