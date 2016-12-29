# linux_midi_commands

Command line midi tools for Linux

This is based on an initial program for a midi clock and sync
command line tool by Pedro Lopez-Cabanillas (see http://lists.linuxaudio.org/pipermail/linux-audio-user/2009-August/061724.html)

The first step (which I'm still at) is to use the program by Pedro to
investigate the workings of ALSA midi.

## How to Compile

    gcc -o ametro -lasound ametro.c


## Setting up midi ports

To view what midi ports are available use the command

    sudo aconnect -l


Which gives a response like this:

    client 0: 'System' [type=kernel]
        0 'Timer           '
        1 'Announce        '
    client 14: 'Midi Through' [type=kernel]
        0 'Midi Through Port-0'
	    Connecting To: 24:0
    client 20: 'Bass Station II' [type=kernel]
        0 'Bass Station II MIDI 1'
    client 24: 'UX16' [type=kernel]
        0 'UX16 MIDI 1     '
	    Connected From: 14:0

You can then connect the ports together using a command like this:

    sudo aconnect 14:0 20:0

In this command the midi through port is connected to the Bass Station II port.
The UX16 port is already connected to the midi through port in the same way.
Therefore, all midi sent to the midi through port will be sent to both the
Bass Station II and the UX16.

## How to Run

A simple example of how to run:

    ./ametro  -M -t 50 -o 14:0

-M
: Set this program as the master clock
-t 50
: Set the tempo to 50 beats per minute
-o 14:0
: Set the output midi port to 14:0 (the midi through port and hence the BSII and UX16)

For a full list of command line arguments use:

    ./ametro -h


