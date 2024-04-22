# Final_project_QxQ_23-24
This repository contains the code used for encrypting and decrypting messages using the BB84 Quantum Key Distribution (QKD) protocol, as part of a final project undertaken during the Qubit by Qubit program in 2023-2024.


## Project Description

In the Encryption in Python Project, students will write code to encrypt and decrypt a message of their choice using a key created through Quantum Key Distribution (QKD). They will analyze their work and write a short paper discussing the steps of encrypting and decrypting data and the effect an eavesdropper would have on the success of transmitting encrypted data.

## Project Overview


This project consists of two parts: first, we need to create a key that will be used to encrypt and decrypt messages, for this purpose, we will use the BB84 quantum protocol.
Second, we will define two functions; one for encrypting and another for decrypting messages. For this task, we utilize binary addition, in this way, we need to transform the message into binary format before encrypting it.
![image](https://github.com/LazaroR-u/Final_project_QxQ_23-24/assets/80428982/81dcb297-b143-4f04-b0a6-a02168784b21)


### Creating the Key

The BB84 protocol is utilized to generate a secure key for encryption and decryption. The protocol involves two parties, Alice and Bob, connected by a classical communication channel. Alice generates random binary strings a and b, which encode the state and basis of qubits, respectively. She then prepares qubits accordingly and sends them to Bob. Bob measures the qubits and stores the results, and Alice and Bob publicly announce their basis choices. The matching bits between Alice's string a and Bob's measurement string indicate a secure cryptographic key. The BB84 protocol is resilient against intercept-and-resend attacks, ensuring the security of the key exchange process.


#### No eavesdropper
In the absence of an eavesdropper, the BB84 protocol operates smoothly. Alice prepares her qubits according to the random binary strings a and b and sends them to Bob. Bob measures each qubit in the appropriate basis c and stores the results in string m. Since there is no interference from an eavesdropper, Alice and Bob's measurements perfectly align. When they publicly announce their basis choices (b and c), they find that they used the same basis for most qubits. By comparing these bits, they derive a secure cryptographic key, as their measurements are consistent and unaltered. For example, if Alice and Bob have a different basis, then Bob doesn't measure anything. 
![image](https://github.com/LazaroR-u/Final_project_QxQ_23-24/assets/80428982/43ff0385-37dd-460b-be64-03afffcf3631)

On the other hand, if Alice and Bob have the same basis then, Bob will measure a 1. 

![image](https://github.com/LazaroR-u/Final_project_QxQ_23-24/assets/80428982/9abd3b54-09f5-4695-998a-49c34b0aa402)


#### Eavesdropper 
When an eavesdropper, Eve, is present, the scenario becomes more complex. Eve intercepts the qubits sent from Alice to Bob and attempts to measure them to gain information about the key. However, the act of measurement disturbs the quantum states of the qubits, introducing errors into the system. Eve then sends modified qubits to Bob, hoping to remain undetected. However, since her measurements have disrupted the original states, Bob's measurements no longer match Alice's as consistently. When Alice and Bob compare their bases (b and c), they find discrepancies in their measurements, indicating the presence of an eavesdropper. By detecting these inconsistencies, Alice and Bob can take measures to ensure the security of their communication, such as discarding the compromised key and initiating a new key exchange process.

![image](https://github.com/LazaroR-u/Final_project_QxQ_23-24/assets/80428982/60bc0d46-1278-46fd-9b01-4933eef9fc43)


### Encrypt-Decrypt

The encryption and decryption tasks involve transforming a message using a specific key. This is achieved through binary addition, where the message is converted into binary format before encryption. The encrypted message can then be securely shared over a channel, with only the recipient possessing the correct key able to decrypt and read the original message.

For instance, the table below illustrates the transformation of various messages into binary format:

| Original Message  | Binary Format Message                                      |
|-------------------|------------------------------------------------------------|
| 12345             | 11000000111001                                             |
| "Google"          | 010001110110111101101111011001110110110001100101         |
| "HswrTY@K"        | 0100100001110011011101110111001001010100010110010100000001001011 |
| "I am a future quantum leader (:" | 01001001001000000110000101101101001000000110000100100000011001100111010 10111010001110101011100100110010100100000011100010111010101100001011011 10011101000111010101101101001000000110110001100101011000010110010001100 10101110010001000000010100000111010 |
