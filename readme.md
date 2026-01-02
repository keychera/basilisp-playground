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