---
layout: default
title: Databases
---

# Databases

## Description

For this artifact I am continuing to improve upon the Event Tracking App previously developed during CS 360: Mobile Architecture & Programming.  When discussing application features related to the database category, Event Tracking App features use of Room as its primary means of storage.  Whether a user creates an account or populates new event cards into their home screen display, CRUD capability is supported by Room.  Its initial setup in the original artifact consists of a class for the database, two entities for user and event information, and data access objects (DAOs) which contain CRUD functionality.  While the database works in the original artifact, there are many areas that can be improved for better information storage, security, and query capability.

## Justification

The purpose of the applied category three enhancements was to keep Room in place, as I like its persistent storage features, while updating security and overall architecture.  Upon initial artifact review, one major weakness that stood out was the way passwords were being stored/maintained by the database.  Originally, all passwords were stored as plaintext, making them vulnerable to leaks should database integrity be compromised.  Post enhancement, all user input passwords are salted and hashed.  Salting a password means adding random characters to it, at which point password hashing occurs and converts it into a completely different set of characters (Owolabi, 2024).  Now in Event Tracking App, a user enters their password, SecureRandom creates the salt, and PBKDF2 uses the password plus salt to return a secure password hash.

Other database improvements relate to data integrity storage improvements.  In Event Table, for example, I added a foreign key to tie each event to the user generating it.  Additionally, as to prevent orphaned records, this foreign key maintains a cascade deletion rule, meaning that if a user account is deleted so are all events associated with it.  Unique usernames are also now being enforced at the database level rather than just via application logic through an added index setup, and dates/times are now stored as epoch milliseconds vice strings for even more consistent data formatting.

[Link to Databases Enhancement](https://github.com/agbrandt88/CS-499/tree/main/Category%20Three%20-%20Databases)

## Reflection

Course outcomes four and five were heavily executed during the implementation of category three application enhancements.  Outcome four was demonstrated by the fact that updates to database setup were architecturally improved upon vice being completely replaced.  Room worked as a persistent database, but it was not fully optimized in accordance with well-founded and innovative techniques.  By adding foreign keys to the Event Table entity, I used a common computing tool for ensuring data integrity is preserved and issues like orphaned data do not occur.  Additionally, using proper indexing techniques for unique data storage and long values vice strings for dates/times creates a much more efficient database environment while demonstrating adherence to good coding standards and practices.

This update displays a high level of security minded project improvements through its complete overhaul of the user validation process.  Storing passwords as plaintext represented a clear security vulnerability, however in accordance with course outcome five, this process has been replaced in favor of one that relies on two separate secure techniques for increased data protection.  In line with course outcome four, password salting/hashing is based on well-founded coding techniques and performs multiple operations to ensure that a user provided password remains a hard target, even if someone gains access to Event Tracking App’s database.  Additionally, because this is a one-way process, user passwords are protected even from website administrators (Owolabi, 2024).

Category three taught me a lot about the overall application enhancement process.  Since I used the same project for all three update areas, each additional enhancement required some change be made to the previous ones.  For example, whereas initially I was using string values for date/time, in this enhancement they were converted into numeric values.  This meant going back and making changes in a lot of areas, to include the algorithms implemented during category two.  Simple changes like this also affected multiple areas in general due to the MVVM architecture implemented during category one enhancements.  Any area dealing with UI needed readable values, which needed to be converted by the ViewModel before database storage.  Then, when attempting to convert back into a readable format, numeric dates/times had to be passed back to Event Adapter.

Another lesson I continue to learn is that just because something works doesn’t mean it can’t be improved.  Event Tracking App started with a database built to be functional rather than secure.  Storing passwords as a string works and makes account use easy to setup/maintain, however this methodology completely ignores good security practice in favor of simplicity.  Each new implementation reinforces the fact that making an app functional is only step one, after which efforts must be made to build in security and efficiency/performance.  Applying only password hashing would have modestly improved security, however salting, while much more complicated to learn, makes each password unique.

Finally, I learned that creating redundancy between the application and database is good practice when creating something with defensive programming in mind.  For example, while denial of duplicate usernames was previously enforced through validation techniques conducted when creating an account, they are now also enforced via an added index in User Table.  Also, at the application level orphaned records are prevented by tying any generated event to the user who generated it.  Now, for redundancy, this relationship is enforced via the addition of a foreign key tying users to events, along with cascade for deletion.  This means that the application and database are both enforcing user/event relationships and preventing orphaned data from occurring.

## References

Millington, S. (2025, August 20). Hashing a password in Java. Baeldung. https://www.baeldung.com/java-password-hashing

Owolabi, R. (2024, October 25). Understanding password hashing and salt: a comprehensive guide for new engineers. Medium. https://medium.com/@rohteemie/understanding-password-hashing-and-salt-e52738ddb3dc

[Previous Page](index.md)
