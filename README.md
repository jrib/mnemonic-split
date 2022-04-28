One-time pad for mnemonic phrases
=================================

An intentionally simple algorithm with an intentionally simple (read: easily recreated from memory) implementation.

***What is this code for?***

It allows one to split a mnemonic phrase commonly used for cryptocurrency wallets into two mnemonic phrases.  These two mnemonic phrases can then be combined to recover the original mnemonic phrase.

***Can you show me an example?***

    $ ./split_by_words.py split "abandon zoo"
    mnemonic1:  episode shell
    mnemonic2:  reflect dentist

    $ ./split_by_words.py combine "episode shell" "reflect dentist"
    mnemonic: abandon zoo

***How does it work?***

For each word in the original mnemonic phrase, a random word is generated.  A second word is calculated so that: `[id of original word] = [id of random word] + [id of second word] mod 2048`.  2048 is the length of the wordlist embedded in this code.

***What word list is being used?***

As of 2022-04-26, the english word list used by [electrum](https://github.com/spesmilo/electrum/blob/097ac144d976eb46dff809e1809783dc78ab6d8b/electrum/wordlist/english.txt) and [bip39](https://github.com/bitcoin/bips/blob/ce1862ac6bcffa1dd20aad858380e51e66e949ea/bip-0039/english.txt) is embedded in the code.

***Why don't you...?***

The point of this algorithm is that it is easy to conceptualize; the algorithm can be described in a single sentence (so it can be included alongside the mnemonic phrases); and it can easily be reimplemented, even by hand.  So I probably won't add any features like implementing Shamir's secret sharing or splitting into more than 2 parts.  Having said that, feel free to open discussions via pull requests.

***Should I use this code?***

You probably shouldn't ever enter your mnemonic phrase into an online computer.  But if you understand what this code does and want to use it offline, then sure, go for it.

You may want to consider using [slip39](https://github.com/satoshilabs/slips/blob/master/slip-0039.md) instead depending on your use case.
