
# Persistence

Socket Conveyor uses persistence for its functionalities. The persistences available are for:

- channels
- listeners
- user association

> **Important:** By default, Socket Conveyor uses `OpenSwoole\Table` for persistence, which means that during server restart it will be fresh. When using a different persistence strategy, you'll need to refresh the data during server bootstrap.
>
> For that, call the method `SockerMessageRouter::refresh($customPersistence)` once before the server starts. That will invoke the method "refresh" available at the Persistence's interfaces. You can also call those methods yourself.
>
> e.g.:
> ```php
> use Conveyor\SocketHandlers\SockerMessageRouter as Conveyor;
> Conveyor::refresh($customPersistence);
> // then, on message events, run it as usual...
> $websocket->on('message', fn (Server $s, Frame $f) => Conveyor::init()->run($f->data, $f->fd, $s));
> ```
>
> When you don't do this using a persistence that lasts for more than the server restart, it will cause some data conflicts due to old data remaining.

Next: [Usage](usage.md)
