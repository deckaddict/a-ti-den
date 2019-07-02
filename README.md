# Android TI(83) Development Environment

<details>
<summary>Backstory</summary>

My fascination for the TI calculators started when my brother got a TI-82 when I was 13 years old. The fact that it was possible to have such a small device on which you were still able to do programming on. I really fell for the portability and three years later when I got my TI-83 it didn't take long until I had found ticalc.org, tried all assembly programs, and a couple of months later started learning assembly myself.

This fascination for portability has followed me and I think that the most natural environment to use today is an Android phone. Combine this with a TI-83 project that was never finalized and there is a need to get the environment for TI-83 development running.

This repository lists a set of software that can be used as a development environment on Android. Details are for TI-83 but it will generally be the same for most z80 based devices.
</details>

<details>
<summary>Shell (termux)</summary>

Termux is a great terminal emulator. It contains a package management system and allows for the installation of lots of great linux tools that we need.

pkg install python clang cmake git p7zip
</details>

<details>
<summary>z80 cross assembler (caz)</summary>

In the Amiga section on ticalc.org we can find the z80 cross assembler CAZ that was written in the early 90's for the Amiga. The author (Carsten Rose) was foreseeing enough to make it ANSI-C compliant.

It can be built by replacing all instances of dcc with clang inside the Makefile then typing "make all".

Compiling something is then done with ./caz -o example.bin example.z80
</details>

<details>
<summary>83p management</summary>

There are two python scripts to manage 83p files. One of which can make an 83p file out of a binary file. Another that can split 83g files into 83p files.
</details>

<details>
<summary>Emulator (AndieGraph)</summary>

The Google Play Store contains quite a few emulators for TI-83. As far as I've found out, only one of them (Wabbitemu) has officially support to load 83p files. I have however not managed to get it working good enough.

Instead I prefer the more lean application called AndieGraph. This app is no longer available on the play store but its source code is available here (https://github.com/dgmltn/AndieGraph).

This emulator is based on AlmostTI. Although it doesn't feature a way to load 83p files it uses an external RAM file that can be manipulated.

The source is structured for the IntelliJ Android IDE but can be tweaked to work on your device for AIDE.

You will need your own ROM-file for the emulator.

AndieGraph can be started from termux by using the startTI script. Started from this there is a graphical glitch but good enough for quick feedback.
</details>

<details>
<summary>AlmostTX</summary>

Among with the scripts to manage 83p files there is a script called AlmostTX that can populate a fresh AlmostTI compatible RAM-file with 83p files.

Generate the clean ram file by starting AndieGraph and doing exit immediately after "Mem cleared" appears on the screen. The RAM-file is then found in the same location as your ROM-file.
</details>

<details>
<summary>HOWTO</summary>

Cloning this repo and running ./setup will install dependencies, download and compile caz, and add the repository directory to the path in .bashrc
Running tibuildandrun from a directory containing your source files will compile the code, link it to 83p, import to a RAM-file, and start AndieGraph.

</details>

<details>
<summary>Current constraints and future features</summary>

There are several improvements to this type of environment. I will list some suggestions here.

- The AlmostTX script is made for TI-83 ROM version 1.07000 no other versions are yet tested.
- Extracting 83p files from a RAM-file could be nice.
- Supporting other variable types than program-files.
- Make it work for more calculators, either by improving AlmostTX or making a more general link port service in the emulator.
- There is a pull request to improve the contrast handling in AndieGraph enabling fades. (see my fork https://github.com/deckaddict/AndieGraph)
- AndieGraph to get multitouch support. Pull request prepared. (see my fork https://github.com/deckaddict/AndieGraph)
- Letting link port signals through to the speaker meaning that all cool sound effects that people have done can be enjoyed.
</details>

<details>
<summary>Thanks</summary>

- David Hellerström for helping me with getting started and creating tiLin for me to have linksoftware from Linux.
- Ahmed El-Helw for his TI-83 Assembly tutorials that got me started.
- Hannes Edfeldt (Movax) for taking the time to chat with me and correcting my misunderstandings.
- Florent Dhordain for the sound through linkport, and documentation of the 83p file formats.
- Joe Wingbermuehle for all the awesome code and library support in SOS.
- Linus Åkesson for inspiration of fades using contrast.
- Doug Melton for making AndieGraph open source.
- To whoever created yoloader causing a copyright ruckus in the TI community.
</details>
