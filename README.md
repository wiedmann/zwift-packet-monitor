# zwift-packet-monitor

This module monitors Zwift UDP traffic and emits events for the player state updates.

## Install
On Windows this requires WinPcap. On other systems, libpcap should be installed.

```
npm install zwift-packet-monitor
```

## Usage

```javascript
const ZwiftPacketMonitor = require('zwift-packet-monitor')

// interface is cap interface name (can be device name or IP address)
const monitor = new ZwiftPacketMonitor(interface)

monitor.on('outgoingPlayerState', (playerState, serverWorldTime) => {
  console.log(playerState)
})

monitor.on('incomingPlayerState', (playerState, serverWorldTime) => {
  console.log(playerState)
})

// The Zwift server sends states in batches. This event is emitted at the end of each incoming batch
monitor.on('endOfBatch', () => {
  console.log('end of batch')
})
```

