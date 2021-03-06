# Commenting System Domain Model

## Introduction
Commenting on the Internet has become one of the biggest drivers for user engagement on any website. Any website that wants to increase the time users spend on their website uses a comments system.Comments systems are so important that specialized companies have been formed around them to provide comments as a service. The major ones on the market are DISQUS, MUUT, JETPACK and INTENSEDEBATE.

None of the major comments systems have  reputation features that I want.

## Class Diagram of the Domain Model

Below is the domain Domain of the new comment system that I want to develop.

![Domain Model](/model.png)

## Description of the Domain Model and its Invariants

According to the Domain Model, each Site instance will be managed by Site Managers, with their Contact details and could play the Role of either Administrator or Moderator. The Administrator's job, in addition to moderating comments, is to add and remove the site from the Comment System.

The Job of the Moderator is to only moderate Comments  and Responses that have been flagged as Spam or have Internet links.

Each Comment belongs to a story from a particular site and allows a User to post a Response. Both the Comment and the Response have the feature to allow people to  Vote Up or Down. The Value of a Vote is just an integer that is either incremented or decremented as long as the value of the counter is more than Zero. Additionally, both the comment and Response have the Filter Flag to mark the status of the comment as either APPROVED OR MODERATE.

All comments and responses suspected to be SPAM or have links in them will be marked as MODERATE until the moderator either deletes them or changes their status to APPROVED. Only APPROVED items are visible on the site. Inappropriate comments can also be reported by any user using the Abuse Report feature.

A User who wants to post a Comment MUST supply their email address to post a comment or response. The sum of all the votes both UP and Down on the comments made by the user are used to compute the Reputation of a user per day at midnight.

Voting is tracked by the Voter Register to prevent a user from voting twice by keeping track of their IP address on a subject item (Comment or Response) they have voted on. If a voter casts his Up vote, the system needs to check whether the voter voted before. If they didn't, the vote is incremented.

If they did vote, their previous vote is decremented. The User should not cast both the UP and the DOWN vote on one subject.
If they had an UP vote, and cast a DOWN vote, their UP vote should be decremented. The reverse should be true.


