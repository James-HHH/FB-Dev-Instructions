##### Pre-read

Before reading this, if you are *not* coming here from the Furret Discord Bot, please leave immediately. Thank you.

If you're freaking out because you think it'd be too complicated for you, I am trying to keep this as friendly to use as possible, and once you get used to it, it's not too bad. If you already know JSON script, go ahead and skip to 'First Dialogue' to learn the syntax of this interpreter.

# Getting the Necessary Tools

Any text editors will work, but you’re still programming so something that will automatically finish brackets would be preferable. Something like [Atom](https://atom.io) or even [Repl.it](https://repl.it) is what you should use.

[Node.js](https://nodejs.org) is the language that the development.js script is programmed in. Now if you’re using Repl.it or another online IDE that supports Node.js, there’s no need to download it.

The [dovelopment.js](https://fcs--jamesahelton.repl.co/dovelopment.js) script is non-negotiable, you need it. It’s a local version of the interpreter found in the bot. You could try to program without the testing area, but I highly recommend against it. It’d be like a spelling test and you had to write a whole 2 pages but you aren’t allowed to proofread.

Google. For any *terms* I haven't specified, just use Google. But if it's a question about this, contact me at jhelton351@gmail.com and I could make an FAQ.

### Terminology

Key - `"key":`
Key Object / Array - `"key name": {object / array}`
Key Value - `"key name": "key value"`

Array - Collection of keys that could also have arrays in them.

Sect / Section - A provided way of organizing the code, supposed to be used to section off different scenes, settings, whatever.
Dio / Dialogue - The specified text/choices provided to the player.

### The Syntax of JSON

Before you write any code, you need to know how it comes together first. The instructions are written in JSON code, and it is very picky when it comes to what is where, but it doesn't have too much variety in the things you can do.

You're gonna want multiple keys in the same array most of the time.
For keys that are not the last (if there are multiple), you're gonna want to put a comma at the end of the value, to say "hey, get ready for another key".
But if it is the last or only key, don't put a comma.

Never let a bracket pair be on the same line. It doesn't look nice.

---

# First Dialogue

Let's start by making 'game.json' in the same directory as the dev.js file and putting a pair of {} brackets. Then we want to type `"metadata:" {},` in those brackets. (Don't worry, we'll get back to that.)

Make a new key called `"sect 1": {}` or something. This will be our first sect.

```json
{
  "metadata": {

  },

  "sect 1": {

  }
}
```

Now, inside sect 1's brackets, type 

```json
"sect 1": {
  "dio 1": {
    "character": "Sample name",
    "text": "Sample text from Foo, Bar",
    "end": true
  }
}
```

Back in metadata, type

```json
"metadata": {
  "sect": "sect 1",
  "dio": "dio 1"
}
```

What this is doing is saying, "When this program starts, the starting dialogue is 'sect 1, dialogue 1'. The order of the keys doesn't really matter, you just have to nest everything together correctly. (But you should go in order of what should be loaded first.) So when you fire it up, it should say whatever you set `"character": "text"` too!

Now, this is a neat trick for displaying text on a screen but it's really boring. let's make some choices.

---

# Adding a Choice

Let's add another dialogue and call it "dio 2". It doesn't matter what it's called, just don't call two dialogues the same thing. Oh, and don't forget the comma and double line-break!
Add the text, character, all of it. Just make sure there's the "end" tag.

```json
"dio 2": {
  "text": "texty text",
  "end": true
}
```

Now back in "dio 1", get rid of the `"end": true` and put `"choices": {}`. Inside choices, add `"1": {}`. It must be 1, as that will be the first choice. And since we don't have multiple dialogues to refer to yet, there's only one possible choice we can do.
So lets do:

```json
"dio 1": {
  "character": "Sample name",
  "text": "Sample text from Foo, Bar",
  "choices" {
    "1": {
      "text": "This is choice 1 and it leads to dio 2",
      "dio": "dio 2"
    }
  }
},
"dio 2": {
  "text": "This more sample text for dio 2",
  "end": true
}
```

If you've done everything right, you should see:

```
Sample name:
Sample text from Foo, Bar

1. This is choice 1 and it leads to dio 2>
```

The code we just made is in Single choice.json if you wanna take a look.

But that's not all we can do, we can have multiple choices in a single dialogue and theoretically infinite dialogues in theoretically infinite sections (Check out 'Mutltiple choices.json' to see how to refer to a different sect). Cool, huh? I will add variables in the future, but for now, this is all we got.

Happy creating!
