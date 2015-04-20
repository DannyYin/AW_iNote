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

### Line Numbers

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

NOTE: `@` in Goto Anything Palette is also known as **Goto Symbol**.



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
