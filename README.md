
**This was an experiment that has been migrated to its official home in SlicerMorph: https://github.com/SlicerMorph/SlicerEditor/tree/main**

# SlicerEditor


Experiments to embed an editor in Slicer.

Currently uses ths [monaco]("https://github.com/microsoft/monaco-editor") editor (the one used in VSCode) in a qSlicerWebWidget.


To try this in Slicer, use a Slicer preview newer than March 5, 2024 (where [this feature](https://github.com/Slicer/Slicer/pull/7624/files) is available).

## Hosted online from CDN example

Then paste the following in the python console:
```
editor = slicer.qSlicerWebWidget()
editor.size = qt.QSize(900, 750)
editor.url = "https://pieper.github.io/SlicerEditor"
editor.show()
```

![image](https://github.com/pieper/SlicerEditor/assets/126077/fa556ee4-bf19-4102-a0f8-8edad05e45d8)

You will get autocomplete suggestions based on the current Slicer session.

Press the slicer icon to run the code.

# Notes
* Running code from web pages in Slicer is a possible security issue,
so you must approve with the dialog.  Use care when accessing untrusted
pages using the qSlicerWebWidget infrastructure.

![image](https://github.com/pieper/SlicerEditor/assets/126077/3e1d44d7-90ac-4660-910f-d537bc6e76e3)

## Offline examples

These examples do not need an internet connection.

For these, download https://github.com/pieper/SlicerEditor/releases/download/prototype/offline.tar.gz

Open the archive and update the URL parameters below to point to your extracted file.

Note: the archive is monaco build tree and has not been optimized for size.

### Hosted from Slicer WebServer example

```

DOCROOT = "/Users/pieper/slicer/latest/SlicerEditor/offline".encode()
PORT = 9916
import WebServer
try:
    logic.stop()
except NameError:
    pass
logMessage = WebServer.WebServerLogic.defaultLogMessage
logic = WebServer.WebServerLogic(port=PORT, logMessage=logMessage)
logic.docroot = DOCROOT
logic.requestHandlers = []
logic.addDefaultRequestHandlers(enableSlicer=False, enableStaticPages=True)
logic.start()

editor = slicer.qSlicerWebWidget()
editor.size = qt.QSize(900, 750)
#editor.url = f"http://localhost:{PORT}".encode()
editor.show()
```

### Read directly from file example

```
URL = "file:///Users/pieper/slicer/latest/SlicerEditor/offline/index.html"

editor = slicer.qSlicerWebWidget()
editor.size = qt.QSize(900, 750)
editor.url = URL
editor.show()
```

* This is just a skeleton prototype as a proof of concept. See [this dicussion](https://discourse.slicer.org/t/support-python-text-highlighting-in-text-module/34511) for more ideas about how this can be improved to be useful.
