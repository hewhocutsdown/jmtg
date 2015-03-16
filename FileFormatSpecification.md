# Introduction #

A .tcg file is an encrypted .zip containing at minimum, an XML file and an image (.jpg or .png), and optionally one or more .py files.


# Details #

<p>JMTG is a game engine, and is intended to be used with both existing card designs as well as lending itself to new designs and card-swapping. To do this effectively yet securely, it implements a process similar to how many Linux repositories work. JMTG stores one or more public keys (by default it just has one game-specific one). Cards are stored in .tcg files, which are saved to the cards/ directory (specified in the settings).</p>

<p>The .tcg files are encrypted with the creator's private key. They are decrypted when you import them into your library. The decrypted .tcg file is a gzip-compressed folder containing an XML file (validated against the JMTG RELAX NG XML schema for the given ruleset <a href='the.md'>2009 MTG Rules Revision, in our example</a>), zero or more images (zero: uses default placeholder image; > 1: uses primary image as specified in the XML file by default) and zero or more .py files (if needed, they are referred to in the XML file).</p>

<p>In gameplay, once a game is selected and decks are prepared, the hashes, pub keys corresponding the hashes and the names of each card is compiled in a temporary decklist, which is transmitted to the other player(s). Each player's client then looks up the cards.<br>
<br>
If (OtherPlayerDeck.Card is not InMyLibrary AND it's public key<br>
<br>
If a card from another player's deck does not exist in your local library, but the hash matches the public key supplied, and the public key already exists in your system, then the card is automatically downloaded from the other player. If it does not exist<br>
<br>
</p>


<p>Optionally, the XML file can specify a hash value and a remote site to compare hashes against, to ensure against player modifications when networking. This idea needs a little fleshing out - how would one ensure that each player is using the same (intended) card?</p>