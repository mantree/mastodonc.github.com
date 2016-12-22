---
layout: post
title: Kixi Architectual Decisions
date: 2016-12-22 11:00
author: tcoupland
comments: true
categories: [kixi, design, architecture]
---
The Kixi platform is constructed around a design pattern known as Command Query Responsibility Separation (CQRS). This pattern is part of a hierarchy of designs that build upon one another and are generally used within a Micro-Services architecture.

At the bottom of this hierarchy is the idea that decoupling the parts of a system that create actions from those that act upon them is valuable. At this level, we don’t have Events, we just have Messages whose purpose is, intentionally, ill-defined. This idea can be termed Message Passing. The power gained from this decoupling comes from the message queues and the inversion of control achieved when the consumer can control the rate of message processing. The pattern can also help the system scale horizontally, as message consumer instances can be added easily.

We then ascend to the Event-Driven pattern. In essence, we are adding constraints to our Messages, describing them in more detail and making more use of them. Here we state that when any data is updated by a service it should create an Event describing what it has changed. This can be used for eventually consistent transactions, as services can communicate asynchronously about changes, eventually coming to a consensus on the state. The pattern can also make it easier to add certain types of features, notifications and audit logs are go to examples. When building new features you can use the events to drive or trigger their behaviour.

Event-Sourcing is the next stage, and it swaps around the relationship between action and event creation. Instead of updating state and then releasing an event, the event comes first. Now system elements create events that encapsulate the change they want to occur, and then consumers enact them. The events should contain deltas of the data, explicitly containing the changes to be made. Here we encounter the idea of Idempotence. It must be assumed that events can be processed multiple times and therefore the delta’s have to be carefully crafted to ensure that the data won’t become corrupted when that occurs.

Finally, we make our way up to Command Query Responsibility Separation (CQRS). Now we make a further change to our event constraints, by adding a new flavour of them called Commands. Commands encapsulate the verbs of the system, they are instructions for the system to perform an action. Every action within the system should be the result of a Command telling it to do so. A big part of Command processing is decided if it should be actioned or not. There can be many reasons for rejecting a Command, authentication, authorisation, invalid data, etc. The result of processing a Command must always be an event. This event captures the outcome of the Command. It can either explain why the Command was rejected or changes caused by the Command. Once the Event describing the changes has been released into the event stream, it is considered to have occurred, from the system’s point of view. This is why the event stream is considered the Source of Truth for the system, meaning that whatever it claims is true, is true, no matter what other stores within the system may claim.  The system as a whole is therefore Eventually Consistent.

These ideas and patterns grow in complexity as we add constraints and meaning upon our events. The application of these ideas is not simple and increases the complexity of working with the system, they also add to the operational burden. However, they do have some significant benefits:

* Scaling. Event and Command processing can be easily scaled, horizontally, by just adding more instances of a given event processor. This can even be performed dynamically in response to load. This ability can also be used to help with events that require significant processing time.
* Audit logging. This is practically a by-product of the architecture. It is always possible to trace the cause of a given action.
* Debugging. If a problem occurs it is possible to replay the system and investigate the exact cause of the issue.
* New query models. By having all data modifications in the events it is possible to create new models of the data to fulfil future feature requests. If a new data API needs to be supported, you can reingest all the data from the stream and store it in a bespoke format for that API.
* Completely decoupled processes. The system naturally breaks down into small components, each dealing with a given event or small group of events. These are completely decoupled from each other. They can be moved into micro-services easily.
* Late feature addition. As the system grows additional features, encapsulated as new event types or novel processing of current events, are simple to add. This can allow many teams to contribute the system needing little coordination.

The use of CQRS for the datastore and kixi can be thought of as a bet. We are betting that by laying the foundation of the system using this pattern we will get to take advantage of the benefits listed above, and those benefits will out weigh the cost over a time period we are happy with.
