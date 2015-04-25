# The Critical Rendering Path

NOTE: Web Performance Optimization is a prerequirement for this note.

60 Hz -> 60 FPS (Frame Per Second)

### CRP Revisit

How browser making a frame?

1. Browser sending request to the server (GET/ HTTP/1.0).
1. Server sending back `HTML`
1. Browser parse the HTML and generate nodes (DOM), indicate by **Pharse HTML** in Chrome DevTools.
1.