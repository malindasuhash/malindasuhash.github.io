---
layout: post
title:  "Domain Modeling and Service Independence"
date:   2020-02-12 23:27:00 +00:00
categories: Design
---

I attended an architectural community meetup recently and one of the points discussed was around naming consistency between problem domains. The example that was presented was an Order should have the same meaning across the business. This was too abstract so it got me thinking. 

## Divide and conquer  

The domain partition is a way of simplifying the problem space so that it can be reasoned and discussed. It allows designers to think within their area of expertise and develop solutions to enable business initiatives.  

Nowadays a typical enterprise consists of bespoke, off-the-self and cloud hosted application. So, it’s hard and closer to impossible to assume any naming consistency across these applications. What you can do instead is to embrace this difference and introduce a layer of abstraction.   

## Canonical data model 

This is a term that Enterprise data architecture use quite often to highlight the need for a common data format to describe an entity.  

As far as I understand, the principle is for dependent systems accept the canonical data model as an argument. Thereafter each application processes the incoming data by mapping it to a private type.  

At a high level, this sounds a great idea. But can you actually get the whole enterprise to agree on a single data model? Enter Ant-corruption layer. 

## Anti-corruption layer 

The Anti-corruption layer is a well-known “adapter” style pattern that allow two systems with different semantics to communicate. So, considering the *Order* example, in System A; an Order it may called *Transaction* whereas in System B an Order maybe known as a *Collection*.  


The Anti-corruption layer pattern is a quite a versatile and it can be adapted as an architectural or development design pattern. 

![anti-c](/assets/Simple-anti-c.png)

Few examples use cases are: 

> Bridging the gap between a legacy protocol and a modern protocol (e.g., SOAP --> JSON) 

> Migration from legacy system to a new system (e.g., Continuing to support legacy interface) 

> Data integration (e.g., mapping between different schemas) 

## Cost 

There are obviously some costs involved with maintaining an anti-corruption layer (e.g., yet another failure point in the architecture). 

The most obvious costs are maintenance and performance. The owner is expected to understand both legacy and the new system in order to best use of this pattern. Depending on the scenario this may not be the *best use of time*. Nevertheless, the alternative is a big-bang approach, which carry significant risks.  

## Summary 

The presenter in community standup was attempting to hint towards a canonical data model. I am not in favor of centralising and mandating which properties/data should be defined within an aggregate. If there is a desire to maintain a canonical data model, then the dependency can to be inverted so that the consumer access the service via an abstraction. I think the anti-corruption layer is the way to achieve best of both worlds! 