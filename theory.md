# AtomicBombStrong

`AtomicBombStrong` is an app that can generate a strong key(password).

## Motivation:
Google chrome kept insisting me that my passwords might have been found in other data bases so I should change them and that's when I decided that I would generate my next set of passwords using my own app. So here we are, time to innovate!

When I was almost done with the prototype of my app, I asked myself:

`"So why not just write some gibberish text, save it and use it?"`

1. It is very easy to lose it and once that is lost, good luck resetting them.
2. Its not a fun activity. Fun is what follows. :)

## App requirements:
The resulting key must be super strong. (Duh.)

Let's get serious.
* It must be `reproducible`.
* It must be `uni-directional`.
* Every `[key:value]` pair must be unique.
* It must have an element of interest.
* It must be easy enough to reproduce without using the app, on-the-go if needed (provided you have average mental math capabilites). This one is my personal favourite.

`reproducible` meaning that I should be able to get that exact key generated again if needed.

`uni-directional` meaning there should be only `input -> output` flow. By no means there can be a reverse path (i.e. identification of steps in the program through reverse engineering). This means that even if the hacker were to be provided with a large data set of output keys from this app (a scenario where your new password(s) is(are) also leaked into the `www`), they should not be able to identify/decrypt/guess your other keys generated from the app.

## The stuff

People who dislike chemistry may stop at this point (just kidding, I am not so good at it either and here we are).

Chemical reactions. Yes, that's the element of interest I used at the core of this app.

The process goes like this:

`INPUT` -> `map into chemical reaction(s)` -> `perform the reaction` -> `perform selective math operations` -> `output`

## The app

It takes in your normal `phrase`/`password`/`md5`/`...` type looking string and generates a value that you may want to use as a `secret key`/`password` or for `any further ciphering needs`.

The app can work with or without an external encoder. The encoder implemented here is(are) `chemical reaction(s)`.

## Try it for yourself!

Finally, the [app is live here](http://dynamic.ankurdalal.com/php/runner.php)!

For demo, enter 'demo' without quotes (case sensitive) in `hash` and `reaction` field. Enter your word in the `phrase` field.

The demo uses a neutralization reaction `K.O.H + H.Br -> K.Br + H.2.O` as the cipher.

Four operations follow.

1. Atomic number. `(KOH = 28)`

2. A reactant itself. `(HBr)`

3. Producting alpha number map.

The input characters are mapped to reacting elements. Based on the products of the reaction, the characters are substitued back. For part 3, the characters are mapped to a number.

`K->d     O->e     H->m    Br->o`

```
Character to number map.
0-9 as is;
a-z = 10-35; 97-122
A-Z = 36-61; 65-90
other characters not mapped.
```
Hence, if we provide the thw `word` as `demo`, we get `1324`. `K->d->13` & `Br->o->24`

4. Concatenate alphabets.

The alphabets are put together based on the producting compound. `H2O -> mme`.

That's all of it. I hope you enjoy it!

P.S.: I was thinking of using the name PassStrong for this app but looks like something of that sort with the same name already exists (a physical keygen actually). Nevertheless, hopes are still high and honestly, it was fun development.

P.P.S.: I still need to change those old passwords. :P

[ankurdalal.com](https://ankurdalal.com)

---
Use of this idea or the name `AtomicBombStrong` without permission shall be considered as violation of intellectual property copyright.

Copyright © 2020 Ankur Dalal - All Rights Reserved.
