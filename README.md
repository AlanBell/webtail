WebTail
=======

This tool works in a unixy way, doing one thing fairly well and being chainable to other tools. It basically listens on the standard input for stuff being piped into it, maybe tail -f /var/log/syslog or something more interesting. Any command line application that produces output on stdout can be piped into it. WebTail opens a websocket port and accepts client connections, anything it gets on the standard input it squirts out to all the clients.

You can watch your logs

    tail -f /var/log/syslog | ./webtail

You can watch the clock

    while true ;  do date  ; sleep 1 ; done|./webtail

To connect to it you will need a little bit of javascript on a web page, example file also provided.

See it in action at http://givehugs.net/


Outline socket server structure was from https://gist.github.com/jkp/3136208
