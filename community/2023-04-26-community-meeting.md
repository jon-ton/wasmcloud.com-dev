---
title: 2023-04-26 Community Meeting
authors: [brooks]
tags: [community, meeting]
description: Agenda, notes, and recording for the 2023-04-26 community meeting
---

import ReactPlayer from 'react-player/youtube';

### Agenda

- (DEMO + DISCUSSION) Wadm, the declarative application format OAM, and where the `0.4.0` release stands
- (DISCUSSION) wasmCloud builtin numbergen capability, cryptography, generating random bytes
- KubeCon EU wrap-up, video recording links

<!--truncate-->

### Meeting Notes

- [Wadm](https://github.com/wasmcloud/wadm) 0.4 release: reworked and redesigned with Rust and NATS jetstream, now tidy and productionized.
  - Declaratively manage your wasmCloud apps across the lattice.
  - Wadm works alongside wasmCloud across a NATS connection - the same as your wasmCloud.
  - Host surveys the lattice for the entire state of hosts, actors and providers.
  - This means you can define your wasmCloud apps in terms of the [open application model (OAM)](https://oam.dev).
  - You can define your version (Wadm supports many) and define a list of components - actors or capability providers.
  - As part of components you can design a specific trait - for example the scale or amount of hosts you want to spread.
  - Also linkdefs come as standard with Wadm to stitch together wasmCloud actors to give configuration.
  - Pushing towards 0.4 release but, yes, you can use it today with the [wash support PR](https://github.com/wasmCloud/wash/pull/520).
  - Essentially, this is how folks work with K8s deployments - declaratively say how I want things to work.
- wasmCloud builtin numbergen capability, cryptography, generating random bytes.
  - Contributions from Stephen generating random bytes into the numbergen builtin.
  - wasmCloud host responsible for generating a random number but are they cryptographically suitable?
  - How we version the interface is still in discussion. The key question is the relationship between builtin numbergen interface application to cryptographically safe random bytes generation.
  - Kevin: interface is designed for 'best effort' functionality, host implementation not necessarily cryptographically random.
  - Same with random numbers - interface gives no guarantee that numbers are cryptographically random.
  - Is it the responsibility of the builtins to give you a cryptographically random number or should we have a separate provider/UI to expose data that is suitable for use in cryptography?
  - wasi-fill approach could be a route to explore. Write your code like you would normally do - when the component runs in wasmCloud we handle the distribution for you.
  - Decided to use careful language indicating random numbers are best effort, and that we don't make guarantees in the interface. Bailey agreed to create an [issue to explore adding wasi-crypto support](https://github.com/wasmCloud/wasmCloud/issues/315).
- KubeCon Retro
  - Recognition - 80% of the folks we talked to have heard of Wasm - progress! "Who hasn't?!" said one visitor to the booth.
  - The Wasm side of KubeCon was sold out early and packed to the rafters - shows how fast the server-side ecosystem is growing.
  - The Wasm Day recordings are up - check them out [here](https://cosmonic.com/blog/industry/cloud-native-wasm-day-2023-wrap-up).
  - Kevin's KubeCon talk still to appear - week or so.

### Recording

<ReactPlayer url='https://youtu.be/lONNmx0fXME' controls />
