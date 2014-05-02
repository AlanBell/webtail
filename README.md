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

If you are having problems with a lack of output it might be buffering, try just running it without piping data in, you can then just type into it and press ctrl+d to send an end of file signal. If that works fine then the pipe is buffering things, you can install the unbuffer command from the expect-dev package, then put unbuffer in front of the thing that prints the output, for example:

    $ sudo apt-get install expect-dev
    $ while true; do unbuffer date; sleep 1; done|./webtail
