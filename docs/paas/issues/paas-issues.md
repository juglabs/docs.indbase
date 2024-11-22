# Issues to keep track

## Problems with Cloud Service Providers - AWS, GCP etc

- Stripe in its initial days was engaging 20% of their engineering team on managing AWS infrastructure. Its about the same in other companies also
- Stripe back in 2016 was still not using Kubernetes
- AWS is like, look we give you these legos, you build whatever you want!
- But the QUESTION is, once these applications on PaaS scale, it begins HARD TO DEBUG. So how do you deal with that?
    - Your platform should expose right kind of primitives, but it doesn't have to expose all fo them at the same time, and all of them in the same way.
    - Platform should have PRIVATE NETWORKING built in, SERVICE DISCOVERY built in
        - Every application on the platform gets both a public address and private address - databases, managed data stores etc
        - Network Isolation as a feature, isolate development/staging/production environments from each other from a network standpoint of view with a single click
    - Ultimately it really comes down to being INCREDIBLY CLOSE to your customers who are scaling on the platform - AWS-NETFLIX analogy

## User Experience

- Lot of IN-PRODUCT GUIDANCE
- Information architecture work
- Lot of design, UI/UX
- Lot of sensible defaults
- Customer feedback
- Good logs, Good Documents, Good Error Messageas are key

## Managing Kubernetes

- Kubernetes does a good job with container orchestration
- Problem with K8 - surface area of K8 is massive - even to do a simple thing you have to understand 10 different concepts
- Give people the flexibility of Kubernetes without having to understand things

## Things to take care - Security

- As your product becomes popular, DDoS attacks become common - and not just at the HTTP layer, but at L4 as well, at the TCP layer
- So if you are dealing with bare metal, then you have to work about L3,L4, application level attacks
- So RENDER didn't do bare metal, they use AWS, GCP, CloudFlare because they've dealt with these problems before
