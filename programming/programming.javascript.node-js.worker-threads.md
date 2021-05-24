---
id: 78e1ced2-067d-4250-baba-4c35e5ae0d50
title: Worker Threads
desc: ""
updated: 1621708807912
created: 1621708792442
---

## Why?

Intesive cpu work, like compression.

## What should I use: Child_process, worker Threads

Explained : https://blog.logrocket.com/node-js-multithreading-what-are-worker-threads-and-why-do-they-matter-48ab102f8b10

Worker threads: https://nodejs.org/api/worker_threads.html
Child Process: https://nodejs.org/api/child_process.html#child_process_child_process_fork_modulepath_args_options

## Code

```javascript
const {
  Worker,
  isMainThread,
  parentPort,
  workerData,
} = require("worker_threads");

let w = new Worker(path, { workerData: null });
w.on("message", (msg) => console.log(msg));
w.on("error", (msg) => console.log(msg));
w.on("exit", (msg) => console.log(msg));
```

Child on `path`

```javascript
const { parentPort } = require("worker_threads");

// do something

parentPort.postMessage("notify parent");
```

## Thread pool

Is nice to have a thread poll, this library manage it for you
https://github.com/watson/worker-threads-pool

General
https://gobyexample.com/worker-pools

## Concurrent work

https://medium.com/@piotrkarpaa/async-await-and-parallel-code-in-node-js-6de6501eea48\
https://medium.com/platformer-blog/node-js-concurrency-with-async-await-and-promises-b4c4ae8f4510

## child Process

https://medium.com/the-guild/getting-to-know-nodes-child-process-module-8ed63038f3fa

https://medium.freecodecamp.org/node-js-child-processes-everything-you-need-to-know-e69498fe970a

## Aditional Information

https://medium.com/dailyjs/threads-in-node-10-5-0-a-practical-intro-3b85a0a3c953
https://medium.com/lazy-engineering/node-worker-threads-b57a32d84845
https://nodejs.org/en/docs/guides/dont-block-the-event-loop/
