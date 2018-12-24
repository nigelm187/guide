---
title: ABC Problem
---
## ABC Problem

<pre>
let canMakeWord = word => {
  let letterBlocksArray = [ 
                            { letters: ["B", "O"], used: false }, { letters: ["X", "K"], used: false },
                            { letters: ["D", "Q"], used: false }, { letters: ["C", "P"], used: false },
                            { letters: ["N", "A"], used: false }, { letters: ["G", "T"], used: false },
                            { letters: ["R", "E"], used: false }, { letters: ["T", "G"], used: false },
                            { letters: ["Q", "D"], used: false }, { letters: ["F", "S"], used: false },
                            { letters: ["J", "W"], used: false }, { letters: ["H", "U"], used: false },
                            { letters: ["V", "I"], used: false }, { letters: ["A", "N"], used: false },
                            { letters: ["O", "B"], used: false }, { letters: ["E", "R"], used: false },
                            { letters: ["F", "S"], used: false }, { letters: ["L", "Y"], used: false },
                            { letters: ["P", "C"], used: false }, { letters: ["Z", "M"], used: false }
                          ];

  return word
      // split the word into an array so we can loop it using a reduce
      .split("")
      // use a map to convert each character in the word to lowercase
      .map(character => character.toLowerCase())
      // use a reduce to check through the word.
      .reduce( (flag, wordCharacter) => {
          // Identify any block which hasn't been used and which has the letter in it
          let idx = letterBlocksArray.findIndex( block => !block.used && (block.letters[0].toLowerCase() === wordCharacter || block.letters[1].toLowerCase() === wordCharacter));
          if (idx >= 0) {
            // if we've found a block with the letter ,mark it as used so it can't be used again
            letterBlocksArray[idx].used = true;
          } else {
            // if we don't find an available block, set the reduce boolean to false
            flag &= false;
          }
          return flag;
      }, true); 
}
</pre>


