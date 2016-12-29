# linux_midi_commands

Command line midi tools for Linux

This is based on an initial program for a midi clock and sync
command line tool by Pedro Lopez-Cabanillas (see http://lists.linuxaudio.org/pipermail/linux-audio-user/2009-August/061724.html)

The first step (which I'm still at) is to use the program by Pedro to
investigate the workings of ALSA midi.

## How to Compile

    gcc -o ametro -lasound ametro.c

