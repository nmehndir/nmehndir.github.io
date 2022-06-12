---
layout: post
title: "Simulating Coinflips Using Random Words"
date: 2022-06-12
---
I played a few games of Mafia on Friday. While reviewing gameplay with the narrator afterwards, he suggested that in situations where a player wants to randomly pick one of two options (e.g. one of two players to lynch or one of two players to kill), they could simulate a coinflip by picking a random English word, adding up the numbers the letters correspond to on an {‘a’:1 . . . ‘z’:26} scheme, then checking whether this number is even or odd.

I expected this would probably be sufficiently random, but I thought there might be a nontrivial bias in one direction. There are 5.5 vowels (‘a’, ‘e’, ‘i’, ‘o’, ‘u’, and sometimes ‘y’ (**Sidenote:** I want to look more into how frequently ‘y’ is used as a consonant vs. a vowel. This [dictionary site](https://grammar.yourdictionary.com/style-usage/when-is-vowel-easy-guide-words) claims that ‘y’ is a consonant iff it’s at the start of a word or at the start of a syllable. The first part is trivial to check but I’m not sure about how to implement the latter.)) and 20.5 consonants. All 5.5 vowels are odd ({‘a’:1, ‘e’:5, ‘i’:9, ‘o’:15, ‘u’:21, ‘y’:25}) and the consonants are split 13:7.5 even:odd. This made me expect a tiny bias on the “even” side because most of the consonants are even and I figured that vowels tend to be used in pairs. But now that I think about it, this is a pretty bad argument because it doesn’t account for the relative frequency of each letter; I might look into this further at some point in the future.

Anyways, I [tested this approach](https://github.com/nmehndir/misc/blob/main/are_rand_words_coinflips.py) using [WordNet](https://wordnet.princeton.edu/). It turns out that this approach is probably even better than flipping a coin (haven’t looked into this much but it seems like there’s consensus that all coins are at least slightly biased?): of the 146722 English words checked, 73352 are even and 73370 are odd. 
