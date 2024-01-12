# Code Snippets

??? note "Code Snippets - Contents"
    - [GIT](snippets.md#git)
        - [Commands](snippets.md#commands)
        - [ghh CLI](snippets.md#ghh-cli)
    - [SHELL](snippets.md#shell)
        - [Shortcuts (zsh)](snippets.md#shortcuts-zsh)
        - [Core Commands](snippets.md#core-commands)
        - [Chaining Commands](snippets.md#chaining-commands)
        - [Explanation of `grep`](snippets.md#explanation-of-grep)
        - [Piping Commands](snippets.md#piping-commands)
        - [Help](snippets.md#help)
    - [PYTHON](snippets.md#python)
        - [OpenAI API](snippets.md#openai-api)
        - [Token Counts](snippets.md#token-counts)
        - [numpy](snippets.md#numpy)
        - [Reshaping](snippets.md#reshaping)
        - [Broadcasting](snippets.md#broadcasting)
    - [RARELY USED](snippets.md#rarely-used)
        - [tmux](snippets.md#tmux)
        - [Pane Management](snippets.md#pane-management)
        - [Window Management](snippets.md#window-management)
        - [Session Management](snippets.md#session-management)
        - [Resizing Panes](snippets.md#resizing-panes)
        - [Miscellaneous](snippets.md#miscellaneous)

---

## GIT

### Commands

| Command | Description |
| :------ | :----------- |
| `git remote add origin git@github.com:USERNAME/REPO_NAME.git` | Add remote origin (when not set) |
| `git remote set-url origin git@github.com:USERNAME/REPO_NAME.git` | Set remote origin (overwrite existing) |
| `git rm --cached FILE_OR_DIR_NAME`<br>`git commit -m "Removed FILE_OR_DIR_NAME from repository"`<br>`git push origin master` | Remove local already-pushed file from remote. |
| `git config --get remote.origin.url` | Get git remote origin's URL. |
| `git diff --cached origin/main` | Compare committed (pre-push) local changes to remote (all contents).<br>This opens the `less` editor.<br>`n`: Next change<br>`N`: Previous change<br>`spacebar`: Pagedown<br>`b`: Pageup<br>`q`: Quit<br>`?`: Help |
| `git diff --cached origin/main --name-only` | Compare committed (pre-push) local changes to remote (filenames only). |
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

## postgres (Mac)

### Table of Most Common Commands

| Action | Command |
| --- | --- |
| Start postgres and log into main local database | `psql -U [username] -d [database]` |
| List all tables in this db | `\dt` |
| List all tables in all dbs | `\dt *.*` |
| List all databases | `\l` |
| Navigate to a different database | `\c [database]` |
| List all schemas in this db | `\dn` |
| Create a new database | `CREATE DATABASE [database];` |
| Create a new schema | `CREATE SCHEMA [schema];` |
| Create a new table | `CREATE TABLE [table] ( [column] [datatype] [constraints] );` |
| Delete a database | `DROP DATABASE [database];` |
| Export a database | `pg_dump -U [username] [database] > [filename].sql` |
| Import a database | `psql -U [username] -d [database] -f [filename].sql` |
| Exit psql | `\q` |

---

## PYTHON

### New OpenAI API (v 1.7.1)

#### API Key

`export OPENAI_API_KEY='...'`

OR

save .env file in root directory with: `OPENAI_API_KEY=abc123` (be sure to add .env to .gitignore)


#### Models

| Model | Description | Context window | Training data |
| --- | --- | --- | --- |
| gpt-4-1106-preview | **GPT-4 Turbo** The latest GPT-4 model with improved instruction following, JSON mode, reproducible outputs, parallel function calling, and more. Returns a maximum of 4,096 output tokens. This preview model is not yet suited for production traffic. [Learn more](https://openai.com/blog/new-models-and-developer-products-announced-at-devday). | 128,000 tokens | Up to Apr 2023 |
| gpt-4-vision-preview | **GPT-4 Turbo with vision** Ability to understand images, in addition to all other GPT-4 Turbo capabilties. Returns a maximum of 4,096 output tokens. This is a preview model version and not suited yet for production traffic. [Dev Day](https://openai.com/blog/new-models-and-developer-products-announced-at-devday). | 128,000 tokens | Up to Apr 2023 |
| gpt-4 | Currently points to `gpt-4-0613`. See [continuous model upgrades](https://platform.openai.com/docs/models/continuous-model-upgrades). | 8,192 tokens | Up to Sep 2021 |
| gpt-4-32k | Currently points to `gpt-4-32k-0613`. See [continuous model upgrades](https://platform.openai.com/docs/models/continuous-model-upgrades). | 32,768 tokens | Up to Sep 2021 |
| gpt-4-0613 | Snapshot of `gpt-4` from June 13th 2023 with improved function calling support. | 8,192 tokens | Up to Sep 2021 |
| gpt-4-32k-0613 | Snapshot of `gpt-4-32k` from June 13th 2023 with improved function calling support. | 32,768 tokens | Up to Sep 2021 |

#### Chat Completions

**THIS IS DEPRECATED**:

```python
import openai
openai.api_key = os.getenv("OPENAI_API_KEY")

MODEL = "gpt-4" # more expensive now
response = openai.ChatCompletion.create(
  ...
)

# ChatCompletion response object:
# {
#   "id": "chatcmpl-7UkgnSDzlevZxiy0YjZcLYdUMz5yZ",
#   "object": "chat.completion",
#   "created": 1687563669,
#   "model": "gpt-4",
#   "choices": [
#     {
#       "index": 0,
#       "message": {
#         "role": "assistant",
#         "content": "\n\nHello there, how may I assist you today?",
#       },
#       "finish_reason": "stop"
#     }
#   ],
#   "usage": {
#     "prompt_tokens": 39,
#     "completion_tokens": 3,
#     "total_tokens": 42
#   }
# }
```

**THIS IS THE NEW WAY**:

```python
from openai import OpenAI
client = OpenAI() # defaults to looking for OPENAI_API_KEY or .env file

MODEL = "gpt-4-turbo" # cheaper & smarter
completion = client.chat.completions.create(
    model=MODEL,
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},

        {"role": "user", "content": "Knock knock."},
        {"role": "assistant", "content": "Who's there?"},
        
        {"role": "user", "content": "Orange."},
    ],
    temperature=0,
)

# Chat completion object:
# {
#   "id": "chatcmpl-123",
#   "object": "chat.completion",
#   "created": 1677652288,
#   "model": "gpt-4-turbo",
#   "system_fingerprint": "fp_44709d6fcb",
#   "choices": [{
#     "index": 0,
#     "message": {
#       "role": "assistant",
#       "content": "Orange who?"
#     },
#     "logprobs": null,
#     "finish_reason": "stop"
#   }],
#   "usage": {
#     "prompt_tokens": 9,
#     "completion_tokens": 12,
#     "total_tokens": 21
#   }
# }

print(completion.choices[0].message.content)
# 'Orange who?'
```

**Chat Completions Request body fields:**

![Chat Completions Request Args (messages)](img/chatcompletions.png)
![Chat Completions Request Args (response_format)](img/chatcompletions2.png)
![Chat Completions Request Args (functions)](img/chatcompletions3.png)
![Chat Completions Request Args (model, tokens)](img/chatcompletions4.png)

Response object fields:

- `id`: the ID of the request
- `object`: the type of object returned (e.g., `chat.completion`)
- `created`: the timestamp of the request
- `model`: the full name of the model used to generate the response
- `usage`: the number of tokens used to generate the replies, counting prompt, completion, and total
- `choices`: a list of completion objects (only one, unless you set `n` greater than 1)
    - `message`: the message object generated by the model, with `role` and `content`
    - `finish_reason`: the reason the model stopped generating text (either `stop`, or `length` if `max_tokens` limit was reached)
    - `index`: the index of the completion in the list of choices

```python
# Example with system prompt & few-shot learning:

# Faked few-shot conversation to prime the model into translating business jargon into simpler speech
# (OPTIONAL: Use the `name` parameter in the example messages -- so the model won't refer back to them & can differentiate between participants of the same role
completion = client.chat.completions.create(
    model=MODEL,
    messages=[
        {"role": "system", "content": "You are a helpful, pattern-following assistant that translates corporate jargon into plain English."},
        
        {"role": "system", "name":"example_user", "content": "New synergies will help drive top-line growth."},
        {"role": "system", "name": "example_assistant", "content": "Things working well together will increase revenue."},
        
        {"role": "system", "name":"example_user", "content": "Let's circle back when we have more bandwidth to touch base on opportunities for increased leverage."},
        {"role": "system", "name": "example_assistant", "content": "Let's talk later when we're less busy about how to do better."},
        
        {"role": "user", "content": "This late pivot means we don't have time to boil the ocean for the client deliverable."},
    ],
    temperature=0,
)

print(response["choices"][0]["message"]["content"])
# This sudden change in plans means we don't have enough time to do everything for the client's project.
```

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

Function to track tokens:

```python
def num_tokens_from_messages(messages, model="gpt-3.5-turbo-0613"):
  """Returns the number of tokens used by a list of messages."""
  try:
      encoding = tiktoken.encoding_for_model(model)
  except KeyError:
      encoding = tiktoken.get_encoding("cl100k_base")
  if model == "gpt-3.5-turbo-0613":  # note: future models may deviate from this
      num_tokens = 0
      for message in messages:
          num_tokens += 4  # every message follows <im_start>{role/name}\n{content}<im_end>\n
          for key, value in message.items():
              num_tokens += len(encoding.encode(value))
              if key == "name":  # if there's a name, the role is omitted
                  num_tokens += -1  # role is always required and always 1 token
      num_tokens += 2  # every reply is primed with <im_start>assistant
      return num_tokens
  else:
      raise NotImplementedError(f"""num_tokens_from_messages() is not presently implemented for model {model}.
      See https://github.com/openai/openai-python/blob/main/chatml.md for information on how messages are converted to tokens.""")
```

#### JSON Mode

A common way to use Chat Completions is to instruct the model to always return a JSON object that makes sense for your use case, by specifying this in the system message. While this does work in some cases, occasionally the models may generate output that does not parse to valid JSON objects.

To prevent these errors and improve model performance, when calling `gpt-4-1106-preview` or `gpt-3.5-turbo-1106`, you can set [response\_format](https://platform.openai.com/docs/api-reference/chat/create#chat-create-response_format) to `{ "type": "json_object" }` to enable JSON mode. When JSON mode is enabled, the model is constrained to only generate strings that parse into valid JSON object.

Important notes:

- When using JSON mode, **always** instruct the model to produce JSON via some message in the conversation, for example via your system message. If you don't include an explicit instruction to generate JSON, the model may generate an unending stream of whitespace and the request may run continually until it reaches the token limit. To help ensure you don't forget, the API will throw an error if the string `"JSON"` does not appear somewhere in the context.
- The JSON in the message the model returns may be partial (i.e. cut off) if `finish_reason` is `length`, which indicates the generation exceeded `max_tokens` or the conversation exceeded the token limit. To guard against this, check `finish_reason` before parsing the response.
- JSON mode will not guarantee the output matches any specific schema, only that it is valid and parses without errors.

```python
from openai import OpenAI
client = OpenAI()

response = client.chat.completions.create(
  model="gpt-3.5-turbo-1106",
  response_format={ "type": "json_object" },
  messages=[
    {"role": "system", "content": "You are a helpful assistant designed to output JSON."},
    {"role": "user", "content": "Who won the world series in 2020?"}
  ]
)
print(response.choices[0].message.content)
```

In this example, the response includes a JSON object that looks something like the following:

`"content": "{\"winner\": \"Los Angeles Dodgers\"}"`

**Note that JSON mode is always enabled when the model is generating arguments as part of function calling.**

#### Streaming Chat Completions

```python
from openai import OpenAI
client = OpenAI()

completion = client.chat.completions.create(
  model="gpt-4-1106-preview",
  messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Hello!"}
  ],
  stream=True
)

for chunk in completion:
  print(chunk.choices[0].delta)


# ..........
# {
#     "id": "chatcmpl-123",
#     "object": "chat.completion.chunk",
#     "created": 1694268190,
#     "model": "gpt-3.5-turbo-0613",
#     "system_fingerprint": "fp_44709d6fcb",
#     "choices": [
#         {
#             "index": 0,
#             "delta": {
#                 "content": " today"
#             },
#             "logprobs": null,
#             "finish_reason": null
#         }
#     ]
# }

# {
#     "id": "chatcmpl-123",
#     "object": "chat.completion.chunk",
#     "created": 1694268190,
#     "model": "gpt-3.5-turbo-0613",
#     "system_fingerprint": "fp_44709d6fcb",
#     "choices": [
#         {
#             "index": 0,
#             "delta": {
#                 "content": "?"
#             },
#             "logprobs": null,
#             "finish_reason": null
#         }
#     ]
# }

# {
#     "id": "chatcmpl-123",
#     "object": "chat.completion.chunk",
#     "created": 1694268190,
#     "model": "gpt-3.5-turbo-0613",
#     "system_fingerprint": "fp_44709d6fcb",
#     "choices": [
#         {
#             "index": 0,
#             "delta": {},
#             "logprobs": null,
#             "finish_reason": "stop" <---- stop here
#         }
#     ]
# }
```

#### Function Calling

```python
from openai import OpenAI
client = OpenAI()

tools = [
  {
    "type": "function",
    "function": {
      "name": "get_current_weather",
      "description": "Get the current weather in a given location",
      "parameters": {
        "type": "object",
        "properties": {
          "location": {
            "type": "string",
            "description": "The city and state, e.g. San Francisco, CA",
          },
          "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]},
        },
        "required": ["location"],
      },
    }
  }
]
messages = [{"role": "user", "content": "What's the weather like in Boston today?"}]
completion = client.chat.completions.create(
  model="gpt-4-1106-preview",
  messages=messages,
  tools=tools,
  tool_choice="auto"
)

print(completion)

# {
#   "id": "chatcmpl-abc123",
#   "object": "chat.completion",
#   "created": 1699896916,
#   "model": "gpt-3.5-turbo-0613",
#   "choices": [
#     {
#       "index": 0,
#       "message": {
#         "role": "assistant",
#         "content": null,
#         "tool_calls": [
#           {
#             "id": "call_abc123",
#             "type": "function",
#             "function": {
#               "name": "get_current_weather",
#               "arguments": "{\n\"location\": \"Boston, MA\"\n}"
#             }
#           }
#         ]
#       },
#       "logprobs": null,
#       "finish_reason": "tool_calls"
#     }
#   ],
#   "usage": {
#     "prompt_tokens": 82,
#     "completion_tokens": 17,
#     "total_tokens": 99
#   }
# }

```

#### Image Input Chat Completions

```python
from openai import OpenAI

client = OpenAI()

response = client.chat.completions.create(
    model="gpt-4-vision-preview",
    messages=[
        {
            "role": "user",
            "content": [
                {"type": "text", "text": "What’s in this image?"},
                {
                    "type": "image_url",
                    "image_url": "https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Gfp-wisconsin-madison-the-nature-boardwalk.jpg/2560px-Gfp-wisconsin-madison-the-nature-boardwalk.jpg",
                },
            ],
        }
    ],
    max_tokens=300,
)

print(response.choices[0])
```

##### Multiple Images


The Chat Completions API is capable of taking in and processing multiple image inputs in both base64 encoded format or as an image URL. The model will process each image and use the information from all of them to answer the question.

```python
from openai import OpenAI

client = OpenAI()
response = client.chat.completions.create(
  model="gpt-4-vision-preview",
  messages=[
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "What are in these images? Is there any difference between them?",
        },
        {
          "type": "image_url",
          "image_url": {
            "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Gfp-wisconsin-madison-the-nature-boardwalk.jpg/2560px-Gfp-wisconsin-madison-the-nature-boardwalk.jpg",
          },
        },
        {
          "type": "image_url",
          "image_url": {
            "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Gfp-wisconsin-madison-the-nature-boardwalk.jpg/2560px-Gfp-wisconsin-madison-the-nature-boardwalk.jpg",
          },
        },
      ],
    }
  ],
  max_tokens=300,
)
print(response.choices[0])
```

Here the model is shown two copies of the same image and can answer questions about both or each of the images independently.

##### Low or high fidelity image understanding

By controlling the `detail` parameter, which has three options, `low`, `high`, or `auto`, you have control over how the model processes the image and generates its textual understanding. By default, the model will use the `auto` setting which will look at the image input size and decide if it should use the `low` or `high` setting.

- `low` will disable the “high res” model. The model will receive a low-res 512px x 512px version of the image, and represent the image with a budget of 65 tokens. This allows the API to return faster responses and consume fewer input tokens for use cases that do not require high detail.
- `high` will enable “high res” mode, which first allows the model to see the low res image and then creates detailed crops of input images as 512px squares based on the input image size. Each of the detailed crops uses twice the token budget (65 tokens) for a total of 129 tokens.
```python
from openai import OpenAI

client = OpenAI()

response = client.chat.completions.create(
  model="gpt-4-vision-preview",
  messages=[
    {
      "role": "user",
      "content": [
        {"type": "text", "text": "What’s in this image?"},
        {
          "type": "image_url",
          "image_url": {
            "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Gfp-wisconsin-madison-the-nature-boardwalk.jpg/2560px-Gfp-wisconsin-madison-the-nature-boardwalk.jpg",
            "detail": "high"
          },
        },
      ],
    }
  ],
  max_tokens=300,
)

print(response.choices[0].message.content)
```

#### Error Handling

```python
import openai
from openai import OpenAI
client = OpenAI()

try:
  #Make your OpenAI API request here
  response = client.completions.create(
    prompt="Hello world",
    model="gpt-3.5-turbo-instruct"
  )
except openai.APIError as e:
  #Handle API error here, e.g. retry or log
  print(f"OpenAI API returned an API Error: {e}")
  pass
except openai.APIConnectionError as e:
  #Handle connection error here
  print(f"Failed to connect to OpenAI API: {e}")
  pass
except openai.RateLimitError as e:
  #Handle rate limit error (we recommend using exponential backoff)
  print(f"OpenAI API request exceeded rate limit: {e}")
  pass
```

#### Rate limits

Rate limits are restrictions that our API imposes on the number of times a user or client can access our services within a specified period of time.

[Rate Limits](img/Rate%20limits.png)

How do these rate limits work?

Rate limits are measured in five ways: **RPM** (requests per minute), **RPD** (requests per day), **TPM** (tokens per minute), **TPD** (tokens per day), and **IPM** (images per minute). Rate limits can be hit across any of the options depending on what occurs first. For example, you might send 20 requests with only 100 tokens to the ChatCompletions endpoint and that would fill your limit (if your RPM was 20), even if you did not send 150k tokens (if your TPM limit was 150k) within those 20 requests.

Other important things worth noting:

- Rate limits are imposed at the [organization level](https://platform.openai.com/docs/guides/production-best-practices), not user level.
- Rate limits vary by the [model](https://platform.openai.com/docs/models/models) being used.
- Limits are also placed on the total amount an organization can spend on the API each month. These are also known as "usage limits".


(See [here](https://platform.openai.com/docs/guides/rate-limits/error-mitigation) for more info on rate limit & error mitigation strategies.)

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
