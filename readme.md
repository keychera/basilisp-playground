# basilisp playground

trying uv

https://github.com/astral-sh/uv


```
uv tool install basilisp
```


blender python api

https://docs.blender.org/api/current/index.html



keybinding for repl goodness

```json
[
    {
        "key": "f3",
        "when": "resourceExtname == .lpy",
        "command": "calva.runCustomREPLCommand",
        "args": "(do (println \"undo!\") (ops/undo))"
    },
    {
        "key": "f4",
        "when": "resourceExtname == .lpy",
        "command": "calva.runCustomREPLCommand",
        "args": "(do (println \"redo!\") (ops/redo))"
    }
]
```

## note

- issue in requiring other files. in hello.lpy, running (ops/undo) from repl cause the following:
    - workaround: just repl'ing in one file for now.

```
Traceback (most recent call last):
  File "...basilisp-playground\src\ops.lpy", line 5, in undo
    (try (.undo bpy.ops/ed)
          ^^^^^^^^^^^^^^^
NameError: name 'bpy_rvMfRT' is not defined

During handling of the above exception, another exception occurred:
...
```
