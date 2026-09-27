# [introduction To Databases](https://www.freecodecamp.org/learn/relational-databases-v9/)

w/ freeCodeCamp.org

&nbsp;

## Code Editors & IDEs

### Code Editor

A _code editor_ is **any application that allows you to edit code files**.

- **Visual Studio Code**
  - A **lightweight**, **_open-source_ code editor** by Microsoft that supports a wide range of programming languages and provides features like **debugging**, **syntax highlighting**, and **version control** through _extensions_.
    - Highly **extensible** and can work with **many project types and languages**.
      - Live Server
      - ESLint
      - Prettier
      - Auto Rename Tag
      - Better Comments
      - Code Spell Checker
      - Error Lens
      - Pretty TypeScript Errors
      - Indent Rainbow
      - Colorize

  `Note`: You can download the PDF of _keyboard shortcuts_ for your specific operating system by going to the `Help` menu on the top left corner, and clicking `Keyboard Shortcuts Reference`.

- **Sublime Text**
  - For a **fast** and **versatile editing experience**, _Sublime Text_ offers _a sleek interface_ and support for a wide range of programming languages through customizable **syntax highlighting** and **plugins**.

- **Notepad++**
  - Windows users can also use _Notepad++_, **a free**, **open-source text and source code editor** that offers **syntax highlighting**, **code folding**, and a range of **plugins** to enhance productivity and customization.

&nbsp;

#### _Cloud-based_ Editor

A _cloud-based_ editor is an online tool that allows users to **write**, **edit**, and **manage** code or text directly **through a web browser** without needing to install software locally.

- **Replit**
  - An _online platform_ that provides a **collaborative environment** for coding, allowing users to **write**, **run**, and **share code** in various programming languages directly from a web browser.

- **GitHub Codespaces**
  - A _cloud-based development environment_ that provides instant access to **a fully configured code editor** and **development tools** directly from GitHub, enabling seamless coding and collaboration.

- **StackBlitz**
  - Another _cloud-based editor_ that runs directly in the browser and lets you **build**, **test**, and **share** web projects without any local setup.

&nbsp;

### IDE

An _IDE_, or _integrated development environment_, is **a full application that allows you to compile**, **run**, and **debug** your code while you edit it.

- **Visual Studio**
  - An _integrated development environment_ by Microsoft that provides **a comprehensive suite of tools for building**, **debugging**, and **deploying** applications across various platforms.

- **Xcode**
  - An _integrated development environment_ by Apple designed for **creating**, **coding**, and **debugging** applications for _macOS_, _iOS_, _watchOS_, and _tvOS_.

- **Android Studio**
  - Developed by Google, is an _integrated development environment_ specifically designed for **building**, **debugging**, and **testing** _Android_ applications.

&nbsp;

_Code editors_ focus primarily on the **text contents** of the _file_, whereas the _IDEs_ expose various **tools to manage your code**.

&nbsp;

## Bash Fundamentals

### The Command Line

it is **a basic text input interface** which allows a user to enter "_commands_", usually in the form of a series of _characters_, and submit or execute them, usually by pressing the `Enter` key.

- Command line interfaces usually exist within a terminal.

### Terminal

it is **a special application that offers a command line interface** to perform _system-level_ commands beyond the basic _read/write_ operations.

- Windows
  - Microsoft Terminal

- Mac
  - Terminal
  - iTerm2

- Linux
  - gnome-terminal
  - ptyxis
  - yakuake

### Terminal Emulators

These are applications that **wrap a basic terminal interface** to offer **additional features** and **functionalities**.

- kitty
- terminator
- tmux (multiplexer)
- Ghostty

### Shell

it is the software that **wraps the command line**, **interprets the inputs as commands**, and **returns the output**.

- Powershell
- bash
- zsh
- fish

&nbsp;

`Note`: All these terms are used interchangibily.)

&nbsp;

## Basic Keyboard Shortcuts

For _Linux_ and _macOS_, which can both trace their roots to **Unix**, many of these shortcuts will be the same.

But for _Windows_, there will be some differences.

&nbsp;

### Arrow Keys

These two keys (_Up Arrow key_ & _Down Arrow key_) allow you to quickly **cycle through the commands you've previously run**.

- To run the **last executed command** once again, use two exclamation points (`!!`).

- To run a specfic _command_ you've executed in the past, type `history`, and run the number associated with that paticular _command_ along with one exclamation point (`!`).
  - `!6`
  - `!9`
  - `!69`

&nbsp;

### The `Tab` Key

The `Tab` key can be used to **fill in the rest of the suggestion**, quickly populating your command line with the full syntax.

However, suggestions will vary from shell to shell.

- if you're using `zsh`, you can install `zsh-autosuggestions` for better suggestions.

&nbsp;

### `Control + L`

To clear the terminal.

You can also type `clear` to clear the terminal.

- if you're using _command prompt_ for some reason, you can type `cls` to clear the screen.

&nbsp;

### `Control + C`

This will **terminate execution** of the currently running _command_ and create a _new prompt_.

- For _PowerShell_ users, `Control + C` is also used to copy text - and will only work to terminate a process when the context is not ambiguous (such as when there is no text selected to copy).

`NOTE`: inside _linux_ terminals, you must use `Control + Shift + C` to **copy text** from the terminal to the clipboard. And `Control + Shift + V` to paste.

&nbsp;

### `Control + Z` & `fg` (\*nix based terminals only)

There may be times when you need to _multitask_, allowing a process or command to run in the background while you work on another.

Pressing `Control + Z` places the current process in a background task and returns you to the command line, where you can continue your work.

When you need to shift focus back to the background task, you can use `fg` to restore it.

- However, in some operating systems like _fedora_, it tends to **suspend** the process insted.

&nbsp;

For more shortcuts, read the documentation for your particular OS & application.

&nbsp;

## Basic Bash Commands

Bash stands for **Bourne Again SHell**, and is arguably the _most common shell_ you will encounter in _Unix-like_ environments.

- `pwd`: Prints the **current working directory** to the terminal.
  - The "working directory" refers to the directory the terminal is currently _pointed at_.

- `cd`: Allows you to **change directories**.

  ```bash
  cd ./to-another-folder
  ```

  - The single dot(`.`) represents the current directory.

  - You can use the double-dot (`..`) syntax to **move up to the parent** directory.

  - You can use dash (`-`) to **go back** to the previous directory.

  - You can specify an **absolute path**, prefixed with a forward slash (`/`)
    - Or a **relative path** with _no prefix_.

  - `~`: Represents the **home** folder.

- `ls`: **Lists the contents** of your _current working directory_.
  - `-a` Flag: To see **hidden files**.

    ```bash
    ls -a
    ```

  - `-l` Flag: To see **file permissions**.

    ```bash
    ls -l
    ```

    Or,

    ```bash
    ls -la
    ```

- `cat`: To **view the contents** of a file.

  ```bash
  cat Readme.md
  ```

- `mkdir`: **Creates a new directory**/folder.

  ```bash
  mkdir directory-one
  ```

- `touch`: **Creates a new file**.

  ```bash
  touch Readme.md
  ```

- `mv`: Allows you to **move a file _or_ directory** (_rename_).
  - it takes the _old file name_ followed by the _new file name_.

    ```bash
    mv redme.md Readme.md
    ```

    Or,

    ```bash
    mv old-folder to-the-new-folder
    ```

- `cp`: To **copy a file _or_ directory** to a new location.
  - it takes the _file name_ followed by _a path to the new location_.

    ```bash
    cp this-file ./to-this-folder
    ```

    Or,

    ```bash
    cp this-file ../to-a-parent-folder
    ```

  - `-r` flag: Sometimes, in order to _copy a directory_, you'll need to pass this flag.

- `rm`: Allows you to **remove a file** (_delete_).

  ```bash
  rm Readme.md
  ```

  - `-r` Flag: **Removes a directory**.

    ```bash
    rm -r this-folder
    ```

  - `-f` Flag: Sometimes a _file_ or _folder_ _might be protected_, and you'll need to include this flag in order to remove a _file_ or _directory_.

    `NOTE`: Use `rm -fr` **very carefully!!**

- `echo`: Bash equivalent of a `console.log()` _or_ the `print()` function.
  - it takes a _string argument_, wrapped in quotes, and prints it to the terminal.

  - `>` Symbol: it allows you to _specify a filename_ to **create or overwrite with the new string**.

    ```bash
    echo "i, existed." > readme.md
    ```

    - `>>` Symbol: it will **append to the file**.

- `man`: To see the **manual** for nearly any command.

  ```bash
  man whoami
  ```

  - Press `q` to quit.

- `--help` Flag: For **quick help** with any command.

  ```bash
  whoami --help
  ```

&nbsp;

### Command Options and Flags

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;
