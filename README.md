# Jobs prompt: Shell prompt component for displaying background jobs

If you frequently use the `Ctrl + Z` shortcut in Bash or Zsh shells to send a
process to the background, it can be useful to see the list of jobs
continuously without having to query it with the `jobs` command.

[See the screencast on YouTube](https://youtu.be/EtlsE53qG9U)

## Installation

Download the `bin/jobs_prompt` script and place it somewhere on your PATH or use
[Basher](https://github.com/basherpm/basher).

Get the source code, report bugs, open pull requests, or just star because
you didn't know that you need it:

* https://github.com/bimlas/bash-jobs-prompt

## Usage

At the desired part of the prompt, call the script by sending the output of `jobs` to it.

```
PS1+='$(jobs | jobs_prompt)'
```

If you also want to add surrounding text that only appears if there are jobs,
you can use the following solution.

```
PS1+='$('
PS1+='jobs'
PS1+='| jobs_prompt'
PS1+='| sed "s/.\\+/\\n Jobs: & \\n/"'
PS1+=')'
```

## Configuration

You can change the color of the prompt sections with environment variables.

* `JOBS_PROMPT_RED`
  * The color of stopped / suspended processes
* `JOBS_PROMPT_GREEN`
  * The color of running processes
* `JOBS_PROMPT_TEXT`
  * The color of job numbers
