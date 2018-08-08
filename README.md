# menu
Keyboard based menu utility

## Example
```
menu$ ./menu

 _ __ ___   ___ _ __  _   _
| '_ ` _ \ / _ \ '_ \| | | |
| | | | | |  __/ | | | |_| |
|_| |_| |_|\___|_| |_|\__,_|

To exit:               C-c C-c
To go up a menu level: q

[h] - housekeeping -->
[o] - openwrt -->
[u] - ubuntu -->
> ^C^C
```
## Feature Requirements
- The menu program should:
  - parse a filesystem tree for the menu structure
  - allow a menu item to be selected, which will:
      - execute a script; or
      - enter a subdirectory.
  - find and use the 'm' directory in a subdirectory, if specified as
    an argument, as the top level of the menu tree,
  - if not specified, use the 'm' directory in the current working
    directory as the top level of the menu tree

- Menu scripts should:
  - be easy (and possibly automatically) created.
  - be standard linux scripts/programs (eg. binaries and
    executables).

- Scripts should expect that:
  - The working directory is where the menu program is called.

- Example script naming scheme example
  - 1-menu-item-name
  - 2-another-script
  - 3-submenu/

- Exceptions/Special Cases
  - To quit the program, use CTRL-C, CTRL-C (or C-c C-c)
  - The key 'q' is used the exit the current subdirectory/menu and go
    up a level.

### Suggested features
#### Basic Features

With a working menu program, the following features and extensions
have been suggested:

- Follow symbolic links to other menu trees.

- Detect if a menu changes, and re-read if required. This will be
  useful if machine learning is used to assist in selecting menu
  items.

- Log of command history, menu selection and output logs. This could
  be useful for training of a machine learning system

- Read additional environment variables for menu scripts, per
  sub-menu. (eg. Add an 'env' file which gets read to set environment
  variables before a script is run.)

#### Machine Learning / AI Prediction

Have an machine learning process running in the background which can
learn the most common modes of operation, and then assist the use
navigating the menu system.

For  development could be broken up as:
- Level 1: From previous usage/training, make a prediction about the next
  option to be selected.

- Level 2: Time based predictions, depending on time of day and
  selection delay.

## Architecture

- Setup
- Main Loop
  - parse directory
  - display menu
  - get input
  - run script, go up a menu level ot quit

