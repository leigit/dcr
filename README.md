# Drupal Code Review (DCR) [![Circle CI](https://circleci.com/gh/alexdesignworks/dcr.svg?style=svg)](https://circleci.com/gh/alexdesignworks/dcr)

The idea behind DCR is driven by the following workflow:<br/>
Write code -> Format in IDE -> Code Review before Commit -> Commit

Usually, code formatting in IDE covers about 80% of cases, and the other 20% are left to pre-commit code review, but they are the hardest to find.

## Installation
###Global:
1. Pull all dependecies:<br/>`composer global require alexdesignworks/dcr`
2. Link and copy required files (composer does not let to execute scripts):<br/>`~/.console/vendor/bin/dcr install && ~/.profile`

Test of global build status: [![Circle CI](https://circleci.com/gh/alexdesignworks/dcr-global-demo.svg?style=svg)](https://circleci.com/gh/alexdesignworks/dcr-global-demo)

###Per-project (local):
1. Pull all dependecies:<br/>`composer require alexdesignworks/dcr`
2. Link and copy required files (composer does not let to execute scripts):<br/>`vendor/bin/dcr install && ~/.profile`

Test of local build status: [![Circle CI](https://circleci.com/gh/alexdesignworks/dcr-demo.svg?style=svg)](https://circleci.com/gh/alexdesignworks/dcr-demo)

## Roadmap
* <del>Show success and fail status messages</del> DONE
* <del>Allow DCR sniffs</del> DONE
* <del>Allow custom sniffs</del> DONE
* Use JSLint and Rhino
* Limit files scan to N failed files
* Scan only files changed in current branch comparing to a `main` branch.

## FAQ
### What is it?
DCR (Drupal Code Review) is a command-line utility to check that produced code follows Drupal coding standards and best practices.

### More specifically
It is a shell script wrapper around PHP_CodeSniffer and JSLint with Drupal-related code sniffs.

### Why should I use it?
Simply put - convenience. Run code review by only one command `dcr`. 

### Why does it exist?
1. **Ease of install:** `composer require alexdesignworks/dcr`
2. **Less false-positives:** Drupal-specific excpetions allow to have clean DCR output.
3. **Simple call:** no need to call phpcs with tones of confusing parameters. Just use `dcr`.
4. **Project-based configuration:** use `.dcr.yml` file to configure `dcr` for each project and make sure that your teammates are using exactly the same standards.

### But what about code inspection in IDE?
Code inspection in IDE distracts while writing code. Lets concentrate on writing code first and fixing formatting later!

### Why is it a separate tool?
There was a need in a dead-simple solution to review code using a single command, but also be flexible enough to handle project-based sniff rule customisations and pluggable into a CI pipeline.

DCR installs as a single composer dev dependency either into your project or globally.

DCR contains the following:

* PHP_CodeSniffer with Drupal, Drupal Practice sniffs.
* Additional DCR sniff with more specific Drupal rules that.
* Custom project-related sniff - very handy for any custom inclusions.
* JavaScript code review using JSLint.
* Colour CLI output - easy to spot issues.

### Can it automatically review code on commit?
Yes. Use it in git pre-commit hook.

### Can it be used as a part of automated build?
Yes. In fact, there is a [dcr-demo](https://github.com/alexdesignworks/dcr-demo) and [dcr-global-demo](https://github.com/alexdesignworks/dcr-global-demo) projects were setup to test `dcr` integration.

## Does it automatically fix code?
No. Not yet.
