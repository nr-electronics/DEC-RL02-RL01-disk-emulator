# DEC RL02/RL01-disk emulator
                           FPGA based disk emulator for the DEC RL01 and RL02 disk drives                                   

**Secure the vintage software and preserve it on new technology**                                                                 


**Overview:**                                                                                                                 
Project Start was in 2009. In the initial phase, a PIC processor and shortly afterwards an ARM SBC 
was used. This idea quickly turned out to be unrealizable and I walked step by step into the FPGA world.
First, I had worked on the MAX-2 CPLD. The realization failed due to the non-existent onchip-memory.
Then the DE1 board was used with the CYCLON 2 FPGA. The RL01 emulator in the first version was completed in 
**2012** (see video). Then, the next versions were realized with the DE0-Nano, BeMicro CV  board and it was now 
possible to emulate up to 4 RL02 disk drives simultaneously. Unfortunately, the BeMicro CV board is no longer 
available until now ( JAN 2017), to bad and it was a big setback.                                         
The current version has been ported to the DE10-Lite board and many new options have been developed, 
such as basics of WLAN support. All details in DE10_UserManuel_V2_2.pdf. 


**Architecture:**                                                                                                   
Basically, the design of my DEC RL02/RL01 disk drive emulator works like a Solid-State-Disk(SSD),
interfacing the DEC RL-disk serial bus signals (1980) to the current FPGA technology. 
The heart of my design is a DPR ( Dual Ported RAM ) which can hold one RL-track.
DPR-Port #1 is responsible for the firmware communication like MFM De/En-coding, provides the 
complete data transfer to/from  DPR-Port #1 based on a data sequencer and runs completely automatically.
DPR-Port #2 is responsible for the data transfer to/from the (NIOSII) CPU. Sounds easy, but it was very
difficult to construct the right data format emulating the cartridge format with CRC and all the servo 
information. The (NIOSII) CPU is also responsible for the data transfer in the memory with up to 
4 emulated RL drives and finally also for the transfer to/from the SD card.
The operation of the RL02/RL01 emulator is best viewed with a VIDEO via YouTube, however
in the first version from **2012**, based on the DE1-Board. https://www.youtube.com/watch?v=0i3ypBU39as                              


**Implementation** ( see also www.pdp11gy.com ) :                                                                              
The RL emulator is running on a **MAX10/DE10-Lite** , BeMicro CV , DE0-Nano and (on demand) on a DE1 board.
The necessary PCB board was developed in cooperation with the http://www.computermuseum-muenchen.de. 
Additional Information on my homepage. Contact: RLEMU@cm-muenchen.de
The up and running projects are based on QUARTUS Version 16.1 :                                                          
**MAX10_RL_Emulator V1.5**,  BeMicro_RL_EMULATOR_V5  and  DE0_RL_EMULATOR_V5                                                           
After extracting the zip files, the complete development environment for QUARTUS version V16.1 is 
available. The respective project is available with all the sources and correctly Quartus-setup. 
The C programs for eclipse-nios2 can be found in the folder software.                                                                                                 
SD-Card, FAT32 support is provided by : http://elm-chan.org/fsw/ff/00index_e.html + http://www.emb4fun.de/                 
( Please send me an E-Mail if need access to the BeMicro_CV and DE0_Nano based implementation.)           

**Data format:**                                                                                                            
The DEC RL01/RL02 disk drive did have a capacity of 5.2MB/10.4MB, 2 Heads(surfaces), 256/512 cylinder, 
40 sectors/track. 1 sector contains 128 16-bit words (256 Byte) of Data + 12 16-Bit words for 
Servo/Header/CRC Data = 140 words(280 Byte)/sector. The emulater is using the .DEC format which contains 
all the information plus a serial number and the bad sector file. The size of the .DEC file for the
RL02 is 11.521 KB and for the RL01 5.761 KB. Another disk format is the disk image structure .DSK which 
is often used for CPU emulators. To convert this data, the necessary programs are available on my homepage
or direct by: www.2jo.de/pdp11/rlutils/rlutils.zip  ( written/converted to windows by a friend )

**Summary**
This project is no longer being developed by me. The disadvantages are too big: slow NIOSII CPU, no network 
and slow SD card implementation. The new generation: SoC/HPS based environment.

**Now available**                                                                                                                 
DE0-Nano-SoC Board Implementation based on  Altera Cyclon V FPGA with ARM Cortex-A9 CPU. The code has 
been ported successfully to the SoC/HPS environment. Unfortunately, the DE0 Nano SoC board is no longer 
available, so everything must be ported to the replacement- on the replacement board DE10-Nano. More 
details on https://github.com/pdp11gy/SoC-HPS-based-RL-disk-emulator . It is the ideal board because all 
the SIMH CPU emulators are also runable ! 












