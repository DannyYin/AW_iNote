### General 

<kbd>Command</kbd> + <kbd>=</kbd> : increase font size

<kbd>Command</kbd> + <kbd>-</kbd> : decrease font size

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

### Command Pelette

<kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> : Search everything you need there.

### Goto Anything...

<kbd>Command</kbd> + <kbd>P</kbd> : Type the file name to show the target file.

### Goto Symbol...

<kbd>Command</kbd> + <kbd>R</kbd> : Find class, function. You can see all available symbol 
there.

Combine Goto Anything with Goto Symbol with Command + P with @ 
Target Symbol.

### Install Plugins Without Package Control

Put the plugin into Packages folder.

### Package Control

[Package Control](https://packagecontrol.io/docs/usage)

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

### Learn Emmet 

...

### Create File Quickly - AdvancedNewFile

<kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>N</kbd> : Create new file.

Read more in `README.md`

### Sublime Linter

[Sublime Linter](http://www.sublimelinter.com/en/latest/index.html)

### Code Snippet Management with Gists

Using GitHub Gist.

### CONTINUE HERE

[HERE](https://code.tutsplus.com/courses/perfect-workflow-in-sublime-text-2/lessons/docblockr)
