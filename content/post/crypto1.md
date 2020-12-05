---
title: "Cryptography - An elaborate elevator pitch"
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

In the language of cryptography, the process of making something secret is called _encryption_. 
We start with a message or _plaintext_, denoted by $M$, that we want to send to someone else. 
The value $M$ is encrypted via some _encryption function_, and the result is called a _ciphertext_, usually denoted by $C$. 
The encryption function usually depends on using some sort of secret value, typically referred to as a _key_ and denoted with $K$. 
A recipient of $C$ should be able to recover $M$ using an opposing function called a _decryption function_, only if they know what the key is. 

Now you may wonder, what exactly does $C$ look like? Or perhaps more precisely, what kinds of properties should it satisfy? 
This turns out to be a very nuanced question, and we're going to introduce each of the considerations one needs to answer it. 
At a glance, we obviously want our message to be secret, but what does that mean? Well, at the most basic level, we can say that if someone obtains $C$, 
they should not be able to determine the message M that it is hiding. 
However this begs another question, who exactly is the someone that we are trying to make our message secret to? 

Cryptographers have developed a stand-in character, usually called Eve, as the person perpetually trying to discover your secrets. 
To properly define what it means to be secret, we need to assume some things about Eve.
In other words, we need to know what Eve is capable of in order to properly defend against attack.

For now, we'll assume Eve has somehow gotten her hands on the ciphertext $C$ of a message $M$. 
Perhaps she has just this one, or perhaps she's been eavesdropping for a while and has many others. This is commonly referred to as a _ciphertext only_, a scenario where the adversary is not actively tampering with the system or messages, merely observing.  

In addition to her interaction type, we also need to specify how much computational power she has available to her. This can very quite greatly. Does Eve have a fixed number of computing cores? Is she capable of using quantum computation? The most common assumption is that Eve is capable of perform a _polynomial number of operations_ with respect to the inputs to the encryption function (in this case the key and the message).

In summary, we need to specify three aspects of our adversary in order to get a concrete definition of securty.
1) What is the adversary's _goal_? In our case, this was to determine the message $M$.
2) What are the adversary's _interactions_? We assumed a passive adversary with access only to some ciphertexts.
3) What are the adversary's _computing capabilities_? Here we assumed a polynomial time adversary.
