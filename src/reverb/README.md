    =============================================================
    COPYRIGHT NOTE: This source code, and all of its derivations,
    is subject to the "ITU-T General Public License". Please have
    it  read  in    the  distribution  disk,   or  in  the  ITU-T
    Recommendation G.191 on "SOFTWARE TOOLS FOR SPEECH AND  AUDIO
    CODING STANDARDS".
    =============================================================

# History
The ITU-T Reverberation software tool was first released in
STL2005 (Cyril Guillaume & Stephane Ragot, France Telecom, France)
In STL2009, the following updates have been performed:
 - inclusion of a mono impulse response for fullband audio signals
 (Minjie Xie, Polycom, USA)
 - inclusion of stereo impulse responses for superwideband audio signals
 (Claude Marro, David Virette, France Telecom, France)
 - proper saturation of the reverberated output signals
 (Jonas Svedberg, Ericsson, Sweden)



# ITU-T/UGST Reverberation module

## C code
```
 reverb.c: ....... demonstration program using routines in reverb-lib.c
 reverb-lib.c: ... tools for reverberation
 reverb-lib.h: ... Prototypes for reverb-lib.c
```

# Room Impulse responses ('IR' folder)

## mono folder

IR responses in mono are stored in 2 folders : `IR\mono\big_endian` and `IR\mono\little_endian`.
Folder `IR\mono\big_endian` contains UNIX byte oriented files (high-byte first)
and folder `IR\mono\little_endian` contains low-byte-first oriented files.

  - File `visio.IR`: sound capture at 100cm distance in a small video-conferencing room,
  - File `meeting50.IR`: sound capture at 50cm distance in a meeting room,
  - File `meeting100.IR`: sound capture at 100cm distance in the same meeting room.
  - File `IR48.IR`: sound sampling at 48kHz.

WARNING : The first three impulse responses were measured with a sampling frequency of 32kHz.
They are for use with 32 kHz sampled speech files. The last impulse `IR48.IR` is sampled at 48kHz.
It is for use with 48 kHz sampled speech files.

## stereo folder

IR responses in stereo are stored in 2 folders : `IR\stereo\big_endian` and `IR\stereo\little_endian`.
Folder `IR\stereo\big_endian` contains UNIX byte oriented files (high-byte first)
and folder `IR\stereo\little_endian` contains low-byte-first oriented files.
WARNING : All these impulse responses were measured with a sampling frequency of 32kHz.
They are for use with 32 kHz sampled speech files.

# Makefiles

Makefiles have been provided for automatic build-up of the executable program
and to process the test sequences, WHEN made available by the user and left
in the subdirectory `bin`:
```
makefile.cl : .... makefile for MS Visual C compiler
makefile.unx: .... makefile for cygwin gcc compiler
```

The MS Visual C provided makefile can run a portability test on the demo program. They
need the archive test-freqresp.zip ([pk]zip compatible archive) and [pk]unzip to
extract the proper source and reference processed files. This file can be found in `..\freqresp\`
```
test-rev.zip: ..... ZIP-compatible archive with the test files in the UNIX
                    byte orientation (high-byte first).
```