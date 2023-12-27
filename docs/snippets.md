# Code Snippets

---

## GIT

### Commands

| Command | Description |
| :------ | :----------- |
| `git rm --cached FILE_OR_DIR_NAME`<br>`git commit -m "Removed FILE_OR_DIR_NAME from repository"`<br>`git push origin master` | Remove local already-pushed file from remote. |
| `git config --get remote.origin.url` | Get git remote origin's URL. |
| `git reset --hard --force` | Force-update local repo state to match remote branch (**overwrites** -- stash). |
| `git reset --soft HEAD~1` | Undo most recent _local_ commit (to staging). |
| `git reset --mixed HEAD~1` | Undo most recent _local_ commit (to unstaged). |
| `git rm file_to_delete`<br>`git commit -m "removed file_to_delete"`<br>`git push origin master` | Delete file from remote and local. |
| `git rm -r folder_to_delete`<br>`git commit -m "removed folder_to_delete"`<br>`git push origin master` | Delete folder from remote and local. |
| `git rm --cached file_to_delete`<br>`git commit -m "removed file_to_delete"`<br>`git push origin master` | Delete file from remote only. |
| `git fetch origin`<br>`git ls-tree -r master --name-only` | List all files on remote master. |
| `git commit -am "commit message"` | Add and commit all changes. |
| `git clean -f` | Force-remove untracked files. |
| `git clean -fd` | Force-remove untracked directories. |
| `cd subdirectory`<br>`sudo rm -rf .git` | Force-remove subdirectory's sub-git repo. |
| `git branch new-branch`<br>`git checkout new-branch`<br>[make changes]<br>`git add -A`<br>`git commit -m "commit message"`<br>`git push origin new-branch`<br>`git branch -d new-branch` | Create new branch, make changes, push, and delete branch locally. |

### ghh CLI

| Command | Description |
| :------ | :----------- |
| `gh repo create ___ --private` | Create new repo (private). |
| `gh repo clone ___` | Clone repo. |
| `gh repo view --web` | Open repo in browser. |
| `gh repo delete ___` | Delete repo. |
| `gh repo list` | List all repos. |
| `gh repo rename old-name new-name` | Rename repo. |
| `gh repo transfer ___ new-owner` | Transfer repo to new owner. |
| `gh repo fork ___` | Fork repo. |
| `gh repo fork --clone ___` | Fork repo and clone locally. |
| `gh repo fork --clone ___ --remote` | Fork repo and clone locally with remote origin. |
| `gh repo fork --clone ___ --remote --remote-name=upstream` | Fork repo and clone locally with remote origin and upstream. |

---

## SHELL

### Shortcuts (zsh)
| Key/Command | Description |
| --- | --- |
| `Ctrl + A` | Go to the beginning of the line you are currently typing on. This also works for most text input fields system wide. |
| `Ctrl + E` | Go to the end of the line you are currently typing on. This also works for most text input fields system wide. |
| `Ctrl + L` | Clears the Screen |
| `Cmd + K` | Clears the Screen |
| `Ctrl + U` | Cut everything backwards to beginning of line |
| `Ctrl + K` | Cut everything forward to end of line |
| `Ctrl + W` | Cut one word backwards using white space as delimiter |
| `Ctrl + Y` | Paste whatever was cut by the last cut command |
| `Ctrl + H` | Same as backspace |
| `Ctrl + C` | Kill whatever you are running. Also clears everything on current line |
| `Ctrl + D` | Exit the current shell when no process is running, or send EOF to a the running process |
| `Ctrl + Z` | Puts whatever you are running into a suspended background process. fg restores it |
| `Ctrl + T` | Swap the last two characters before the cursor |
| `Ctrl + _` | Undo the last command. |
| `Ctrl + F` | Move cursor one character forward |
| `Ctrl + B` | Move cursor one character backward |
| `Option + →` | Move cursor one word forward |
| `Option + ←` | Move cursor one word backward |
| `Esc + T` | Move cursor one word backward |
| `Esc + Backspace` | Swap the last two words before the cursor |
| `Tab` | Cut one word backwards using none alphabetic characters as delimiters |

### Core Commands

| Command | Description |
| --- | --- |
| `cd [folder]` | Change directory e.g. cd Documents |
| `cd` | Home directory |
| `cd /` | Root of drive |
| `cd -` | Previous directory |
| `ls` | Short listing |
| `ls -l` | Long listing |
| `ls -a` | Listing including hidden files |
| `ls -lh` | Long listing with human-readable file sizes |
| `ls -R` | Entire content of folder recursively |
| `sudo [command]` | Run command with the security privileges of the superuser (Super User DO) |
| `open [file]` | Opens a file (as if you double-clicked it) |
| `top` | Displays active processes. Press q to quit |
| `nano [file]` | Opens the file using the nano editor |
| `vim [file]` | Opens the file using the vim editor |
| `clear` | Clears the screen |
| `reset` | Resets the terminal display |
| `unzip path/to/your/file.zip` | General unzip |
| `unzip path/to/your/file.zip -d path/to/destination/folder` | Unzip to specific path |
| `zip -r compressed_filename.zip foldername` | General zip |

### Chaining Commands
| Command | Description |
| --- | --- |
| [command-a]; [command-b] | Run command A and then B, regardless of the success of A |
| [command-a] && [command-b] | Run command B if A succeeded |
| [command-a] \|\| [command-b] | Run command B if A failed |
| [command-a] & | Run command A in the background |

### Explanation of `grep` 
* `grep` is a command-line utility for searching plain-text data sets for lines that match a regular expression.
* `grep` searches the named input FILEs (or standard input if no files are named, or the file name - is given) for lines containing a match to the given PATTERN.
* By default, `grep` prints the matching lines.
* `egrep` or `grep -E` is the same as `grep`, but uses extended regular expressions instead of basic regular expressions.
  * Example: `egrep 'foo|bar'` is the same as `grep -E 'foo|bar'`
* `fgrep` or `grep -F` is the same as `grep`, but interprets PATTERN as a list of fixed strings (instead of regular expressions), separated by newlines, any of which is to be matched.
  * This is different from normal `grep` which interprets PATTERN as a regular expression.
  * Example: `fgrep 'foo'` is the same as `grep -F 'foo'`
  * Example: `fgrep -f file1 file2` is the same as `grep -F -f file1 file2`
* To obtain the opposite effect of `grep`, use the `-v` or `--invert-match` option.
  * Example: `grep -v 'foo'` will match all lines that do not contain the string 'foo'
* Output grep results to a file using the `>` operator.
  * Example: `grep 'foo' file.txt > output.txt`

### Piping Commands
| Command | Description |
| --- | --- |
| find [dir] -name [search_pattern] | Search for files, e.g., find /Users -name "file.txt" |
| grep [search_pattern] [file] | Search for all lines that contain the pattern, e.g., grep "Tom" file.txt |
| grep -r [search_pattern] [dir] | Recursively search in all files in the specified directory for all lines that contain the pattern |
| grep -v [search_pattern] [file] | Search for all lines that do NOT contain the pattern |
| grep -i [search_pattern] [file] | Search for all lines that contain the case-insensitive pattern |
| mdfind [search_pattern] | Spotlight search for files (names, content, other metadata), e.g., mdfind skateboard |
| mdfind -onlyin [dir] -name [pattern] | Spotlight search for files named like pattern in the given directory |

### Help
| Command | Description |
| --- | --- |
| [command] -h | Offers help |
| [command] -help | Offers help |
| info [command] | Offers help |
| man [command] | Show the help manual for [command] |
| whatis [command] | Gives a one-line description of [command] |
| apropos [search-pattern] | Searches for command with keywords in description |

---

## PYTHON

### OpenAI API

#### Token Counts

* Context window equivalents:
  * 1 token --> 4 characters
  * 128,000 tokens --> 512,000 characters
  * Natural Language:
    * 6 characters per English word on average (5 char + 1 space)
    * 512,000 characters / 6 characters per word ≈ 85,333 words
    * 85,333 words / 250 words per page using 12pt Times New Roman ≈ 341 double-spaced pages (170 single-spaced pages)
    * **So 128,000 tokens is roughly equivalent to 170 single-spaced pages of text**
  * Code:
    * 50 characters per line on average
    * 512,000 characters / 50 characters per line ≈ 10,240 lines of code
    * **So 128,000 tokens is roughly equivalent to 10,240 lines of code**

---

### numpy

#### Reshaping

* The reshape() function takes a single tuple argument that specifies the new shape of the array
  * Used frequently to _add_ a dimension of when for libs like sklearn and keras (to the END of the shape tuple -- i.e. **right-padding with 1s**)
* In the case of reshaping 1-D `(m,)` --> 2-D `(m,1)`:
  * Tuple would be the shape of the array as the first dimension (data.shape[0]) and 1 for the second dimension:
    * `data.shape == (m_old, )` (e.g. `(1000,)`)
    * `data = data.reshape( (m_old, n_new)  )`
      * `data.shape == (m_old, n_new)` (e.g. `(1000, 1)`)

#### Broadcasting

In formal LinAlg, arithmetic can only be performed when:  

* the shape of each dimension in the arrays are equal (even for dotproduct - though not matmul)
  
However, in ML, we often want to add **A** `(m,n)` to **v** `(,n)`.  
NumPy enables this by _broadcasting_ the vector to the shape of the matrix.  
Specifically np (**which considers vectors as (n,) since it is row-oriented**) effectively:

1. **Left-pads with 1s** the dimensions of the smaller array
2. **Right-to-left compares** the dimensions of the two arrays and ensures either
  a. The dimensions are equal **OR**
  b. At least one of the dimensions is 1
3. If all dimensions pass, np **replicates** (_broadcast_) the smaller array along the dim(s) where it is 1 to match the shape of the larger array.

**NOTE**: Broadcasting is not a copy operation. It is a view of the original array with the same data. This means that if you modify a broadcasted array, it modifies the original array.  

So for example:  

* 1-D vs. 2-D
  * LOOKS like comparing:  
    * A.shape -- (2,3)  
    * b.shape -- (3,)  
  * ACTUALLY np is comparing:  
    * A.shape -- (2,3)  
    * b.shape -- (1,3)  
* 2-D vs. scalar  
  * LOOKS like comparing:  
    * A.shape -- (2,3)  
    * b.shape -- (1,)  
  * ACTUALLY np is comparing:  
    * A.shape -- (2,3)  
    * b.shape -- (1,1)

---

## RARELY USED

### tmux

#### Pane Management

* Split Pane Horizontally: `Ctrl + b, then "`
* Split Pane Vertically: `Ctrl + b, then %`
* Switch to x Pane: `Ctrl + b, then x-arrow`
* Close Current Pane: `Ctrl + b, then x (then press y to confirm)`
* (Switch to Next Pane: `Ctrl + b, then o)`

#### Window Management

* Create New Window: `Ctrl + b, then c`
* Switch to Next Window: `Ctrl + b, then n`
* Switch to Previous Window: `Ctrl + b, then p`
* List Windows: `Ctrl + b, then w`
* Rename Current Window: `Ctrl + b, then ,`

#### Session Management

* Detach from Session: `Ctrl + b, then d`
* List Sessions: `tmux ls (outside of tmux)`
* Attach to a Session: `tmux attach-session -t [session-name]`

#### Resizing Panes

* Resize Pane Up: `Ctrl + b:resize-pane -U 10`
* Resize Pane Down: `Ctrl + b:resize-pane -D 10`
* Resize Pane Left: `Ctrl + b:resize-pane -L 10`
* Resize Pane Right: `Ctrl + b:resize-pane -R 10`

#### Miscellaneous

* Scroll Mode: `Ctrl + b, then [ (use arrow keys to scroll, q to exit scroll mode)`
* Copy Mode: `Ctrl + b, then [ (enter copy mode for text selection)`
* Paste from Buffer: `Ctrl + b, then ]`

---
