# DigitalCashFastGUI

## Problem

To implement a protocol for the use of digital cash using various protocols for maintaining secrecy, anonymity, authenticity, integrity, and mutual trust.

## Setting

This project is based on the protocol number 4, described in [SCHN96], p. 142. Basically this protocol implements an electronic cash system, in which the digital cash cannot be copied or reused more than once and the privacy of the customer's identity is guaranteed.

## Design

Basically this project was divided by the three parties(Customer, Merchant, Bank) and we were going to display the whole process simply and straightforward in an GUI. We generally followed every single step. We decided to use Visual Studio to implement and compile the C++ code in Win32 console application platform to demonstrate the process. Lots of GUI designers were tried . And then we decided to use Qt creator to which has its own library to display the user interface frame. Also, we are thinking about converting the code into Python to satisfy that it should be supported cross platforms for Linux, Unix, IOS, Windows. 

## Implementation

-	Digital Signature (follow the services steps)
-	QtGui and PyQt4

## Steps

1.	We (Alice) generate 10 money orders, 

A.	Each one has an amount=100;

B.	Each one has an uniqueness string, so we use a function of C++, to generate 10 uniqueness string, each identity bit string is a 8-bit binary string. 

C.	Each one has 10 pairs of identity bit strings: I1，I2，I3…In; So we use a function of C++, to generate 100 uniqueness string, and we assume that each identity bit string is a 8-bit binary string.

D.	Also each one has 10 pairs of lift side of identity bit strings: I1L，I2L，I3L…INL; So we use a function of C++, to generate 100 uniqueness string, and we assume that each identity bit string is a 8-bit binary string. 

E.	Then using secret splitting (XOR) to get right side of I (IR). I1=(I1L，I1R ); I2=(I2L，I2R); …

F.	After that, using bit-commitment. For this part, we use hash function.

G.	The next step is Blind signature (using RSA):
M=Amount XOR uniqueness string XOR H(M) XOR R1;
      Bank has public key (e), private key (d), public modulus (n);
      Blinding process:
      Alice chooses random k, 1 < k < n
      Alice blinds M by calculating
t = Mke mod n

H.	After all the processes above, the money orders have been completed.

2.	Alice took those money orders to the bank, we assume bank ask Alice to unblind randomly like the following order:
Unblinding process:
Alice unblinds td by calculating
	s = td/k mod n
is the s here is just like the one above, than the bank agree to sign.
Bank signs t by calculating
		td = (Mke)d mod n

3.	Alice took the remaining money order to the merchant, and unblind to the merchant.
Alice unblinds td by calculating
s = td/k mod n

4.	Merchant double checked the bank signature, and give Alice a 10-bit random binary string, Alice reveal the identity string based on the 10-bit random binary string( we assume that when 0, Alice reveal left part).

5.	For Bank, random choice of 1 out of N money orders sent by the customer to remain unopened. An algorithm that certifies that all the N-1 money orders have been filled with valid information. A procedure to certify that the orders received from merchants have not been used previously and storage of the uniqueness string and identity strings of the orders in a database file. Appropriate measures against reuse of the ecash. Finished the deal, and the merchant took the money order and the revealed identity string to the bank. Since we are not going to make this program to complex – Alice use the money order twice, we always assume that no one cheat.
