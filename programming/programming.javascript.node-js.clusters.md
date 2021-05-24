---
id: d69aee32-573c-4b59-abcd-d6cfe3ded443
title: Clusters
desc: ""
updated: 1621707401948
created: 1621707325747
---

## PM2

- Process Manager
- Forever alive
- Monitorin
- Load Balancer
- Centralized Logs
- Not optimal compared with native approachs

### Installation

```bash
npm install -g pm2

```

### Usefull Comands

```bash
pm2 start index.js // Start the app, restart if needed.

pm2 ls  // show the current apps available
pm2 stop app // Stop app
pm2 delete app // Remove the app

pm2 monit // Show the process list, global logs, and more
pm2 log // centralized logs
pm2 start index.js -i max // Create a cluster with all CPUS

```

More: https://devhints.io/pm2

## Cluster Module

Node.js allows to create child processes to use multiple CPU cores and handle multiple tasks in parallel.
It uses by the default the round-robin distribution to distribute connections across the workers.

Example: [Setting up a Node.js Cluster
](https://stackabuse.com/setting-up-a-node-js-cluster/)

master.js

```javacript
const cluster = require('cluster');
const os = require('os')

if (cluster.isMaster) {
 console.log(`Master running on pid: ${process.pid}`)

 for (let i = 0; i < os.cpus().length; i++) {
   cluster.fork();
 }

 cluster.on('exit', (worker, code, signal) => {
   if (code != 0 && !worker.exitedAfterDisconnect) {
     	console.log(`Worker ${worker.id}
crashed, starting a new one`);
     cluster.fork();
   }
 })
} else {
 require('./child')
}
```

child.js

```javacript
const http = require('http');

const server = http.createServer((req, res) => {
 if ( req.url === '/') {
   // blocking
   for (let i = 0; i < 100000000; i++) { }
   setTimeout(() => {
     res.end('okay');
   }, 0)
 } else {
   res.end()
 }
});

server.listen(8080, () => {
 console.log(`Child Server running on pid: ${process.pid}`)
});

setTimeout(() => {
 process.exit(1) // death by random timeout
}, Math.random() * 20000);
```

## Aditional Information

- https://nodejs.org/api/cluster.html
- https://github.com/mcollina/autocannon
- https://flaviocopes.com/node-request-data/
- https://medium.com/tech-tajawal/clustering-in-nodejs-utilizing-multiple-processor-cores-75d78aeb0f4f
- https://medium.com/the-andela-way/scaling-out-with-node-clusters-1dca4a39a2a
- https://medium.freecodecamp.org/node-js-child-processes-everything-you-need-to-know-e69498fe970a
- http://www.acuriousanimal.com/2017/08/12/understanding-the-nodejs-cluster-module.html
