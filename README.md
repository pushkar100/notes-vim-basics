# Vim Basics (Short Notes & Quick Reference)
A Quick reference to Vim commands that contains short explanations on particular functionalities of Vim.

## Basics
NOTE:
- [] represents optional parameters.
- <> represents a certain set of characters like the ones for movement/motion (Ex: <motion> for h,j,k,l,w,$,^,0,... etc!).

### Opening Vim Editor:

- `vim`             = [From CLI] Open a new instance of Vim editor from CLI (No file is specified).
- `:e filename`     = [From VIM] Open a file from inside the Vim editor. (':e' is short for ':edit')
- `vim filename`    = [From CLI] Open specified file in Vim from CLI.

### Help on Commands Usage Inside Vim:

- `:help <command-name>`  (Ex: ':help :s' opens the help pages for the substitute/replace command)

### Saving and Quitting:

- `:w`  = Save the changes (Alternatively, you may use ':write').
- `:q`  = Quit editing (Returns to CLI) (Alternatively, you may use ':quit')
- `:q!` = Forcefully quits. (If unsaved changes existed, it would discard them and exit).
- `:wq` = Save changes and quit.

(Note: `:w filename` = If we opened vim without a filename then while saving the changes to it we must specify the new filename.)

#### Repeat Last Command Given:

`.`   = Repeats the last command executed in vim (When in Normal mode)

## Modes:

### Vim Modes:

- Insert Mode (Enter text where cursor is seen)
- Normal Mode (Traversing the file and other manipulations) 
- Command Mode (Run commands. Mix of different modes and containing other options)

Special mode: Visual Mode (Mainly for visibly copying/selection text)

#### Entering Command Mode:

`:`   = Enters command mode from Normal Mode.

#### Entering Normal Mode:

Press `<ESC>` key (escape) to enter Normal Mode. Alternatively: You can also use `CTRL + [` for the same.

(Note: Entering Command Mode from Insert Mode => Enter Normal Mode(ESC) and hit ':' [A Colon])

## Insertion:

### Entering Insert Mode:

- `i`   = Enter Insert mode at cursor. (The 'i' letter has more uses when it acts as a motion command (Covered Later)).
- `I`   = Enter Insert mode at first non-blank character on the current line.
- `a`   = Enter Insert mode after cursor. (Learn more about 'a' motion in command mode (Covered Later))
- `A`   = Enter Insert mode at the end of the line.
- `o`   = Enter Insert mode on the next line.
- `O`   = Enter Insert mode on the above line.
- `C`   = Delete from cursor to end of line and begin Insert.
- `s`   = Delete character under cursor and enter Insert mode.
- `S`   = Delete line and begin Insert at beginning of same line.

## Movement:

### Scanning Text (Motion):

- `h` (or) Left Arrow   = Move Left
- `k` (or) Up Arrow     = Move Up
- `l` (or) Right Arrow  = Move Right
- `j` (or) Down Arrow   = Move Down

(We can combine the movement with an number argument. Ex: `3j` will move cursor down 3 lines (or 3 + Up Arrow))

### Moving to Specific Positions:

- `gg`  = Moves cursor to the beginning of the document (Beginning of the line number 1).
- `G`   = Moves cursor to the end of the document (Beginning of the last line).
- `:N`  = Moves cursor to the beginning of the line number N in the document (Ex: )
- `$`   = Moves cursor to the end of the current line.
- `^`   = Moves cursor to the first non-blank character on the current line.
- `0`   = Move to the 0th character of the current line.

(Note: 'Ngg' or 'NG' or ':N'       = All 3 move the cursor to the Nth line of the file (Starting from the top).
)

### Other Basic Motions (w, b, e):

- `w`   = Forward to the beginning of the next word.
- `W`   = Forward to the beginning of the next WORD.
- `b`   = Backward to the next beginning of a word.
- `B`   = Backward to the next beginning of a WORD.
- `e`   = Forward to the next end of a word.
- `E`   = Forward to the next end of a WORD.

word => Any non-character, WORD => Words separated by spaces.

(Again, we can combine commands with number arguments. Ex: 3w will take us to the beginning of the 3rd next word in forward direction)

### Slightly Obscure Movements:

- `[n]f<character>`    = Move cursor forward to specified <character> (Inclusive) (on a line).
- `[n]F<character>`    = Move cursor backward until specified <character> (Inclusive) (on a line).
- `[n]t<character>`    = Move cursor forward until specified <character> (Exclusive - stops cursor one position before character) .
- `[n]T<character>`    = Move cursor backward until specified <character> (Exclusive - stops cursor one position before character).

(Ex: 'fg' will take cursor to next forward appearance of 'g', '3T(' will take the cursor to one position before the 3rd earlier '(' backwards) 

### Advanced Motions:

- `()`      = Move cursor between Sentences ('.' Delimited words). ['(' for Previous sentence & ')' for Next sentence]
- `{}`      = Move cursor between Paragraphs (Next empty line). ['{' for Previous Paragraph & '}' for Next Paragraph]
- `[[`      = Move cursor to the  beginning of the current section. (A section depends on filetype. Ex: PHP sections are PHP functions).
- `]]`      = Move cursor to the end of the current section. (A section depends on filetype. Ex: PHP sections are PHP functions).

### Screen Motions:

- `CTRL-D`  = Move cursor HALF A SCREEN DOWN.
- `CTRL-U`  = Move cursor HALF A SCREEN UP.
- `CTRL-F`  = Move cursor ONE FULL SCREEN DOWN (F for forwards).
- `CTRL-B`  = Move cursor ONE FULL SCREEN UP (B for backwards).
- `M`       = Move cursor to the MIDDLE OF THE SCREEN.
- `H`       = Move cursor to the TOP OF THE SCREEN. (Prefixing a number N will put cursor N lines Below the Top of the Screen. Ex: '3H' will put cursor 3 lines below Top).
- `L`       = Move cursor to the BOTTOM OF THE SCREEN. (Prefixing a number N will put cursor N lines Above the Bottom of the Screen. Ex: '3L' will put cursor 3 lines above Bottom).
          
### Screen Motions that DON'T MOVE THE CURSOR:

- `zt`      = Place Current Line at the TOP of the SCREEN. (Useful for viewing, say, a function() definition).
- `zb`      = Place Current Line at the BOTTOM of the SCREEN. (Useful for viewing, say, viewing the previous function definition).
- `zz`      = CENTER the SCREEN.

## Search and Replace Text:

### Searching:

- `/`   = Searches for a word forwards from the cursor (Ex: Type '/Forward' and hit ENTER)
- `?`   = Searches for a word backwards from cursor (Not really needed when '/' is already there)
- `*`   = Searches forward for the current word (The entire word the cursor is on) [Bounded]
- `#`   = Searches backward for the current word (The entire word the cursor is on) [Bounded]
- `g`*  = Same as * but the search is 'unbounded'. It matches partial words also. 
      (Ex: * on word 'for' will match 'forward' also - not possible in bounded)
- `g`#  = Same as # but the search is 'unbounded'. It matches partial words also. 
      (Ex: # on word 'for' will match 'forward' also - not possible in bounded)
      
### Traversing through the search matches:
- `n`   = Go to the next matched word.
- `N`   = Go to the previous matched word.

** Note: **

- Search is **case-sensitive** by default (can be changed in settings)
- Search does not wrap-around to the first match when it hits the bottom of the search, by default (can be changed in settings)
- We can use Regular Expressions in the search using '/' or '?':
    Ex: Running '/\n\n' will search for all the blank lines in a file.
        Running '/l[aeiou]' will highlight all the words starting with 'l' followed by a vowel.
- We need to use the escape sequence(\) for certain symbols in text while searching (Ex: search /'\/Forward to search for '/Forward)
- `:set incsearch` to enable incremental search. That is, Vim starts searching for the term while you are typing it.


### Substituting/Replacing Text:

- `r`                           = Replace the current character (The character to the under the cursor).
- `R`                           = Replace from current cursor position until we tell it to stop (By using ESC to get back to normal mode).
- `:s/pattern/string`           = Search and replace pattern with string ON THE CURRENT LINE ONLY. (Note that there is NO '%' used) (BUT ONLY REPLACES THE FIRST OCCURRENCE ON EACH LINE.)
- `:%s/pattern/string`          = Search and Replace pattern with string THROUGHOUT THE FILE. (BUT ONLY REPLACES THE FIRST OCCURRENCE ON EACH LINE.)

### Replacing Text Using Flags: 

Format is either ':s/pattern/string/flag' (or) ':%s/pattern/string/flag'

#### Flags:

- `g` = Global, replace ALL occurrences of pattern throughout the file (Including the second/third/.. occurences on a line).
- `c` = Confirm replaces. 
          - `y` for 'Yes', 
          - `n` for 'No', 
          - `a` for 'Yes for all remaining matches', 
          - `q` or `<ESC>` for 'Quit substituting',
          - `CTRL-E` to 'scroll the screen up', (Not in Vi)
          - `CTRL-Y` to 'scroll the screen down' (Not in Vi)
 - `i` = Case-insensitive replacement (Vim replacements are case-sensitive by default).
 - `&` = Repeat the last `:s` command.

We may combine flags. Ex: `:%s/bacon/brocoli/gc` replaces all instances of bacon with brocoli throughout the file with confirmation for each.

`:N,Ms/pattern/string/flag`   = Search and Replace pattern with string considering only the text between line number N to M. (Ex: :1,4s/bacon/brocoli/g replaces all instances of bacon with brocoli within lines 1 to 4)

** IMPORTANT TIP **

- Combining Searching & Replacing (Steps):
    - Search for a term. (Ex: '/fire')
    - Replace the searched term - omit the pattern. (Ex: ':s//flame' - Replaces all the instances of searched word, fire, with flame)
- Replacing only a PART of the Searched term (Steps):
    - Search for a term normally and insert '\zs' in between.
    - Whatever comes AFTER it in the search is considered in the NEXT Replace command. 
    (Ex: `/[^ ]\zs(` - This will search for a '(' that is not appearing after any space. 
          But, only '(' is considered for the next replace since it follows '\zs'. 
          And, only the replaceable portion of search gets highlighted. 
          Ex: '(' gets highlighted.)
    - Replace the searched term - omit the pattern. (Ex: `:s// (` - Replaces all the instances of searched word, '(', with ' (').
    - USE '\zs' to make part of search "AFTER IT" to be replaceable in the next replace command
    - USE '\ze' to make part of search "BEFORE IT" to be replaceable in the next replace command

## Undo and Redo:

### Undo/Redo Changes:
- `u`       = Undo last Action.
- `CTRL+R`  = Redo last Action.

## Copy, Paste, Delete and Change:

### Copy/Paste Commands:

- `[n]y<motion>`    = Copy(y) text. Combine y with a motion keyword. Optionally, prefix with a number(n) to repeat action that many times.
                  ('yw' copies current word, '3yw' copies 3 words forward from current word, etc.)
                  We can use any motion key with y.
                  (Ex: yj, y$, y<up-arrow>, y<right-arrow>, yG, ygg) 
- `[n]yy`           = Copies the whole current line. Optionally, prefix with a number(n) to repeat the copy action forward that many times.
                  (Ex: '5yy' copies the next 5 lines including the current line)
- `[n]p`            = Paste copied text (Places after cursor position). If ENTIRE LINE was copied, it is pasted on the NEXT LINE.
                  (Optionally, prefixing command with a number(n) will repeat the paste action that many times)
- `[n]P`            = Paste copied text (Places before cursor position). If ENTIRE LINE was copied, it is pasted on the PREVIOUS LINE.
                  (Optionally, prefixing command with a number(n) will repeat the paste action that many times)
- `v`               = Enters Visual Mode. 
                  (We can use motion commands(w, j, G, etc) and see exactly what text is being selected and then press 'y' to copy it!)
                  (Type ESC to return to normal mode and use p or P to paste accordingly.)
                  
(Note: p or P work not only for last yanked text(y command) but ALSO for the LAST DELETED TEXT (The d command))

### Deleting text:

- `[n]d<motion>`    = Delete(d) text. Combine d with a motion keyword. Optionally, prefix with a number(n) to repeat action that many times.
                  ('dw' deletes the current word, '3dw' deletes the next 3 words from the current word, etc.)
                  We can use any motion key with d.
                  (Ex: dj, d$, d<up-arrow>, d<right-arrow>, dG, dgg>
- `[n]dd`          = 'dd' deletes the current line entirely. Optionally, prefix with a number(n) to repeat the delete action that many times forward.
                  (Ex: '5dd' deletes 5 lines forward including the current line)
- `D`               = Deletes text from Cursor to the End of the Line when in Normal Mode. (Alternatively: Use 'd$')
- `x`              = Delete the character to the right of the cursor. 
- `X`               = Delete the character to the left of the cursor.

(Note: Pressing 'x' continuously keeps deleting the character under the cursor. Hence, it acts like the 'delete' key.)

### Changing Text (Instead of Deleting):

- `c<motion>`       = Replace selection text (from motion). Similar to delete(d) but puts us in 'Insert' Mode to type new text. (Ex: cw replaces the current word and puts us in insert mode.)
- `[n]cc`           = Deletes the current line and puts us in insert mode at the beginning of a new line (at the same location). (Prefixing with a number (n) would delete contents of all lines and put us in insert mode on a new line.)

Tip: To change all the contents written between quotes("..."):
Place the cursor on the first character after the opening quote and press 'ct"' (Without the single quotes wrapped around it).

## More About the `i` Motion:

The `i` command, when it follows another command, stands for 'INSIDE' something.
It can be used to move between two similar characters (EXCLUSIVE - Does not include those similar characters):
That is, 'i' can be used to move in between Quotes("" or ''), Brackets({} or () or []), etc.

### Examples:

- `di"`                 = Deletes all characters within double quotes(""). The cursor can be ANYWHERE in BETWEEN the quotes("").
- `di{` (or) `di}`      = Deletes all characters within double quotes({}). The cursor can be ANYWHERE in BETWEEN the quotes({}).
- `ci"`                 = Deletes all characters within double quotes("") and places in 'Insert' mode. 
                  (Again, the cursor can be ANYWHERE in BETWEEN the quotes("").)
- `ci(` (or) `ci)`      = Deletes all characters within double quotes("") and places in 'Insert' mode. 
                  (Again, the cursor can be ANYWHERE in BETWEEN the quotes("").)

## More About the `a` Motion:

The `a` command, when it follows another command, stands for 'AROUND' something.
It is VERY SIMILAR to 'i' when 'i' is used in command mode - Except: it is INCLUSIVE!
That is, it matches the similar/matching characters also when it is in between them.

### Examples to try out:

- `da"`
- `da{` (or) `da}`
- `ca"`
- `ca(` (or) `ca)`    ... etc!

## Tricks: Delete/Change/Copy from Cursor to a Searched Word:

Press 'd' and then hit '/' to search for a word => This will DELETE from cursor position upto the position of the matched word.

Press 'c' and then hit '/' to search for a word => This will DELETE from cursor position upto the position of the matched word and will also put you in INSERT MODE.

Press 'y' and then hit '/' to search for a word => This will COPY from cursor position upto the position of the matched word.

## Visual Mode Tips:

- `v`           = Goes into Visual mode.
- `V`           = Goes into Visual mode where we may select complete lines while moving up an down(j,k).
- `gv`          = Goes into Visual mode and RE-SELECTS the PREVIOUSLY Selected Block.
- `%`           = Pressing % when in Visual mode will select upto the matching character. Can be used to select entire blocks/functions. (Ex: Cursor on { and you press % , it will select upto the matching })
- `o`           = Moves cursor to opposite side of Visual Selection and we can expand selection in other direction (Ex: Using k & j keys).

### We can run commands in the visual mode:

- `d` = Deletes selected text (Alternate: 'x')
- `y` = Yanks/Copies selected text
- `c` = Changes the selected text. It goes back to Insert mode and we can change the previously selected visual text.
- `I` = Goes into Insert mode allowing us to insert at the BEGINNING of the selected text.
- `A` = Goes into Insert mode allowing us to insert at the ENDING of the selected text.

Make sure you press `<ESC>` upon Inserting/changing text: Because hitting enter will be considered as a new line and not end of insertion.

### REPLACING TEXT Within a Visually Selected Portion:
We can make our selection in the usual way in Visual mode and then type the `:s` command normally.

(Command line will appear something like `:<,>` => No problem. We can continue typing the substitution command.)

** IMPORTANT **

- BLOCK/COLUMN Selection in Visual Mode: (VISUAL BLOCK) 

Similar to MULTILINE selection in Sublime:
Press `CTRL-v` and you will end up in visual mode - column/block selection.
Using the `j` and `k` movements will select same columns/blocks in the lines above/below resp.
Using the `h and `l` movements will select adjacent chars to the block from left/right resp.
(Make sure to press <ESC> upon Inserting/changing text: Because hitting enter will be considered as a new line and not end of insertion.
In the case of Block selection, there may be a slight delay in inserting/changing all rows of the visual column.
)

- TEXT OBJECT SELECTION (VISUAL MODE ONLY):

Text objects can be Selected in Visual Mode using 'i' or 'a'.

- `i` will contain the 'inside' of a text object. (Ex: text contained inside an html tag)
- `a` will include the beginning and ending characters of the text object as well. (Ex: text + tags)
   - Selecting tags:
        - `it` will select inside of a tag (say, in html)
        - `at` will select the whole tag (say, in html)
   - Selecting words:
        - `iw` will select inside of a word
        - `aw` will select the whole word
        - `iW` will select inside of a word (space separated)
        - `aW` will select the whole word (space separated)
   - Selecting Brackets:
        - `i(` and `i(`  [Similarly for `a`]
        - `i[` and `i]`  [Similarly for `a`]
        - `i{` and `i}`  [Similarly for `a`]
        - `i>` and `i<`  [Similarly for `a`]
   - Selecting Quotes:
        - `i` followe by &lt;quote&lt; (Single or double quotes)

- Post the selection - We may use the commands to delete, yank, etc.
   - We can even delete PRE-Selection - Ex: `dit`
   - We can even change PRE-Selection - Ex: `cit`

## Macros and Registers:

Pressing `CTRL-G` will show us information about the file: File-Name, Current-Line, Total-Lines, %-Of-File-Viewed, Column-Number. (Use this command to get any of the above listed information.)

- MACROS - Help us **record** a sequence of commands.
- REGISTERS - Help us store those recorded MACROS.

Together, they can be effectively used to store and repeat the same sequence of commands multiple times.

### View Register Names and Values:

-`:reg`          = Shows you a list of registers with their values. (Values can be overwritten by re-assigning the register). (Alternatively, you can type `:registers`).

### Start Recording a Macro (Record a Sequence of Commands):

- Press `q` plus a register name (say, 1) and you will see **recording** appear on the bottom of the screen. (Ex: `q1`)
- Start typing commands. (Ex: `djj^`)
- Press `q` again to stop recording. (The sequence of commands have been saved in the mentioned register, that is, register `1`).

### Running/Repeating the Macros stored in a Register:

- To run a macro once: Type `@` followed by the register name (Ex: `@1` will execute the macro stored in register 1).
- To run a previously executed macro: Type `@@` (Ex: `@@` will execute the last macro that was executed from a register).
- To executed a macro multiple times: Prefix the execution with a Number (Ex: `10@a` will execute macro stored in register `a` 10 times).

### Marking & Remembering a Cursor Position using a Register:

- Type `m` followed by register name. This will remember the position of cursor. (Ex: `m1`)
- While editing other portions of the file, if we intend to go to the earlier marked position of the cursor, we can press single quote symbol followed by the register name containing the position. (Ex: "'1" will move to cursor position saved in register 1)

(Note: Press single quote twice Ex: `''` to go back to last marked cursor position.)

## Use Command Line Directly From Vim:

- `:!<CLIcommand>`      = Executes any Command-Line Interface(CLI) Command. The results are shown on the Terminal & a prompt to return to Vim is shown.

### Copy-Pasting the commands from Terminal:

- `:r !<CLI-command>`  = Copies the results of the executed CLI command and pastes it inside current file under the cursor (New line). Alternatively, you can also use `:read !<CLI-command>`).

### Sending Text inside Vim to CLI Command as Input Text (Standard input):

- Make a selection for input in Visual Mode.
- Run the CLI command with some parameters.

Example:

`:<','>!coffee -c -s -p`

(The above command runs the 'coffee' compiler with `-c` option to compile, `-s` to take standard input (The text selected in Visual mode),`-p` to print the result in vim instead of saving it to a file)

Another Example: 

Visually copy haml code and run `:<','>!haml -s` to convert haml to js and replace the former text.)

## Autocomplete in Vim:

Pressing `<ctrl-n>` will open up the autocomplete/context dropdown while typing something in INSERT Mode.
This context menu feature can be used to autocomplete function names/object properties/variables/etc. appearing in the file.

### Passing through the Context Menu dropdown:
- `<ctrl-n>` goes downwards.
- `<ctrl-p>` goes upwards.

(We can replace `<ctrl-n>` with another character, like <Tab>, which is easier to use - See Mappings section for shortcuts.)

## Buffers in Vim:

Buffers are special places in memory that store information about the files that are open in Vim. Each file opened in vim is allocated a buffer of its own. (Ex: Opening vim with `vim single.js index.html` will actually open two files(buffers) but we see only one at a time.)

### View the list of open files in vim:

`:ls`     = Displays the buffers and information about the files they hold. (Format: BufferNumber-Flags-FileName)

Note: Flags Inside the buffer listing: 
  - The current buffer (currently visible file) is marked with `%a`, and 
  - previously visited file (previous buffer) is marked with a `#`

### Visiting Other buffers:

- `:bn`     = Opens the NEXT buffer (Alternate: ':bnext') (Use ':ls' and you will see that %a and # have changed). 
- `:bp`     = Opens the PREVIOUS buffer (Alternates: ':bprevious' or ':b#') (Use ':ls' and you will see that %a and # have changed). 
- `:bf`     = Opens the FIRST buffer (Alternate: ':bfirst').
- `:bl`     = Opens the LAST buffer (Alternate: ':blast').

Advantage of using buffers: Macros recorded and executed in one can be re-executed in the other buffers as well.

### Deleting a buffer:

- `:bd<BufferNumber>`   = Deletes the file from vim which has the given buffer number associated with it. (Ex: `:bd12`)

## Vim Tabs and Windows: (Not in Vi)

### Managing Multiple Files At Once (TABS):

- `:tabe <file>`    = Opens a file to edit in a new tab.
                  (Aternates: `:tabedit <file>` or `:tabnew <file>` or even `:tabnew` followed by `:edit <file>`).
- `:gt` (or) :tabn`  = Next Tab (Can also use :tabnext)
- `:gT` (or) :tabp`  = Previous Tab (Can also use :tabprevious)
- `:tabm #`         = Move current tab to position number # (Zero-indexed). No argument? Move to the end. (Can also use - `:tabmove)
- `:tabo`           = Close All Other Tabs.
- `:tabc`           = Close Current Tab. (Alternatively, you may close all windows in a tab, using `:q`, o close that particular tab)

### Managing Multiple Files At Once (SPLIT WINDOWS):

- `:vs <file>`      = Opens specified file by VERTICALLY splitting the window (Alternate is ':vsplit <file>').
- `:sp <file>`      = Opens specified file by HORIZONTALLY splitting the window (Alternate is ':split <file>').

(Note: We can combine horizontal and vertical splits - No problem!)

### Moving Between Windows:

- `CTRL-W` + `l`  = Moves cursor to the RIGHT window.
- `CTRL-W` + `h`  = Moves cursor to the LEFT window.
- `CTRL-W` + `j`  = Moves cursor to the BOTTOM window.
- `CTRL-W` + `k`  = Moves cursor to the TOP window.

(In short, we can use the movement keys - hjkl to move up/down and left/right between windows)

### Changing Position of a Particular Window: (Or, swapping windows)

- `CTRL-W` + `L`  = Moves Current Window to the RIGHT END.
- `CTRL-W` + `H`  = Moves Current Window to the LEFT END.
- `CTRL-W` + `J`  = Moves Current Window to the BOTTOM END.
- `CTRL-W` + `K`  = Moves Current Window to the TOP END.

### Resizing Current Window:

- `CTRL-W` and then `+`  = Increases height of current window by 1 unit. (To increase by X units, type `CTRL-W` and then `X+`)
- `CTRL-W` and then `-`  = Decreases height of current window by 1 unit. (To decrease by X units, type `CTRL-W` and then `X-`)
- `CTRL-W` and then `>`  = Increases width of current window by 1 unit. (To increase by X units, type `CTRL-W` and then `X>`)
- `CTRL-W` and then `<`  = Decreases width of current window by 1 unit. (To decrease by X units, type `CTRL-W` and then `X<`)
- `CTRL-W` and then `=`  = Equally distributes height/width between horizontally/vertically split windows.

Closing Windows(Files):

- `:q`    = Normal way of quitting files.

Note: Files from the windows we quit still exist in the buffers. (Type `:ls` to confirm).

### To REOPEN a CLOSED FILE/WINDOW as a:

- Horizontal split: Type `:sb<buffernumber>`
- Vertical split: Type `:vert sb<buffernumber>`

Note: We can combine tabs and windows - One tab can have multiple windows - Try it!

Tip: Keep files of similar context open in windows (in same tab) and for files of different contexts, keep them in different tabs.

## Vim Structure:

### Vim Directory Structure: (Inside Home Folder `~`)

- `.vimrc` (This is the user settings file)
- `.vim/`
    - `after/`  (Another plugins folder - rarely used)
    - `syntax/` (Syntax scripts)
    - `plugin/` (Store single file plugins here)
    - `colors/` (Stores all the colors)
    ...
    - `bundle/` (Plugins containing multiple files spanning multiple folders are usually installed using pathogen/bundle)

## About Vim:

`:version`    = Check Vim Version: Shows vim version (Ex: 7.4 Improved)

## Vim Settings:

### Temporary settings (for current vim session): 

Use the colon(:) prefixx command (in command mode):

- `:<command> <setting-name-and-args>`    = Sets a particular rule for the current vim session.

### Overriding Default Vim Settings (for all files opened by you, the user):
(Default settings are stored in /usr/share/vim/vim74/)

Edit the `~/.vimrc` file to have your own user settings for vim.

On the CLI - `vim ~/.vimrc`,
Inside Vim - `:edit ~/.vimrc` or `:edit $MYVIMRC` ($MYVIMRC is a global variable representing YOUR .vimrc file)


We can insert the colon(:) based commands into .vimrc, each command on a new line.

Note: 
- Do NOT prefix ':' next to command in .vimrc file - since it is not getting invoked immediately.
- Use double quotes (") to start a comment from cursor position to End-of-Line in .vimrc file.
- Run ':source ~/.vimrc' inside vim for changes made to '~/.vimrc' to take shape (Alternatively, you may close and reopen vim).

Run `:source %` on any current file will make the updates to that file take effect.

### Certain Rules:

- `:set number`       = Shows the line numbers to the left of every line of the file.
- `:syntax on`        = Enables syntax coloring while viewing different types of files in Vim.
- `:set incsearch`    = Vim starts searching for the pattern automatically while you type it.
- `:set ignorecase`   = Allows for a case-insensitive search (Vim search is case-sensitive by default).
- `:set hlsearch`     = Highlights all the Words that match the searched pattern.
- `:set nohlsearch`   = (Opp. of hlsearch) Does not highlight all the matching search words. (Alternately, use ':noh').
- `:set nolist`       = Vim will NOT print the invisible characters such as new-line, tabs, etc. (Default in Vim)
- `:set list`         = Vim will print the invisible characters such as new-line, tabs, etc.
                    (Tab by '^I', Newlines by '$' on the screen)
- `:set noexpandtab`  = Tabs are NOT replaced with spaces (Default in Vim)
- `:set expandtab`    = Inserts space characters whenever the tab key is pressed (Convert tabs to spaces).
- `:set smartindent`  = Indentation for new lines based on tabs. (Might be intrusive - careful)
                    (Decides where to place the cursor on the new line w.r.t the indentation of the previous line).

Note: `:set softtabstop=X` (or) `:set sts=X` will set X no. of spaces per tab while typing in INSERT MODE.
This is helpful when a file that's open has different spaces/tab width than what's defined in your vim settings(shiftwidth, default 8).

### Setting an Automatic Fold Method:

- `:set fdm=<value>`    = Alternate is to use `:set foldmethod=<value>`.

### Setting filetypes inside vim: 

(Better to do this inside vim instead of .vimrc since it can have 'syntax on' instead)

`:set ft=javascript`    = Syntax highlighting for filetype 'javascript'. Use other file types for other types of files.
(This is usually helpful when vim has opened a new file that it does not recognise the type of.)

## GVim:

Stands for 'Graphical Vim'.

Not available for Mac (Mac instead uses MacVim).

Advantages:
- GUI.
- Mouse enabled.
- Buttons exist for various commands.

## Vim Indents and Folds:

### Some command rules:

- `:set nolist`       = Vim will NOT print the invisible characters such as new-line, tabs, etc. (Default in Vim)
- `:set list`         = Vim will print the invisible characters such as new-line, tabs, etc. (Tab by '^I', Newlines by '$' on the screen)
- `:set noexpandtab`  = Tabs are NOT replaced with spaces (Default in Vim)
- `:set expandtab`    = Inserts space characters whenever the tab key is pressed (Convert tabs to spaces). (Default number of spaces for a tab is = 8)
- `:set shiftwidth=X` = Changes the number of spaces per tab used to X units when 'expandtab' is enabled. (Ex: ':set shiftwidth=4')
(See more such rules under 'VIM SETTINGS' section).

### Tabbing/Indentation(NORMAL MODE):

`>>`              = This will indent current line to the right by tabs (or, spaces if 'expandtab' is set).
`<<`              = This will indent current line to the left by tabs (or, spaces if 'expandtab' is set).

Note:
To indent X lines from current line, press X>> or X<<, whichever side you wish to indent. Ex: `5>>` will indent 5 lines from cursor position to the right.

#### We can also indent lines inside VISUAL MODE(v):

Go to visual mode(v), make a selection and type either:

- `>` for right indent or
- `<` for left indent.

### Smart Indentation:

- `:set smartindent`  = Indentation for new lines based on tabs. (Might be intrusive - careful) (Decides where to place the cursor on the new line w.r.t the indentation of the previous line).

Example: 
Moving to a new line under a tabbed line will place you in the same column.
But, moving to a new line under an `if(..) {` line will tab you one more time on the new line.

**IMPORTANT**

- Automatically Adjust Indentation (Prettify Code):
  - Method 1:
          Visually Select a piece of text(v) and press '='.
  - Method 2:
          When in Normal mode, Press '=' and an UP/DOWN Movement.
          
  (Ex: `=3j` will automatically adjust indent of 3 lines down from the cursor)
  
- Adjust Indentation of the ENTIRE FILE (Prettify Completely):
  Goto Line 1 (`gg` or `:1`) & Press `=G` in Normal Mode.

### Adjusting Indentation when Hitting <TAB> in INSERT MODE:

Say, you have a file that is indented by 3 spaces/tab. But, on pressing <tab> yourself (in insert mode), 8 spaces are added (or, whatever is specified in 'shiftwidth'). To change this setting back to 3 spaces for tab in INSERT MODE:

- Go to NORMAL MODE and type `:set softtabstop=3` or `:set sts=3`

### Indenting in INSERT MODE:

- Press 'CTRL-T' to indent the current line FORWARDS (Adv: Can be done while typing in insert mode).
- Press 'CTRL-D' to indent the current line BACKWARDS (Adv: Can be done while typing in insert mode).

### VIM FOLDING:

#### Create Manual Folds:

- `zf<motion>`   = Creates a fold from lines chosen by the movement (Ex: `zf5j` will create fold of 6 lines below including current one).
                (Folds will be something like '+--  3 lines: function c(a) --' & the line is highlighted).
- `zo`            = Opens a fold.
- `zc`            = Closes a fold.
- `zd`            = Deletes a fold. (Content of fold is not deleted - still exists in expanded/non-fold mode).

Example: Go to a block of code and press `zf%` it will fold from current line upto the line holding the matching brackets - one fold!

#### Toggling Between All the Folds in a File:

- `zi`            = Opens all folds if closed & closes all folds if they are open (toggle) (This can be used to enable/disable existing folds in a file).

#### Automatic Folding:

`:set fdm=<value>`    = An automatic fold method(<value> tells you the type of fold). (Alternate is to use ':set foldmethod=<value>').(One of the most common autofold method is: `:set fdm=syntax` which folds according to the file type.)

There are other values for auto folding.

Ex: `:set fdm=diff` which can be used while comparing two similar files - the common portions of the code are folded. Run `:help foldmethod` for more information.

Ex: `:set fdm=marker` which allows us to define a sequence of opening and closing characters for custom defined folding.

Note: `zC` will NOT ONLY close current fold but all the folds upto the root fold - That is, closes all the nested folds upto outer one.

#### Custom Folding by Setting Markers:

- `:set fdm=marker`                                           = Set fold method using markers.
- `:set foldmarker=<openingsetofchars>,<closingsetofchars>`   = Define the markers for folding (Ex: ':set foldmarker={{{,}}}')

Go into that fold (Defined by the markers) and press `zc` or `zo` or `zi` etc. to open/close the fold.

Note:
To set a fold comment (appears when closed) => Have a commented line at the beginning of fold: 
`// <comment> <openingsetofchars> ... `.

## Some More `~/.vimrc` File Settings:

Some useful settings to save in the .vimrc file: 
(Remember - DO NOT USE ':' as prefix while placing rules inside .vimrc files)

Comments in .vimrc are denoted by double quote("). These are single line comments.

- `:set nocompatible`                   = If there exists a Vim way of doing things that Vi also does then VIM way is always chosen (Better way is the vim way since it is the improved version and has different approaches to execute the same commands.)

- `:filetype on`            = Helps identify files based on their file type.
- `:filetype indent on`     = Helps indent files based on their type.
- `:filetype plugin on`     = Helps identify the plugins that work with a filetype.

### Setting variables in Vim (in ~/.vimrc):

- `:let <variable-name> = <value>`     (Ex: let mapleader = ",")

- `:syntax enable`          = Enables syntax processing.

Opinion:
Setting a foldmethod (Ex. ':set foldmethod=syntax') inside the vimrc file may not be the best since you may want to change fold styles while editing a file.

- `:set autoindent`         = Similar to ':set smartindent' and sets the indentation automatically for a file while typing.

- `:set hlsearch`           = Highlights all the matching terms while searching (& it stays this way until a new pattern is searched)
- `:set nohlsearch`         = Opposite to 'hlsearch' (Recommend you use this setting).

- `:set fileencoding=utf-8`   = Supplying a encoding to this rule will make sure all the characters seen are of that format (recommended).
- `:set encoding=utf-8`       = Similar to 'fileencoding'. Keep both values the same to maintain consistency.

Note:
'encoding' affects what is displayed,
'fileencoding' affects what is written to the file - Hence keep both consistent (same values)

- `:set backspace=<value(s)>`   = Somewhat advanced setting - deals with how backspace is used (Run ':h backspace'). (Don't use it till you understand it fully).

- `:set tabstop=N`                       = N number of visual spaces per TAB.
- `:set softtabstop=N`                   = N number of visual spaces per TAB while TABBING in INSERT MODE.
- `:set expandtab`                       = Tabs are converted into spaces (default is 8 spaces/tab).
- `:set shiftwidth=N`                    = Changes the number of spaces per tab to N number.

- `:set ignorecase`       = Allows for a case-insensitive search (Vim search is case-sensitive by default).
- `:set smartcase`        = Ignores case as long as you type No Uppercase Letter in your search. 
                        (If you type even one uppercase letter in the search, it becomes a case-sensitive search!)

- `:set gdefault`         = Always subsitutes patterns GLOBALLY - If this rule is set then NO NEED to set the 'g' FLAG during searches(/).
- `:set incsearch`        = Begins searching while you are typing the pattern in the search command(/).

- `:set showmatch`        = Highlights the matching Brackets[] / Parentheses() / CurlyBraces{} when one of them is under the cursor.

- `:set list`       = View all the tabs & line endings displayed.
- `:set nolist`     = Opposite of list (tabs & line endings are hidden). (Default)

- `:set number`     = Adds line numbers to the left gutter.

- `:set noswapfile`   = Disables swap files (Learn more about it on your own!)

- `:set visualbell`   = Normally when you are trying to do something wrong in Vim, an alarm is sounded. 
                    This rule replaces the alarm with a continuous screen flashing.

- `:set cursorline`   = Highlights the line that you are in (Current line / line on which cursor is placed).
- `:set nocursorline` = Opposite of cursorline (removes it) (Default)

- `set wildmenu`      = Visual autocomplete for command menu.
- `set showcmd`       = Show last command in right bottom bar (HELPFUL!).
- `set showmode`      = Shows mode (Insert/Normal/Visual) on the bottom left corner (HELPFUL!).

### Setting Visual Color columns:

Visual color columns appear on the screen on a particular column number. These are just for display and do not affect the text. The use for such columns are to enable the user to indicate a width for each line (For ex: Helpful while writing a blog post and you want to neatly display the text within a fixed layout)

- `:set cc=N`       = Colors the column number N on the screen (Alternate: ':set colorcolumn=N')
- `:set cc=N,M,O`   = Colors the column number N, M, & O on the screen (Alternate: ':set colorcolumn=N,M,O')
- `:set cc-=N`      = Removes color column on line N on the screen (Alternate: ':set colorcolumn-=N')
- `:set cc-=N,M,O`  = Removes color column on lines N, M, & O on the screen (Alternate: ':set colorcolumn-=N,M,O')

- `:set background=dark`            = Sets a dark background for vim
- `:colorscheme <colorschemename>`  = Applies a color scheme theme (which resides in a file inside "~/.vim/colors/") to Vim.

**Some advanced filetype settings:**
Learn about the 'au' command/rule from other resources.

### Some Automatic Window Resizing Commands:

`:set winwidth`, `:set winheight`, `:set winminheight`, etc. => Google and find out how automatic resizing takes place.

### For GUI options (& MacVim): 

Refer to the .vimrc file settings video (do not bother unless you are working with them!)
Ex. Rules: 'guifont', 'guioptions', etc.

## Customizing Vim - Pathogen Tool:

'Pathogen' tool is used to install plugins into vim. Before pathogen, it was really hard to install plugins in vim, 
especially the ones which required certain files to exist in certain folders.

### Installing Pathogen (Steps):

- Visit https://github.com/tpope/vim-pathogen
- Scroll down to the README section and copy+paste the commands specified into Linux/Mac terminal

(Fow Windows - check online)

The copy/pasted commands will do the following:
- Create two folders - 'autoload' and 'bundle'.
- Copy the 'pathogen.vim' source code into the 'autoload' folder.

### After Installing Pathogen:

We need to add it to our `~/.vimrc` file:
Add this line after all the 'filetype' rules: `call pathogen#infect()` - This is responsible for loading plugins downloaded to '~/.vim/bundle' folder.

### Installing a plugin using pathogen:

(This example install 'nerdtree' plugin which is a FILE EXPLORER for Vim.)

- Go to the Vim.org page (or) Github page of the plugin: (Ex: https://github.com/scrooloose/nerdtree)
- Follow the installation guide VIA PATHOGEN in the README of the github pages of the plugin. (Usually a 'git clone' command)
- Nerdtree will be downloaded into a new 'nerdtree' folder inside the '~/.vim/bundle' folder.

### Structure of a plugin (Inside `~/.vim/bundle/<plugin>`):

- /doc        = Contains documentation for the plugin.
- /plugin     = Contaisn the code for the plugin itself.
- /syntax     = Defines the syntax rules for the various components of the plugin.

Apart from these 3 standard folders, other custom folders might exist inside a plugin - which will mostly be triggered from code residing from within the 3 standard folders.

### For Nerdtree plugin: 

Open vim or a folder in vim & you will see a file explorer opened - we may scan through the subdirectories & choose files to open.

- Opening a folder in nerdtree: press `o` (Expands the folder)
- Close parent folder: Press `x`
- Opening a file in nerdtree: press `o` (Opens the file in vim)
- Go up one folder in nerdtree: press `q`
- Show hidden files of a folder: press `I` (Toggle action)

### Opening the Nerdtree left sidebar while a file is opened:

- `:NERDTreeToggle`     = Opens if closed / Closes if opened the nerdtree file explorer sidebar.

Moving between nerdtree sidebar and file windows:
Same way in which you move between various windows in a tab - 'CTRL-W' followed by one of h,j,k, or l

### Adding a new file/folder using Nerdtree:

Press `m` which opens up a menu.
From the menu choose the option to '(a)dd a child node'.
It will create a file/folder with given name in the current Nerdtree directory.

### Moving a file/folder using Nerdtree:

Press `m` which opens up a menu.
From the menu choose the option to '(m)ove the current node'.
You can now edit the path of the file and the file will be moved to the specified path.
(Similar steps for copying a file)

### Deleting a file/folder using Nerdtree:

Press `m` which opens up a menu.
From the menu choose the option to '(d)elete the current node'.
It deletes the current file/folder (file currently pointed to in nerdtree) from the system.

Nerdtree - very famous plugin and very good!

Many good vim plugins have been created by 'Tim Pope' - https://github.com/tpope

Check out some other cool plugins: 'Snipmate' & 'Command-T'.

## Vim Color Schemes:

### Check the current color scheme:

- `:colorscheme`      = Returns the current color scheme in use (or, just ':colo')

### Using/Applying a colorscheme:

`:colorscheme <colorschemename>`    = Applies the specified colorscheme to Vim. (Alternate: ':colo <colorschemename>')

**FOR COLOR SCHEMES THAT ARE "NOT" PLUGINS INSTALLED USING PATHOGEN**

Vim colorscheme files are stored in '~/.vim/colors' and the <colorschemename> is the name of the specific file in that folder - but excluding the extension (like .vim). Therefore, add such a colorscheme file to the '~/.vim/colors' folder.

**FOR PATHOGEN COLORSHEME PLUGINS** 

Follow the pathogen way of installing. That is, git clone plugin folder into '~/.vim/bundle'.

Note: Type `:colo ` and hit `<TAB>`. It will autocomplete a new colorscheme evey time you hit <TAB>. Hit <ENTER> to apply a color scheme (for that session).

### Vim color schemes can have two variants(in-built):

One for 'dark' background and one for 'light'.
So, we can specify the background like this:

- `:set bg=light` (or) `:set bg=dark`     = Sets a light/dark background (You may use 'background' instead of 'bg').

Note:

- Open vim and set a colorscheme. Change background and see if the second variant of the applied color scheme is set. (Color will change if the second variant for the color scheme exists)
- It is common to save a permanent background and color scheme for all files in vim. Save the 'bg' & 'colo' rules in your ~/.vimrc.

We can edit a colorscheme setting - open the file & change the rules (NOT RECOMMENDED FOR ALREADY EXISTING COLORSCHEMES).

### Creating your own colorsheme files (Advanced):

Refer to/watch this screencast: 
"http://vimcasts.org/episodes/creating-colorschemes-for-vim/"

## Vim Mappings and MapLeader:

Mappings help us assign shortcuts to execute long/complex commands.

### Setting a map:

- `:map <shortcut-characters> <commandtobereplacedbyshortcut>`

Ex: `:map ,rs :bundle exec rspec` will make sure to run ':bundle exec rspec' command upon seeing the ',rs' shortcut command.
In this case, We will see the expanded command in the bottom after pressing the shortcut - Then hit <ENTER> to run that command.

To automatically execute shortcut for a command, we need to add the ENTER key as well to the command:

- `:map ,rs :bundle exec rspec<CR>`   = The <CR> stands for Enter/Carriage Return key. The above comand gets executed automatically. (That is, we will not see the entire command appear at the bottom and we need not hit enter to execute it!)

### Executing map shortucts depending on MODE:

- `:map ....`   = Executes mapped shortcuts in Normal, Visual & Operator-pending(Not very important) modes.
- `:nmap ...`   = Executes mapped shortcuts in Normal mode.
- `:nmap ...`   = Executes mapped shortcuts in Normal mode.
- `:vmap ...`   = Executes mapped shortcuts in Visual mode.
- `:imap ...`   = Executes mapped shortcuts in Insert mode.
- `:omap ...`   = Executes mapped shortcuts in Operator-pending mode.... etc.

**IMPORTANT! EXAMPLE: AUTOCOMPLETION IN VIM**

- `:imap <Tab> <C-n>`      = Hitting tab in insert mode will open the context menu (Ctrl(C) followed by n).

The context menu will contain text options that will autocomplete the current text that we are typing.

### Key characters used in maps:

- `<Tab>`   = The Tab key.
- `<CR>`    = The Enter key.
- `<C-n>`   = C stands for Control key. So the rule is for holding control and pressing 'n'. (Similarly, we can have any character other than 'n'. Ex: <C-t>, <C-x>, <C-Tab>, etc ...)
- `<S-n>`   = C stands for Shift key. So the rule is for holding shift and pressing 'n'. (Similarly, we can have any character other than 'n'. Ex: <S-t>, <S-x>, <S-Tab>, etc ...)

### Recursive & Non-recursive Mapping:
- `:remap` is an option that makes mappings work **recursively**. By default it's on and it's better you leave it that way.
- `:map` and `:noremap` are recursive and non-recursive versions of the various mapping commands. 

What that means is that if you do:
```
:map j gg
:map Q j
:noremap W j
```

Then 'j' will be mapped to 'gg'. 'Q' will also be mapped to 'gg', because 'j' will be expanded for the recursive mapping. 
'W' will be mapped to 'j' (and not to gg) because 'j' will not be expanded for the non-recursive mapping.

For each of these sets of mappings (:map and :noremap), there is a mapping that works in Normal, Visual, Select and Operator modes: 

One that works in normal mode (:nmap and :nnoremap), 

One in visual mode (:vmap and :vnoremap) and so on ... !

### For help/information on mappings:
- `:help map`     = Map is actually a function expecting an expression and a string. This function gets executed upon ':map' command.

### Create and use a Map Leader for Mappings:

VIM MAPLEADER: Choose a key you don't need as a prefix for the map shortcuts: `,` is a good leader key.

- `:let mapleader = ","`

### More Information on Mappings and Mapleader:

- http://learnvimscriptthehardway.stevelosh.com/chapters/06.html
- https://hashrocket.com/blog/posts/8-great-vim-mappings


## Some Useful Vim Plugins:

- Auto Pairs: Insert or delete brackets, parentheses and quotes in pairs. (Source: https://github.com/jiangmiao/auto-pairs)

- Vim Git Gutter: Shows the git diffs (mod/addtn/deltn) in the Left gutter. (Source: https://github.com/airblade/vim-gitgutter)

*Important* (https://github.com/hukl/Smyck-Color-Scheme/) 

Use this vim & terminal color combo:

- Awesome Vim Theme: https://github.com/hukl/Smyck-Color-Scheme/blob/master/smyck.vim (Copy to ~/.vim/colors folder & update to 'colorscheme smyck' in ~/.vimrc)

- Same theme for Bash Terminal (Good combo with the above vim theme):
https://github.com/hukl/Smyck-Color-Scheme/blob/master/Smyck.terminal (Open terminal preferences and check for import option and import the 'Smyck.terminal' file)

- CTRL-P for fuzzy file search: https://github.com/ctrlpvim/ctrlp.vim

- Nerdtree file explorer: https://github.com/scrooloose/nerdtree

- Vim-airline (The awesome looking status bar for vim): https://codybonney.com/install-vim-airline-using-pathogen/

## Further Learning:

### Help with Basics:

- 'vimtutor' command on the Terminal
- ':help' (or) :help <cmd>' inside Vim.
- ':help options' - Help with the vimrc options or in-file settings. (List of options available to insert in the vimrc file).

### Excellent places to learn Vim tips (HOW-TOs):

- http://vimcasts.org/episodes
- https://code.tutsplus.com/articles/25-vim-tutorials-screencasts-and-resources--net-14631
- https://vimeo.com/user1690209

### Most Popular Vim Cheat Sheet:

- http://www.viemu.com/vi-vim-cheat-sheet.gif

### 10 Awesome color schemes:

- http://www.vimninjas.com/2012/08/26/10-vim-color-schemes-you-need-to-own

** THE END **
