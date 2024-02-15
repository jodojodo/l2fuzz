# L2Fuzz

A stateful fuzzer to detect vulnerabilities in Bluetooth BR/EDR Logical Link Control and Adaptation Protocol (L2CAP) layer.

## Prerequisites

Ensure pyenv is installed. Then install python version 3.6.9, which needs a patch for pip to actually work. The patch is already part of this repository.

```bash
pyenv install --patch 3.6.9 < [repository]/pip.patch
```

Enter the folder and allow the direnv:

```bash
direnv allow
```

L2Fuzz uses scapy 2.4.4 and ouilookup 0.2.4. Also, it uses Bluetooth Dongle.

```bash
sudo apt-get install libbluetooth-dev
pip install scapy==2.4.4
pip install pybluez
pip install python-statemachine
pip install ouilookup==0.2.4
```

## Running the tests

1. move to L2Fuzz folder.
2. run l2fuzz.py .

```bash
sudo env "PATH=$PATH VIRTUAL_ENV=$VIRTUAL_ENV" python l2fuzz.py
```

3. Choose target device.

```bash
Reset Bluetooth...
Performing classic bluetooth inquiry scan...

	Target Bluetooth Device List
	[No.]	[BT address]		  [Device name]		[Device Class]	  	[OUI]
	00.	AA:BB:CC:DD:EE:FF	  DESKTOP       	Desktop   	      	Vendor A
	01.	11:22:33:44:55:66	  Smartphone    	Smartphone	      	Vendor B
	Found 2 devices

Choose Device :
```

4. Choose target service which is supported by L2CAP.

```bash
Start scanning services...

	List of profiles for the device
	00. [0x0000]: Service A
	01. [0x0001]: Service B
	02. [0x0002]: Service C
	03. [0x0003]: Service D
	04. [0x0004]: Service E
	05. [0x0005]: Service F

Select a profile to fuzz :
```

5. Fuzz testing start.

### End test

```bash
Ctrl + C
```

### Log file

The log file will be generated after the fuzz testing in L2Fuzz folder.

## Paper

L2Fuzz paper is published in Jun 27, 2022 through "The 52nd Annual IEEE/IFIP International Conference on Dependable Systems and Networks".

Title : L2Fuzz: Discovering Bluetooth L2CAP Vulnerabilities Using Stateful Fuzz Testing

Paper : https://arxiv.org/abs/2208.00110

Video : https://youtu.be/lrc-mJTw1yM

Authors : Haram Park (Korea University), Carlos Nkuba Kayembe (Korea University), Seunghoon Woo (Korea University), Heejo Lee (Korea University)

Contacts : freehr94@korea.ac.kr, https://ccs.korea.ac.kr/
