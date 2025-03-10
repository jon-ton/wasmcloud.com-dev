---
title: 2023-03-01 Community Meeting
authors: [brooks]
tags: [community, meeting]
description: Agenda, notes, and recording for the 2023-03-01 community meeting
---

import ReactPlayer from 'react-player/youtube';

### Agenda
- (DEMO) cargo nextest and `wash` integration tests
- (DEMO) washboard error handling
- wadm RFC - Addressing comments and requesting more feedback

<!--truncate-->

### Meeting Notes
- Welcome to two new community members, Chuck Fair and Frank Schaffa!
- cargo nextest is a tool for quicker, more reproducible tests
  - could add some friction in terms of new contributors to install that test runner
  - we've noticed a ton of flakes in PRs that depend on network/IO lately in wash
  - nextest does not run serial tests in the way we do with cargo test, which is a small difference. Instead, we can just add serial tests to a test-group with nextest
  - Roman: Consider constraining nextest to CI, and fix the tests that are flaky, so that we can both take advantage of a better test runner and keep our tests well architected
  - Frank: How common is nextest in other communities / projects?
    - Matt: Well supported and fairly popular, but not present in the most popular projects as far as I know
  - Keep going forward keeping in mind adding another tool is a small barrier and we should make adding the nextest tool as simple as possible
- washboard error handling
  - Brooks showed a short and sweet demo of a recent PR to the wasmCloud host: [https://github.com/wasmCloud/wasmcloud-otp/pull/553](https://github.com/wasmCloud/wasmcloud-otp/pull/553) by vados-cosmonic
  - Essentially there are a few places in the wasmCloud dashboard that have placeholders for error messages but we opt to put them in the console instead. As we move forward with a better UX for the dashboard, we'll be looking for opportunities to surface these errors in the UI
- wadm RFC
  - After some great discussion on distributed systems in the wadm RFC: [https://github.com/wasmCloud/wadm/issues/40](https://github.com/wasmCloud/wadm/issues/40), we sought to leave room for a little more discussion
  - By the next community call we plan to solicit feedback, comments, and questions, before turning this RFC into a set of tasks in a project
  - General discussion followed, see the recording to catch up

### Recording

<ReactPlayer url='https://www.youtube.com/watch?v=gksQ46h3Khg' controls />
