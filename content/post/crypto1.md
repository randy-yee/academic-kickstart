---
title: "Cryptography - First steps"
date: 2020-08-21T15:55:23-06:00
draft: false

image:
  caption: ""
  focal_point: ""
  preview_only: false

projects: []
---


December 4, 2020
4:43 PM

"Cryptography is the science of sending secret messages." 
Most professionals would say this is too simple or too narrow of a definition, but in every day life I find myself saying this phrase very often. 
Probably, most people don't want to listen to me explain things like digital signatures or message authentication codes, and they certainly don't want to hear me talk about math.
I plan on writing on many other aspects of cryptography in future posts, but for now this will serve as a working definition. 

In the language of cryptography, the process of making something secret is called encryption. 
We start with a message or plaintext, denoted by $M$ that we want to send to someone else. 
The value M is encrypted via some encryption function, and the result is called a ciphertext, usually denoted by $C$. 
The encryption function usually depends on using some sort of secret value, typically referred to as a key. 
A recipient of $C$ should be able to recover $M$ using an opposing function called a decryption function, only if they know what the key is. 

Now you may wonder, what exactly does $C$ look like? Or perhaps more precisely, what kinds of properties should it satisfy? 
This turns out to be a very nuanced question, and we're going to introduce each of the considerations one needs to answer it. 
At a glance, we obviously want our message to be secret, but what does that mean? Well, at the most basic level, we might say that if someone obtains $C$, 
they should not be able to determine the message M that it is hiding. 
However this then begs another question, who exactly is the someone that we are trying to make our message secret to? 
Cryptographers have developed a stand-in character, usually called Eve, as the person perpetually trying to discover your secrets. 
To properly define what it means to be secret, we need to assume some things about Eve.
To reflect what we said earlier, we'll first need to assume how Eve can interact with our encryption scheme. 
For now, we'll assume Eve has somehow gotten her hands on the ciphertext $C$ of a message $M$. 
Perhaps she has just this one, or perhaps she's been eavesdropping for a while and has many others. 
