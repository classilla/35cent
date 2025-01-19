# John Iannetta's 35-Cent Modem, Revisited

[Another Old VCR Vision of Excellence!](https://oldvcr.blogspot.com/2025/01/the-35-cent-commodore-64-softmodem.html)

This program is public domain.  
Based on original works by John Iannetta.

## What it is

This is an updated version of John Iannetta's "35-cent modem," a 1998 post to Usenet that uses the Commodore 64 as a one-way 300 baud software modem. With a cable that connects a telephone pair from a RJ-11C or similar to an RCA jack (which, at the time of John's post, cost approximately 35 cents in the Jameco catalogue), his original program could send data to a connected modem set to "originate." The updated version here merges the PAL and NTSC versions, adds a better menu interface and an ASCII upload mode, supports true-ASCII, and provides an artificial North American Precise Tone Plan-compatible dialtone for those modems that require it.

To construct the cable, wire the centre (first pair) lines of an RJ-11C or compatible 6-conductor modular cable to an RCA phono jack. Ring should be wired to the phono jack's ground and tip to its centre ([wire colours may vary](https://en.wikipedia.org/wiki/Registered_jack#RJ11)). Connect the phono jack to the Commodore 64's audio output and the phone jack to the modem of the other computer. **Never connect this cable to a wall jack. You could send 48V through your machine.**

The softmodem program `LOAD`s and `RUN`s like a BASIC program. Set the connected computer's modem and/or terminal program to originate, 300 baud, 8-N-1 (8 bits, no parity, one stop bit). When the program starts, it will detect the video mode of your C64 and set its timings appropriately (or you can force NTSC or PAL, if the detection is incorrect). Select the dialtone option if the connected modem requires a dialtone to be able to initiate a call. When ready, select the answer tone. If the connected system uses a Hayes compatible modem, a command line `ATX1D` will blind dial the link and establish a connection; older manual-dial modems may come on line immediately.

Once the connection is established, you may enter a mini-terminal (press F1 to exit), or send files either directly as ASCII with no protocol, or as Xmodem-CRC. If the transfer has a problem, it will need to start over: as the link is one-way, there is no means for the C64 to detect that an error has occurred.

"Hanging up" will cause the answer tone to be turned off, which most connected modems will perceive as a loss of carrier.

The communication is done with Bell 103 modulation. Look at the file `post.txt` for John's original post from 1998, including BASIC source code and a brief description. [Here's a disassembly of the original code and how it works.](hhttps://oldvcr.blogspot.com/2025/01/the-35-cent-commodore-64-softmodem.html)

## Building

To build from source, you need the [`xa65` crossassembler](http://www.floodgap.com/retrotech/xa/). You can then use the `Makefile`, or manually a command line like `xa -O PETSCII -o softmodem 35cent.xa` (PETSCII conversion must be specified).

## Before you file an issue or PR

This is a toy project intended largely for demonstration. Bug reports without PRs may or may not ever be addressed. Feature requests without PRs are subject to deletion. Rewrites or stylistic changes won't be accepted (fork it and make it your own).

## License

This program is placed in the public domain or CC0, as appropriate for the jurisdiction in question.

