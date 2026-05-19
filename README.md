UCF Assisted Learnubg Lab Python Loops Intro, Bv Victor S, Based on Python 2. Maybe compatible with future Verisions


---

# Extracting "PYTHON" from a Scramble with Nested Loops

A short guide on using nested loops to pull the letters of a target word out of a jumble of characters.

---

## The basic idea

You have a string of jumbled characters that contains the letters P, Y, T, H, O, N somewhere inside it, in order, with other letters mixed in. You want to walk through the scramble, pick out those six letters in the right order, and end up with the clean word "python".

Two loops do the work: the outer loop walks through each letter of the target word "python". The inner loop scans through the scramble looking for that letter.

---

## The example

The scramble:
```
scramble = "apxbycztdhpqornf"
```

The letters P, Y, T, H, O, N are hidden in there, in order, with other letters between them.

Code:

```python
scramble = "apxbycztdhpqornf"
target = "python"
result = ""
position = 0

for letter in target:
    for i in range(position, len(scramble)):
        if scramble[i] == letter:
            result += scramble[i]
            position = i + 1
            break

print(result)
```

Output:
```
python
```

---

## How it works, line by line

`result = ""`
Start with an empty string. We'll build up "python" one letter at a time.

`position = 0`
Track where we are in the scramble. We start at the beginning. After finding each letter, we'll move this forward so the next letter must come after the previous one.

`for letter in target:`
The outer loop walks through each letter of "python" in order: first 'p', then 'y', then 't', and so on.

`for i in range(position, len(scramble)):`
The inner loop scans through the scramble, starting from `position` (not from 0). This is the key idea: by starting from `position` instead of the beginning, we guarantee that each letter we find comes after the previous one.

`if scramble[i] == letter:`
Check whether the current character in the scramble matches the letter we're looking for.

`result += scramble[i]`
If it matches, add it to our growing result string.

`position = i + 1`
Move `position` forward so the next round of the outer loop starts searching after this letter, not before it.

`break`
Stop the inner loop as soon as we find the current letter. No need to keep scanning; we have what we need for now. The outer loop then moves on to the next letter of "python".

---

## The pattern behind the pattern

The outer loop walks through what you're looking for. The inner loop walks through where you're looking. The `position` variable carries information between iterations of the outer loop so each letter is found after the previous one.

This same recipe handles any "extract a sequence from a jumble" problem: pulling a name out of a sentence, finding sorted numbers in a list, picking specific items out of any ordered collection.

---

End Goal?
One scramble, one outer loop, one inner loop, one result: the clean word "python." Tested, em-dash-free, line-by-line explanation matching the style of the other guide.

---

Please Contact DatJavaClass for questions or Victor S on Slack for questions.
