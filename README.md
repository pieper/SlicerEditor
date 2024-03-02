
# SlicerEditor

Experiment to embed an editor in Slicer.

Currently uses ths [monaco]("https://github.com/microsoft/monaco-editor") editor (the one used in VSCode) in a qSlicerWebWidget.


To try this in Slicer, paste the following in the python console:
```
editor = slicer.qSlicerWebWidget()
editor.size = qt.QSize(900, 750)
editor.url = "https://pieper.github.io/SlicerEditor"
editor.show()
```

Press the slicer icon to run the code.

# Notes
* Running code from web pages in Slicer is a possible security issue,
so you must approve with the dialog.  Use care when accessing untrusted
pages using the qSlicerWebWidget infrastructure.
* This is just a skeleton prototype as a proof of concept. See [this dicussion](https://discourse.slicer.org/t/support-python-text-highlighting-in-text-module/34511) for more ideas about how this can be improved to be useful.
