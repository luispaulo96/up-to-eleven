# Up to Eleven

This is the source code for the Up to Eleven game, a 2048 game written in 8080 assembly.

Made for the RC2025/10

The assembler used is zasm, which supports writing 8080 code using the Z80 syntax, here's the page:\
<https://k1.spdns.de/Develop/Projects/zasm/Distributions/>

The font used for the video display is based on the Amstrad CPC 464 font, here's the repository:\
<https://codeberg.org/Dmian/font-cpc464>

Build instructions for Linux

1) Run this command to assemble the code and generate the binary:

`zasm game.x80 --8080 --reqcolon -l0 -o binary.rom`\
or\
`./game.x80`

2) Use the split command to split the binary into two files:

`split -db 2048 binary.rom maze.`

3) Rename the two files (or create the symlinks):

`mv maze.00 maze.h && mv maze.01 maze.g`\
or\
`ln -s maze.00 maze.h && ln -s maze.01 maze.g`

4) Create a folder named `maze` and put the files `maze.g` and `maze.h` inside it:

`mkdir -p maze && mv maze.* maze`

4) To run the game on MAME use this command (MAME will complain about the checksums, just ignore it):

`mame -rompath . maze`
