+++
title = "Domain Modeling"
date = "2023-05-02T15:00:08+06:00"
author = "fl4ssh"
authorTwitter = "" #do not include @
cover = ""
tags = ["", ""]
keywords = ["", ""]
description = "This post is based on a recap of Cosmic Python book"
showFullContent = false
readingTime = false
hideComments = false
draft = true
+++

# Domain modeling

Domain model is another term to describe business logic layer. It is a central layer of a three-layered architecture (Presentation -> Business -> Database). It is the part of the code that is likely to change and delivers the most value to the business. It is important to make it understandable and easy to modify.

The *domain* is a fancy way of saying the problem you're trying to solve.
A *model* is a map of a process or phenomenon that captures a useful property.
Steps to develop domain model:
 - initial conversation with business experts
 - agree on glossary
 - set some rules for the first minimal version of the domain model
 - wherever possible, concrete examples should be given for a rule

To model a domain, two concepts can be used: 
 - value object
 - entity. 

Value objects are used to represent concepts or values within the domain, while entities are used to represent objects with unique identities that are relevant to the domain. By using these constructs effectively, we can create models that accurately reflect the business rules and concepts of the domain. 

Example of a value object is `EmailAddress`. It's immutable and its identity is represented by its state. Example of an entity is `User` which can have attributes (or value objects) such as name, email address, password, etc. Its state may change over time, but its identity remains the same (e.g. ID).
