## The current state and future state of Contract Testing at Discover

TL;DR - It is not consumer driven contract testing unless the providers are driven by it.

[Insert an an image of a mobile phone case]

We all use or have used mobile phone cases to protect our shiny devices of glass and metal. Have you ever wondered how they are available usually before the device even hits the market? Casemakers are given dummy devices with exact dimensions but no internals either in physical or digital form by the manufacturer of the mobile phone way in advance of the device even being announced. The point is that the dummy device is a contract that the consumer of the case, the mobile phone will be compatible with the case as long as they adhere to the dimesnsions of the mobile phone. This prevents both the mobile phone manufacturer and the case manufacturer from crossing certain boundaries as they continue to develop their products. 

Now imagine a world where the mobile phone manufacturer has to ensure case comaptibilty by ordering all the advertised mobile phone cases and maintain a list of cases that actually fit their phone. The case manufacturers in this world are only informed of an incompatibilty after the case hits the inital development phase and a physical case is 3D-printed and given to the mobile device maker. Case manufactureers then go back and make changes to the case dimensions if it does not fit. Clearly there is a better way to do this and it has already been figured out and put in place.

This document hopes to cover the current state and target state of contract testing at Discover. Although a handful of teams are performing contract testing currently, it is still not being done the way it is intended. This is however not due to lack of knowledge on how to do it right, it is only because of lack of collaboration and buy in from either the provider or consumer of the API (usually the provider).

Let us first take a look at how the pipeline team is handling contract testing.

[Insert diagram here]

The pipeline team have a script called the PACT automation script that generates both consumer and provider tests. Developers still have to write provider states and run the consumer tests to generate the contract files.

Key points to take away from this process

1) The consumer is writing both the consumer and provider tests

2) The conusmer is always testing against the current provider version deployed in a specific ENV

3) The contract is not shared with the provider. There is no one honoring the generated contract.

4) The only way the providers know if a future version will break all or some of their consumers is only if the developer/s on their team are aware of the consequences of changing the schema.

5) Broken/non-existent feedback loop - The primary intent behind contract testing is to enable developers on both sides to immediately know if a breaking change has just been commited to a code repository. Currently changes are communicated over IM or if someone remembers it during story grooming.

Unlike the mobile phone industry we have a plethora of ways to make sure API consumers and providers are in sync through use of certain tools and practices. This involves the use of tools like the Pact Broker, CICD pipelines, versioning and branching strategies. The difficult part is to get everyone to do it, becuase no city is beautiful unless everyone mowes their own lawn.


No matter how updated the consumers are here, they are always testing against a moving target, the current version of the provider deployed in their environment of choice. There is no guarantee that a future version of a provider will break their API.

