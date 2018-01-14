# DEC RL02/RL01-disk emulator
                           FPGA based disk emulator for the DEC RL01 and RL02 disk drives                                   

Secure the vintage software and preserve it on new technology                                                                 

Aim of this project:                                                                                                                                                                                                   
Being able to use the RL02/RL01 Emulator on all DEC vintage computer platforms.




Overview and architecture:

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
in the first version, based on the DE1-Board. https://www.youtube.com/watch?v=0i3ypBU39as


Implementation ( see also www.pdp11gy.com ) :                                                                              
The RL emulator is running on a MAX10/DE10-Lite , BeMicro CV , DE0-Nano and (on demand) on a DE1 board.
The necessary PCB board was developed in cooperation with the computermuseum muenchen. 
Additional Information on my homepage. Contact: RLEMU@cm-muenchen.de

The up and running projects are based on QUARTUS Version 16.1 :                                                          
MAX10_RL_Emulator,  BeMicro_RL_EMULATOR_V5  and  DE0_RL_EMULATOR_V5                                                           
SD-Card, FAT32 support is provided by : http://elm-chan.org/fsw/ff/00index_e.html + http://www.emb4fun.de/   


Open issues:                                                                                                        
DE0-Nano-SoC Board Implementation: NOT yet runable ! It is the ideal board because it can also be used 
for other purposes such as PDP-11 and PDP-8 emulators. However, a lot of issues must be new developed. 
A NIOS II CPU with the existing C-code is very difficult to implement here, so most of all has to be 
ported to the ARM Cortex-A9 CPU environment. Currently the entire firmware is successfully ported and
a NIOS-II CPU is running from the onchip memory using the I/O with the PCB board (AUG 2017). I have 
already made many attempts to sync the NIOS CPU with the Cortex-A9 CPU, but so far without success. 
At least, I have little experience with the ARM DS-5 v5.26.0 Developer and run always into new problems.
I am running out of time, maybe I am too old :-) Maybe someone wants to complete this project ??








