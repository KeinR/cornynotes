
A command line cornell notes-like parser.

You write your notes in a text file with
the Best Editor of All Time (which should be VIM) in
a very simple format, and pass files and directories with notes
in them to the script. The script parses the files,
and then gives you a fzf search prompt where you can filter to
certain notes by question.

Each "note" consists of a question, answer, and zero or more examples.

Example:

```
This stuff isn't parsed
This area is for just general note taking

>>q
Here is a question. This is what will be searched for
when looking for this note. Keep in mind that when parsed,
due to how fzf works, newlines are replaced with spaces.
>>a
This is the answer. It is displayed when you select this note.
>>e
This is example #1
>>e
This another example.
Remember that the examples aren't actually required

And they can have spaces

Even extra space at the end

Until another line that only has ">>q" is reached
```

The output of the above is as follows:

```
+------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Question   | Here is a question. This is what will be searched for when looking for this note. Keep in mind that when parsed, due to how fzf works, newlines are replaced with spaces. |
+------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Answer     | This is the answer. It is displayed when you select this note.                                                                                                            |
+------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Example #1 | This is example #1                                                                                                                                                        |
+------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Example #2 | This another example.                                                                                                                                                     |
|            | Remember that the examples aren't actually required                                                                                                                       |
|            |                                                                                                                                                                           |
|            | And they can have spaces                                                                                                                                                  |
|            |                                                                                                                                                                           |
|            | Even extra space at the end                                                                                                                                               |
|            |                                                                                                                                                                           |
|            | Until another line that only has ">>q" is reached                                                                                                                         |
+------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
```

Help:
```
$ ./cornynote -h
usage: cornynote [-h] [-q] [-a] [-e E] F [F ...]

Look up formatted cornell notes

positional arguments:
  F           Folders or files containing entries

optional arguments:
  -h, --help  show this help message and exit
  -q          Supress warnings
  -a          Only print answer (ignores -e)
  -e E        Print only example X
```



