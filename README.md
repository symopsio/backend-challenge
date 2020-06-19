# Sym Backend Challenge

Thanks for taking the time to check out our backend engineering challenge! Today, you'll be building a command-line tool called `msr`. Please implement your CLI in Python, and ensure that, once installed (with a standard `pip install`), it can be called simply by typing `msr` at a shell prompt.

## Background

You've been tasked with putting together a CLI that performs various measurements on remote web pages. We'll call this CLI `msr`. There will be several subcommands to `msr`, each of which might take some arguments.

## Tests

We've provided a script ([`test.sh`](https://github.com/symopsio/backend-challenge/blob/master/test.sh)) that you can run to test your implementation.

Note that the tests should not take a long time to run. If your implementation takes more than 30 or so seconds, you should consider making some of your serial requests parallel.

## Implementation

### Version

The first subcommand to implement is `version`. Calling `msr version` should print a [semver](https://semver.org/) string to STDOUT.

### Register

`msr register` should take one argument, a URL. It should validate this URL, and return with a non-zero exit code if the URL is invalid. If the URL is valid, it should add the URL to an internal, persistent registry.

Feel free to use a file to back this registry, although proper XDG conventions (e.g. `XDG_CONFIG_HOME`) should be followed.

### Measure

`msr measure` takes no arguments, and should return a pretty-printed table of all of the URLs in the registry, along with the size (in bytes) of the body received by making a GET request to that URL.

### Race

`msr race` takes no arguments, and should return a pretty-printed table of all the domains found in the URLs in the registry, along with the average page load time for the URLs of that domain.

### Blast

`test.sh` includes one last testing method that is intended to see how your implementation holds up when the registry has a bunch of URLs in it. `blast` will register all the URLs in the pre-seeded [`blast.txt`](blast.txt) file, and then calls `race`.

## Submitting

You should have received an email from Sym with a link to upload your submission. If you haven't, please let us know!
