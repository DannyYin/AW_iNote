# Website Performance Optimization

## Getting Up and Running

Before start, Google's [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) analyzes page and generates suggestions on how to make page faster.

### Why should care profile the site on mobile

Mobile phones are much more resource constrained (lower CPUs, less RAM and GPU memory, higher connection latencies, etc.).
Always try to profile and debug your site on mibile hardware to get a better and closer picture of how users will experience the site on handset.

#### Setup for mobile

Detailed text Instruction can be found [HERE](https://developer.chrome.com/devtools/docs/remote-debugging) for **Android**.

iOS WebKit Debug Proxy can be found [HERE](https://github.com/google/ios-webkit-debug-proxy).

NOTE: If you do not have a mobile device, you can emulating mobilde device with Chrome Canary. Detailed instruction is [HERE](https://developer.chrome.com/devtools/docs/device-mode).

NOTE+: Chrome Canary is the developer version of Chrome. It includes new and experimental features that haven't released yet.

## The Critical Rendering Path (CRP)

**CRP Working Process**

![CRP Process](http://dl.dropbox.com/u/1725146/Screen%20Shot%202015-04-19%20at%209.56.54%20AM.png)

Before the browser can render the page, it needs to construct the **DOM** and **CSSOM** tree.
Therefore, fast delivery of HTML and CSS is important.
The goal is to prioritize and display the content that relates to the primary action the user wants to take on a page.

Optimizing for performance is all about understanding what happens in intermediate steps between receiving the *HTML*, *CSS* and *JavaScript* bytes and the required processing to turn them into redered pixels.

![CRP](http://dl.dropbox.com/u/1725146/progressive-rendering.png)

**Bytes** -> **characters** -> **tokens** -> **nodes** -> **object model**

HTML markup is transformed into **DOM** (Document Object Model) and CSS markup is transfers into **CSSOM** (CSS Object Model).
They are two independent things.

NOTE: *Chrome DevTools Time-line* can capture and inspect the construction and processing costs of **DOM** and **CSSOM**.

### Critical Rendering Path Walk-through

Browser construct the **DOM** incrementally, and developer can take the advantage of it to speed up the rendering process.

#### DOM First

![HTML Tokenizing Work Process](http://dl.dropbox.com/u/1725146/full-process.png)

1. **Conversion** (Browser converts *raw* bytes into *characters* based on specified encoding)
1. **Tokenizing** (Browser converts *string* into *token*)
1. **Lexing** (Browser converts *token* into *objects* which define their properties and rules)
1. **DOM Construction**

**Final Output**

![Final DOM Output](http://dl.dropbox.com/u/1725146/dom-tree.png)

Learn more about [the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/) with Google's Web Fundation.

The **DOM** is the full parts presentation of the HTML markup.

#### CSSOM Second

![CSSOM Rendering Process](http://dl.dropbox.com/u/1725146/cssom-construction.png)

**Bytes** -> **characters** -> **tokens** -> **nodes** -> **CSSOM**

**CSSOM Output**

![CSSOM Output](http://dl.dropbox.com/u/1725146/cssom-tree.png)

When computing final styles set for object on page, browser stats with most general rule applicable to that *node* and then recursively refines the computed styles by applying more specific rules. (The rules "cascade down")

NOTE: Browser DOES provide a default set of styles, known as "user agent styles".

NOTE: `curl` is a tool to transfer data from or to a server, using one of the supported protocols (DICT, FILE, FTP, FTPS, GOPHER, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMTP, SMTPS,  TEL-NET and TFTP).
The command is designed to work without user interaction.

#### What's the Document Object Model?

[Original Post](http://www.w3.org/TR/DOM-Level-2-Core/introduction.html)

**DOM** is an application programming interface (API) for valid HTML and well-formed XML documents.
It defines the logical structure of documents and the way a document is accessed and manipulated. For example, XML presents data as documents, and the **DOM** may be used to manage this data.

With **DOM** programmer can build documents navigate their structure, and add, modify, or delete elements and content.

One important objective for **DOM** is to provide a standard programming interface that can be used in wide variety of environments and application.
It is designed to be used with any programming language.
It is based on an object structure that resembles the structure of the documents it *models* for instance.

```HTML
<TABLE>
<TBODY>
<TR>
<TD>Shady Grove</TD>
<TD>Aeolian</TD>
</TR>
<TR>
<TD>Over the River, Charlie</TD>
<TD>Dorian</TD>
</TR>
</TBODY>
</TABLE>
```

**Graphical Representation of the DOM of the example table**

![Graphical Representation](http://dl.dropbox.com/u/1725146/table.gif)

Each document contains zero or one 'doctype' node(s), one root element node, and zero or more comments or processing instructions.
The root element serves as the root of the element tree for the document.

The **DOM** is a logical model that may be implemented in any convenient manner. One important property of **DOM** structure models is structural isomorphism:
*if any two DOM implementations are used to create a representation of the same document, they will create the same stricture model, in accordance with the XML information Set*.

NOTE: **DOM** was chosen because it's an "Object Model" in the traditional object oriented design sense.
Documents are modeled using objects, and the model encompassed not only the strcture of a document, but also the behavior of a document and the objects of which it is composed.
For example, the `node`s in the diagram do not represent a data structure, they represent objects, which have functions and identity.

As an object model, the **DOM** identifies:

- The interfaces and object used to represent and manipulate a document
- The semantics of thses interfacs and objects, including both behavior and attribute.
- The relationship and collaorations among these interfaces and objects.

#### What the DOM is NOT

The following text provide a more precise understsanding of the **DOM** by distinguishing it from other systems that may seem to be like it.

- **DOM** is not a binary specification.
- **DOM** is not a way of persisting objects to XML or HTML. (It specifies how object may be represented in document. It specifies how XML and HTML documents are represented as objects so that they may be used in object oriented programs)
- **DOM** is not a set of data strcture. (It's an object model that specifies interfaces)
- **DOM** does not define what information in a document is relevant or how information in a document is structured. (It is an API to the information set)

### Fast Google Search Response

![Google Response Process](http://dl.dropbox.com/u/1725146/Screen%20Shot%202015-04-21%20at%208.46.49%20PM.png)

Many sites use a static header and then use JavaScript to fill in the custom bits, which allow them to serve the same header regardless the user status.

Important part is that the server does not have to wait to render the full response before returning it to the client. The sooner server can flush some data, the sooner the browser can start building the DOM, and discover the dispatch requests for other critical resources.

### Exploring Time-line Traces

PROTIO: In order to user the hard reload trick to capture the full trace, you have to load the page first, open Time-line in DevTools, start and stop recording, and then use the shortcuts to reload the page.

### Converting CSS to the CSSOM

CSS cannot be use partially and the child element will inherent the parent and hence cannot be use partially during page rendering process.

### Which Style Render Faster

The more specific the CSS rule is the more expensive it is during rendering process.

NOTE: Measure first and optimize second.

### Recalculating CSS Styles in DevTools

NOTE: Right click the time-line in order to save to load trace.

In **Recalculate Style** event browser convert CSS style in to CSSOM.

### The Render Tree

The render tree only capture the visible contents. The children nodes will be ignored if their parents is not visible.

### Layout

Calculating positions and dimensions. The percentage in CSS is percentage to the width set in the `<meta>` tag.

```
<meta name="viewport" content="width=device-width">
```

The width is always relative to its parent.

NOTE: If there is NO viewport meta provided, the browser will use the default viewport width which is *980px* for large screen optimization.

ALWAYS SET VIEWPORT!

NOTE: <em> and <span> are inline elements. Unless they are converted to display: block or display: inline-block, their widths will be determined by the text they contain.

### Analyzing Layout in DevTools

Layout can be triggered by device orientation change on mobile, a window resize, or any other action that modifies the content of the DOM - e.g. adding or removing content from the DOM tree, toggling CSSOM properties on a node, and so on!

## Optimizing the CRP

...

