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
