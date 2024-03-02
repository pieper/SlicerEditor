
# SlicerEditor

Experiment to embed an editor in Slicer.

Currently uses ths [monaco]("https://github.com/microsoft/monaco-editor") editor (the one used in VSCode) in a SlicerWebWidget.


To try this in Slicer, paste the following in the python console:
```
editor = slicer.qSlicerWebWidget()
editor.size = qt.QSize(900, 750)
editor.url = "https://pieper.github.io/SlicerEditor"
editor.show()
```
