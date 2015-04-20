# Sublime Text

## Getting Started

NOTE: This note is from the perspective of a Mac user.

Sublime Text supports addons/plugins/extensions called *packages* that extend the native functionality of the editor.

Beside installing packages using [**Package Control**](https://packagecontrol.io/) created by *Will Bond**. User can add repository using **Command Palette**, Sublime will attempt to install the package for you.

<kbd>Command</kbd> + <kbd>=</kbd> : increase font size

<kbd>Command</kbd> + <kbd>-</kbd> : decrease font size

## Command Palette

> It's always faster and more savvy to use keyboard shortchuts or the commands menu.
> --- Sublime Text Power User

<kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>,

Generally, you can search everything you need there.

### Goto Anything...

<kbd>Command</kbd> + <kbd>P</kbd>

Use it to navigate to any file, line or symbol within your current projects or open files. <kbd>ESC</kbd> close the palette or press the combination again.

#### Files

<kbd>Command</kbd> + <kbd>P</kbd> presents you a list of files, folders, projects you have open. File preview is underneath the panel box. The file path is shown under the file name.

#### Line Numbers

Start query with `:` followed by the line number allows to jump to a specific line number within a file.

<kbd>Ctrl</kbd> + <kbd>G</kbd>

Bring up the **Goto Anything Palette** and pre-populate it with `:`.

#### Fuzzy Search

It is a way of searching through documents for an approximate string of text. Use `#` to enable fuzzy search in **Goto Anything Palette**.

Example: For search `jQuery`, open **Goto Anything Palette** and type `#jq`.

NOTE: Fuzzy search also work  in the command palette.

#### Code & Text Blocks

To navigate through code and text blocks, by opening **Goto Anything Palette** and typing `@`, then you can use fuzzy search to filter list for specific functions, classes, or blocks of text.

<kbd>Command</kbd> + <kbd>R</kbd>

Bring up the **Goto Anything Palette** and pre-populate it with `@`.

In JavaScript you see a list of function, in CSS you see all selector classes and IDs and in Markdown you see sections of content.

In Sublime Text 3 has introduced the ability to find symbol across entire project and open docuemtns.

NOTE: `@` in Goto Anything Palette is also known as **Goto Symbol**.

#### Chaining Commands

The above features are more powerful when used together.

Example: Find function named `runCommand()` in `plugin.py` file inside project folder.

**Goto Anything Palette** -> `plug@rc` will find the target for you.

#### Excluding Files & Folders From Search

Files or folders you do not want to see in **Goto Anything Palette**. (Like, compiled JavaScript from CoffeeScript, compiled CSS from SASS)

Perferences -> Settings -> User, define `binary_file_patterns`.

```
// Ignore files
"binary_file_patterns": [".DS_Store", ".gitignore", "*.psd"]
// Ignore folders
"binary_file_patterns": ["node_modules/", "vendor/", "tmp/"]
```

NOTE: `file_exclude_patterns` and `folder_exclude_patterns` properties can exclude file and folder from Goto Anything Palette. They also remove those files and folders from sidebar.

#### Changing Syntax

New tab is not knowing what language you are typing, unless you have the file or manually set syntax highlight. Set the syntax at bottom righthand corner.

Using fuzzy search with combination of Command Palette. `sscss` -> `Set Syntax: CSS`.

#### Keyboard Shortcuts

When you have trouble to remember keyboard shortcuts you can utilise the Command Palette.

#### Snippets

Snippets should have keyboard shortcut associated with them. Use `snip` to filter installed snippets.

## Editor Settings and Customization

### Settings Files

Sublime Text has no GUI settings. It has settings files (JSON file). They are located inside Sublime Text packages folder.

Every customisation settings can be found in `Settings - Default`, it is a file only used as a reference.

NOTE: Reading through the `Settings - Default` file to get an idea of what change are possible to enhance the workflow.

#### *.sublime-settings Files

Most customisations are done in `Preferences.sublime-settings`, `Preferences` -> `Settings - User`.

<kbd>Command</kbd> + <kbd>,</kbd>

Types of Settings files and the editor references them in this order:

1. Default Settings (NEVER edit this file)
1. `Packages/Default/Preferences.sublime-settings`
1. Plantform-Specific Settings (For developer jump between OS)
1. User Settings (Most Customization done here)
1. `Packages/User/Perferences.sublime-settings`
1. Syntax-specific Default Settings (do NOT edit this)
1. `Packages/<syntax>/<syntax>.sublime-settings`
1. Syntax-specific User Settings
1. `Packages/User/<syntax>.sublime-settings`

#### Syntax/Language Specific Settings

Example, use space in JavaScript and use hard tab in Markdown. Using above reference order and create a new fill named `Markdown.sublime-settings` in side `/Packages/User` folder and put the following text.

```
{
	"translate_tabs_to_space": false
}
```

#### Settings Files JSON Gotchas

1. Using "double quotes" when defining both keys and string values. (Single quotes are not valid JSON)
1. Each key-value pair requires a common between them.

**Sample**:

```
{
 "setting_name" : true,
 "another_setting" : 12,
 "font_face": "inconsolata"
}
```

#### .sublime-keymap Files

Keymap files work similary to the settings hierarchy noted above. Detailed information on setting up shortcuts will be coverd later in this note.

### Syncing Your Settings

Two popular ways to do this is using **Git** or **Dropbox** (Prefered becuase its passively and automatically).

Only need to sync the `/User` folder which contains `Package-Control.sublime-settings` the file that tells Package Control which packages should be installed.

Syncing entire `/User` make sure the following user preferences get moved over:

1. Master setting file - `Preferences.sublime-settings`
1. Language specific settings files - `<syntax>.sublime-settings`
1. Custome snippets
1. Custome build tasks
1. SFTP server information
1. Other package specific information and settings

### Tabs, Spaces & Indentation

#### Specifying Tabs Or Spaces

Sublime use 4 size tab characters by default. To use space add below:

```
"translate_tabs_to_spaces": true,
"tab_size": 2
```

#### Converting From Tabs -> Space Or Space -> Tabs

To convert entire document fomr tabs to spaces.

1. Open file
1. Open Command Palette
1. Type `space` or `tabs`
1. Find `Indentation: Convert to Spaces` or `Tabs`
1. Hit enter

#### Detacting Indentation

Not every project share tab or space preferences by default. Sublime detect that tabs or spaces used for indentation. Using code below to turn it off.

```
"detect_indentation": false
```

#### Detect Settings with Editor Config Package

[**EditorConfig**](http://editorconfig.org/) is a package which can help to bring some sanity to project-specific formatting nuances. Include a `.editorconfig` file in the root of project directory.

When **Editor Config** package is installed, it detect this file and update Sublime settings to reflect the project's preferences.

#### Paste And Indent

Instead of using <kbd>Command</kbd> + <kbd>v</kbd> to past.

<kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>v</kbd>

Automcatically indent the past code block and switch it to the current use of tabs or spaces.

Remapped key combos to past and indent by default using code below

`Preferences` -> `Key Binding - User`

```
{ "keys": ["super+v"], "command": "paste_and_indent" },
{ "keys": ["super+shift+v"], "command": "paste" }
```

### Fonts and Type Sizing

Pg. 35...

***

# Recommendation and Questions

Suggestions

1. pg. 20 command palette short-cut is Super + Shift + P, NOT Super + P that's Goto Anything.

2. Images about using `@` in pg. 21 is confusing. You should put them after Code & Text Blocks.

3. pg.25, Subtitle 3.2 Changing Syntax and the Subsubtitle content does not closely releated. It's probably good to merge 3.2 with 3.1.

Questions

1. In pg. 20, how to go to next match when using `#` fuzzy search. about. It is not mentioned in the book.

2. pg. 32, how to create symbolic link?

***

# Legacy NOTE

### Column Selection

*Using the Mouse*

<kbd>Option</kbd> + Left Mouse :

*Using the Keyboard*

<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Up</kbd> : Add previous line
<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Down</kbd> : Add next line

### Multiple Selection with the Keyboard

*Splitting the Selection into Lines*

<kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>L</kbd>

*Quick Add Next*

<kbd>Command</kbd> + <kbd>D</kbd> : Add next selected word

*Find All*

<kbd>Ctrl</kbd> + <kbd>Command</kbd> + <kbd>G</kbd>

*Single Selection*

Escape : To go from multiple selections to a single selection.

### Auto Complete

*Manually Showing Completions*

<kbd>Ctrl</kbd> + <kbd>Sapce</kbd> : Show the completion popup.

*Commit on Tab*

By setting the `auto_complete_commit_on_tab` setting to true, enter
will insert a newline, and tab will commit the current completion.
There are other benefits, too: because Sublime Text knows there is
no ambiguity, it will show a more curated list of completions, with
the one you want more likely to be in first place.

### Tab Completion

Tab Completion completing words by pressing the Tab key.

Tp insert a tab, press Shift + Tab.

### Distraction Free Mode

View/Enter Distruction Free Mode menu.

### Vintage Mode

Remove "Vintage" inside `"ignored_packages": ["Vintage"]`.

### Create First Snippet

Create snippet for differnet languages and save the snippet file
into **User** folder and with file extension `.sublime-snippet` (
Important).

*Sample*

```
<snippet>
	<content>
		<!--Break Point using ${1}-->
		<!--With default value ${1:DefaultVal}-->
		<![CDATA[
			Hello, ${1:this} is a ${2:snippet}.
		]]>
	</content>
	<!-- Optional: Set a tabTrigger to define how to trigger the
	snippet -->
	<tabTrigger>hello</tabTrigger>
	<!-- Optional: Set a scope to limit where the snippet will
	trigger -->
	<!-- <scope>source.python</scope> -->
</snippet>
```

### Download Snippet using Package Control

...

### Create File Quickly - AdvancedNewFile

<kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>N</kbd> : Create new file.

Read more in `README.md`

### Code Snippet Management with Gists

Using GitHub Gist.

### CONTINUE HERE

[HERE](https://code.tutsplus.com/courses/perfect-workflow-in-sublime-text-2/lessons/docblockr)