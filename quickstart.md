
# Quick Start

After installation, let's start with the simplest case: ping/pong with the server.

The following 2 files build an example of how to create an OpenSwoole WebSocket server and interact with it:

File `server.php`:

```php
<?php

require __DIR__.'/vendor/autoload.php';

use OpenSwoole\Http\Request;
use OpenSwoole\Http\Response;
use OpenSwoole\WebSocket\Frame;
use OpenSwoole\WebSocket\Server;
use Conveyor\SocketHandlers\SocketMessageRouter as Conveyor;

$html = <<<HTML
<textarea id="msg"></textarea>
<button id="btn-base">Base</button>
<button id="btn-broadcast">Broadcast</button>
<ul id="output"></ul>

<script type="text/javascript">
    // page elements
    const msg = document.getElementById('msg')
    const btnBase = document.getElementById('btn-base')
    const btnBroadcast = document.getElementById('btn-broadcast')
    
    // listeners
    btnBase.addEventListener('click', () => base(msg.value))
    btnBroadcast.addEventListener('click', () => broadcast(msg.value))
    
    // ws/http server
    const ws = new WebSocket('ws://127.0.0.1:8001')
    ws.onopen = () => connectChannel()
    ws.onmessage = (e) => receive(e.data)
    
    // functions
    const connectChannel = () => ws.send(JSON.stringify({'action': 'channel-connect', 'channel': 'chat'}))
    const base = (val) => ws.send(val)
    const broadcast = (val) => ws.send(JSON.stringify({'action': 'broadcast-action', 'data': val}))
    const receive = (data) => {
        let li = document.createElement('li')
        li.innerText = data
        document.getElementById('output').append(li)
    }
</script>
HTML;

$websocket = new Server('0.0.0.0', 8001);
$websocket->on('message', fn (Server $s, Frame $f) => Conveyor::init()->run($f->data, $f->fd, $s));
$websocket->on('request', fn(Request $rq, Response $rp) => $rp->end($html));
$websocket->start();
```

With that file available, run:

```shell
php server.php
```

Access http://localhost:8001 on your browser (in more than one window to test broadcasting). That should work as follow:

<p align="center">
<img src="./imgs/test.gif" title="How it works"/>
</p>

Next: [Persistence](persistence.md)
