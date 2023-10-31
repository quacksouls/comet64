# Achievement: The Master

{% youtube id="IHmwZFrX-vM", title="57. Open the voodoo file, Comet 64" %}{% endyoutube %}

This achievement requires you to unlock the secret ending. On the home screen,
you should see four disks on the left side. On the right side are two disks and
two text files. One of the text files is named "voodoo". To access this text
file, you need a 4-letter code. You do not need to solve all puzzles in a disk
for a character of the code to appear. Each character of the code is unlocked
once you have solved a certain number of puzzles in each disk on the left hand
side. Solve the required number of puzzles in a disk and look for a box that
says `code: <char>`, where `<char>` is a character of the 4-letter code. Note
the order of each letter from each of the four disks, going from disk 1 to
disk 4. Now click on the "voodoo" file, enter the 4-letter code, and you should
be presented with a bunch of text. The most useful part of the text is on the
very first line. This line shows a user name. Make note of the user name or copy
it down somewhere. Quit the game, load the game again, and choose an empty save
slot. If you do not have an empty slot, you must delete one of the save slots
and choose the new empty slot. You would then be prompted to enter a user name.
Type in the user name you found in the "voodoo" file.

{% youtube id="GjLDRkQpDno", title="58. The Master ending, Comet 64" %}{% endyoutube %}

You are now given one last puzzle to solve. Click on the box that says "99.
ErRor" and you would be presented with some lines of code. Run the code if you
want, but it would not solve the puzzle. Comment out the code. Now each input is
an encrypted string. Decrypt each string and print the unscrambled string. The
command `output = str` no longer works. You must use the command `print str`.
Each encrypted string is obtained by interchanging the first and last characters
of the string. To unscramble the string, all you need to do is swap these two
characters around.

```
str = input;           // Read a string.
char = str[0];         // First character.
switch char;           // Store first character.
int = str.length - 1;  // Index of last character.
char = str[int];       // Last character.
str[0] = char;         // Last character at first index.
switch char;           // Retrieve first character.
str[int] = char;       // First character at last index.
print str;             // Print decrypted string.
```
