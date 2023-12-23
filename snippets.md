- [Snippets](#snippets)
  - [▫️ **BASH**](#️-bash)
    - [Zipping](#zipping)
  - [▫️ **OpenAI API**](#️-openai-api)
  - [▫️ **GIT**](#️-git)
    - [ghh CLI](#ghh-cli)
    - [Commands](#commands)
  - [▫️ **NUMPY**](#️-numpy)
    - [RESHAPING](#reshaping)
    - [BROADCASTING](#broadcasting)
  - [tmux](#tmux)
    - [Pane Management](#pane-management)
    - [Window Management](#window-management)
    - [Session Management](#session-management)
    - [Resizing Panes](#resizing-panes)
    - [Miscellaneous](#miscellaneous)

# Snippets

---
---

## ▫️ **BASH**

### Zipping

* General unzip: `unzip path/to/your/file.zip`
* Unzip to specific path: `unzip path/to/your/file.zip -d path/to/destination/folder`

---

## ▫️ **OpenAI API**

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

## ▫️ **GIT**

### ghh CLI

* Create new repo: `gh repo create ___ --private`

### Commands

* Remove local already-pushed file from remote:

  ```git
  git rm --cached FILE_OR_DIR_NAME
  git commit -m "Removed FILE_OR_DIR_NAME from repository"
  git push origin master
  ```

* get git remote origin's url: `git config --get remote.origin.url`
* force-update local repo state to match remote branch (**overwrites** -- stash): `git reset --hard --force`
* undo most recent _local_ commit (to staging): `git reset --soft HEAD~1`
* undo most recent _local_ commit (to unstaged): `git reset --mixed HEAD~1`
* delete file from remote and local:

  ```git
  git rm file_to_delete
  git commit -m "removed file_to_delete"
  git push origin master
  ```

* delete folder from remote and local:

  ```git
  git rm -r folder_to_delete
  git commit -m "removed folder_to_delete"
  git push origin master
  ```

* delete file from remote only:

  ```git
  git rm --cached file_to_delete
  git commit -m "removed file_to_delete"
  git push origin master
  ```

* (same patter for folder)
* list all files on remote master:
  
  ```git
  git fetch origin
  git ls-tree -r master --name-only
  ```

* add and commit all changes: `git commit -am "commit message"`
* force-remove untracked files: `git clean -f`
* force-remove untracked directories: `git clean -fd`
* force-remove subdirectory's sub-git repo:
  
  ```git
  cd subdirectory
  sudo rm -rf .git
  ```

---

## ▫️ **NUMPY**

### RESHAPING

* The reshape() function takes a single tuple argument that specifies the new shape of the array
  * Used frequently to _add_ a dimension of when for libs like sklearn and keras (to the END of the shape tuple -- i.e. **right-padding with 1s**)
* In the case of reshaping 1-D `(m,)` --> 2-D `(m,1)`:
  * Tuple would be the shape of the array as the first dimension (data.shape[0]) and 1 for the second dimension:
    * `data.shape == (m_old, )` (e.g. `(1000,)`)
    * `data = data.reshape( (m_old, n_new)  )`
      * `data.shape == (m_old, n_new)` (e.g. `(1000, 1)`)

### BROADCASTING

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

## tmux

### Pane Management

* Split Pane Horizontally: `Ctrl + b, then "`
* Split Pane Vertically: `Ctrl + b, then %`
* Switch to x Pane: `Ctrl + b, then x-arrow`
* Close Current Pane: `Ctrl + b, then x (then press y to confirm)`
* (Switch to Next Pane: `Ctrl + b, then o)`

### Window Management

* Create New Window: `Ctrl + b, then c`
* Switch to Next Window: `Ctrl + b, then n`
* Switch to Previous Window: `Ctrl + b, then p`
* List Windows: `Ctrl + b, then w`
* Rename Current Window: `Ctrl + b, then ,`

### Session Management

* Detach from Session: `Ctrl + b, then d`
* List Sessions: `tmux ls (outside of tmux)`
* Attach to a Session: `tmux attach-session -t [session-name]`

### Resizing Panes

* Resize Pane Up: `Ctrl + b:resize-pane -U 10`
* Resize Pane Down: `Ctrl + b:resize-pane -D 10`
* Resize Pane Left: `Ctrl + b:resize-pane -L 10`
* Resize Pane Right: `Ctrl + b:resize-pane -R 10`

### Miscellaneous

* Scroll Mode: `Ctrl + b, then [ (use arrow keys to scroll, q to exit scroll mode)`
* Copy Mode: `Ctrl + b, then [ (enter copy mode for text selection)`
* Paste from Buffer: `Ctrl + b, then ]`

---
