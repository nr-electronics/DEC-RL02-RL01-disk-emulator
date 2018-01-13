# DEC RL02/RL01-diskemulator
FPGA based disk emulator for the DEC RL01 and RL02 disk drives

Secure the vintage software and preserve it on new technology

Aim of this project: Being able to use the RL02/RL01 Emulator on all DEC vintage computer platforms.


Overview and architecture
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


Implementation
The RL emulator is running on a MAX10/DE10-Lite , BeMicro CV , DE0-Nano and (on demand) on a DE1 board.
The necessary PCB board was developed in cooperation with the computermuseum muenchen. 
Additional Information on my homepage. Contact: RLEMU@cm-muenchen.de

