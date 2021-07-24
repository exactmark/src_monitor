
The need: Automatically build and run tests while developing.

The plan: Create a module to watch a given path, and if any files in the subset of file types is changed (either from touch or hash), run the commands in the command list with results being piped to related log files.

Required structures:

- Per file
    - Parent - this should allow me to handle files as a nested tree rather than absolute paths for each
    - TouchDateTime - last time this file was touched
    - Hash - The previous file hash

- Config items
    - Folder root
    - Command list items

- Command list item
    - command to run
    - related log location for pipe

Flow:

1. Read the config file
2. Do initial scan creating the file list
3. On timer, check for file changes
    - if any files have changed, run each command in the config's command list

