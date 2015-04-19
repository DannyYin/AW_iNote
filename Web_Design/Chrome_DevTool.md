### Element

Before **DevTool**, Web developer use `alert()` and early debugger while development. Now with DevTool, developer can edit page elements and styles in real time, debuge JavaScript and optimize with profilers.

Inside **Element Panel**, right side is **DOM** (Document Tree), you can edit the DOM in real time and drag the element inside the panel. Left side is the stylesheet, which display CSS rules for active elements. You can enable/disable properties, edit rules for pseudo-classes and link directly to CSS source. Use `Toggle Element State` button located at top-right side panel to show all element states. CSS source will show on the right side with corresponding `*.css` file.

### Source

All changes made previously are temporary. You can edit your source file directory in DevTool. (Modify app. source files, Export changes, and Track file version)

Saving file in **Source Panel** only save file changes in browser's storage not to the original file. In order to save to local disk, just save as to local disk and overwrite the original file.

### Console

Console interact with your App views and scripts. It can run JavaScript commands and view log output.

Detailed [Console API Reference](https://developer.chrome.com/devtools/docs/console-api) 

To examining Exceptions, exam the object inside **Console**.

NOTE: Helper methods like `$('#title)` blink short-cut even you are not using `jQuery` (`jQuery` will overwrite browser's blink).
NOTE+: `$0` store the most recent selected element, `$1` store the second last stored element, so and so fourth.

### Debugging

Debugger can be used to *pinpoint* the problem. 

**Paused on Exception** will pause the code where the exception occured.

**{}** will convert minimised version code become readable again.

**On Caught Exception**, tick the option to enable *On Caught Exception*.

Create code **Debugger Break Point** just like in regular IDE Environment. Excution controls (Step over, Step in, Step out, and Resume) are also similar to the regular IDE Environment. Mouse over to check the value of variable or create *watch expression* to observe the value. 

**Local Storage**, click the resources panel -> Local Storage.

### Network

**Network** provide resource info (size, type, etc.), server response details, timeline of network request. 

Hold <kbd>Shift</kbd> and click *Refresh* button to redownload every resources again, in order to avoid `304` error (Files cached by browser).

Two(2) ways to disable caches:

1. Incognito Mode (also disbale cookies)
2. Setting, click `Disable Cache` checkbox in Network Panel

The colors are for different color, **Blue** for HTML, **Orange** for JavaScript, **Green** for CSS, and **Purple** for images. *Initiator* is the one who calls for loading resource.

**Blue** line at end of timeline represent the DOM content-loaded event fired. (Triggered when browser is doen parsing HTML file, but still could be loading resources)

**Red** line indicates all resources are *done* downloading.

Click file name on the left side of panel to get more information about the request.

**Network Performance**, install `PageSpeed` extension, it downloads page and provide suggestions. (Google the suggetion for more details in order to improve your page performance)

NOTE: Introduce [Google Closure](https://developers.google.com/closure/)

**Removing Unneeded Requests** can help to inprove PageSpeed rating. 

Order for loading resources should be **CSS** > **Images** > **JavaScript**. Add `async` attribute in the `<script>` tag to make better performance, because the JavaScript only affect the behavior of the page.

**Serving Correctly Sized Images**, its about image optimisation and responsive image (Details covered in the **Responsive Image** note)

### Profiles

...

### Memory

...