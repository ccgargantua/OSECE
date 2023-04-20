# Contributing to OSECE

The following is information regarding contributing to OSECE.

### Accepted Contributions

**OSECE IS NOT CURRENTLY OPEN TO CONTRIBUTIONS**

---

### How to contribute

**Contribution process**

  1. Fork the repo
  2. Create a new local branch with a relevant name
  3. Make your changes
  4. Push your changes to your remote branch in the
  forked repo
  5. Open a pull request

**Guidelines**

  1. Circuit diagrams must be created in either LTSpice
  or NI Multisim.
  2. Any code must be tested first and placed into a markdown
  code block. For C code, use GCC with the following flags:
  `-Wall -Wextra -std=c11`
  3. Texts must be in a well-formatted markdown file. File
  names must start with a three-digit identifier if the texts
  in a certain module build off of each other sequentially.
  File names must be relevant to the text within. If there are
  multiple words in the file name, use snake case.
  4. Images used in texts must be placed in a subdirectory with
  the same name within the `OSECE/images/` directory.
  5. Modules must be subdirectories contained in `OSECE/osece/`
  directory and contain a relevant name. If it is multiple
  words, use snake case.
  6. Modules must contain a `README.md` that contains a general overview of the
  module, the content contained within, and a list of
  pre-requisite knowledge required.

---

### The approval process

After opening a pull request, the changes must be reviewed and
approved by at least 2/4 of the OSECE collaborators. If both
members agree that the changes are necessary and meet our
standards, we will merge your changes.
