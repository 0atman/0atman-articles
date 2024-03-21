---
{}
---

Title: An open letter to moonpig.com
Date: 2015-01-05 10:20
Category: privacy

It was with much distress that I read this article about your insecure API: http://ifc0nfig.com/moonpig-vulnerability/

The author, Paul Price, showed that you do not use any authentication. I have tested this myself (I am a software engineer, and it was TRIVIAL) and can confirm the flagrant disregard for my privacy in your service.

According to him, you have had at least SEVENTEEN MONTHS to fix this, and not done so. That is unacceptable!

However, happily for you, the solution is simple: As Paul says in his article, you do have OAuth enabled already. Please start using it across all clients and disable the old insecure API at /rest.

Now that this information is public, you have very little time before your customer’s details are leaked online if it has not already. It will be very clear that the blame will not be in the crackers who took the data, but you, who not only left the door unlocked, but decided not to build the house in the first place.
