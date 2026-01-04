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

- issue in requiring other files. in hello.lpy, requiring from repl cause the following:
    - workaround: just repl'ing in one file for now.

```
Traceback (most recent call last):
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\runtime.py", line 731, in require
    ns_module = importlib.import_module(munge(ns_name))
                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Program Files\Blender Foundation\Blender 5.0\5.0\python\Lib\importlib\__init__.py", line 126, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "<frozen importlib._bootstrap>", line 1204, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1176, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1126, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 241, in _call_with_frames_removed
  File "<frozen importlib._bootstrap>", line 1204, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1176, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1140, in _find_and_load_unlocked
ModuleNotFoundError: No module named 'chera'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp_nrepl_async\nrepl_server.lpy", line 140, in do_handle_eval
    (let [result (last
                 ^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\runtime.py", line 2075, in trampoline
    ret = f(*args, **kwargs)
          ^^^^^^^^^^^^^^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 480, in last
    (if (seq (rest s))
             ^^^^^^^^
  File "C:\Program Files\Blender Foundation\Blender 5.0\5.0\python\Lib\functools.py", line 909, in wrapper
    return dispatch(args[0].__class__)(*args, **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\runtime.py", line 1219, in rest
    n = to_seq(o)
        ^^^^^^^^^
  File "C:\Program Files\Blender Foundation\Blender 5.0\5.0\python\Lib\functools.py", line 909, in wrapper
    return dispatch(args[0].__class__)(*args, **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 285, in _to_seq_lazyseq
    return o.seq()
           ^^^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 173, in seq
    self._compute_seq()
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 168, in _compute_seq
    self._obj = gen()
                ^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp_nrepl_async\nrepl_server.lpy", line 145, in ____do_handle_eval__for_5893_5929__lisp_fn_5930
    (basilisp.lang.compiler/compile-and-exec-form form
                            ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\compiler\__init__.py", line 192, in compile_and_exec_form
    exec(bytecode, ns.module.__dict__)  # pylint: disable=exec-used  # nosec 6102
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...Documents\projects\basilisp-playground\src\hello.lpy", line 6, in <module>
    [mathutils :refer [Vector]]))
                            ^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 5257, in require
    (doseq [libspec (map require-libspec libspecs)]
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 2547, in dorun
    (defn dorun
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 2556, in dorun__arity1
    (when (seq ptr)
          ^^^^^^^^^
  File "C:\Program Files\Blender Foundation\Blender 5.0\5.0\python\Lib\functools.py", line 909, in wrapper
    return dispatch(args[0].__class__)(*args, **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 285, in _to_seq_lazyseq
    return o.seq()
           ^^^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 173, in seq
    self._compute_seq()
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 168, in _compute_seq
    self._obj = gen()
                ^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 5263, in ____require__for_3361_3376__lisp_fn_3377
    (require-lib current-ns libspec flags)
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 5151, in require_lib
    (eval (list 'require*
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 4657, in eval_
    (defn eval
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 4666, in eval___arity2
    (basilisp.lang.compiler/compile-and-exec-form form
                            ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\compiler\__init__.py", line 192, in compile_and_exec_form
    exec(bytecode, ns.module.__dict__)  # pylint: disable=exec-used  # nosec 6102
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "<Eval Input>", line 1, in <module>
  File "...AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\runtime.py", line 733, in require
    raise ImportError(
ImportError: Basilisp namespace 'chera.ops' not found
...
```

    - update: I now can require? or rather, the require throws error, but it still works anyway
    - nope, require still doesn't work. but referring the full name works tho

- why can `basilisp.edn` be `:require`d but not `basilisp.io` ?

    if I call (io/path) directly, the following error thrown:

```
  exception: <class 'basilisp.lang.compiler.exception.CompilerException'>
      phase: :analyzing
    message: can't identify aliased form
       form: io/path
   location: ...\Documents\projects\basilisp-playground\src\chera\ops.lpy:97
    context:
```

but calling `basilisp.io/path` is working


## troubleshooting attempt 1

- put all code in root dir, changing ns name to just file name -> different error
  - requiring make my macro throws the following: 

  ```
    exception: <class 'NameError'> from <class 'basilisp.lang.compiler.exception.CompilerException'>
      phase: :macroexpansion
    message: error occurred during macroexpansion: name 'basilisp_core' is not defined
       form: (py-with-1 (bpy.context/temp_override ** :window bpy.context/window :screen bpy.context/screen :area area :region region) (bpy.ops.view3d/view_axis ** :type (name orientation)))
  ```

  removing the macro temporarily, requiring stops throwing error. but if I run (ops/hello), it will throw similar `basilisp_core` error

  ```
  Traceback (most recent call last):
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp_nrepl_async\nrepl_server.lpy", line 140, in do_handle_eval
    (let [result (last
                 ^^^^^
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\runtime.py", line 2075, in trampoline
    ret = f(*args, **kwargs)
          ^^^^^^^^^^^^^^^^^^
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\core.lpy", line 480, in last
    (if (seq (rest s))
             ^^^^^^^^
  File "C:\Program Files\Blender Foundation\Blender 5.0\5.0\python\Lib\functools.py", line 909, in wrapper
    return dispatch(args[0].__class__)(*args, **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\runtime.py", line 1219, in rest
    n = to_seq(o)
        ^^^^^^^^^
  File "C:\Program Files\Blender Foundation\Blender 5.0\5.0\python\Lib\functools.py", line 909, in wrapper
    return dispatch(args[0].__class__)(*args, **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 285, in _to_seq_lazyseq
    return o.seq()
           ^^^^^^^
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 173, in seq
    self._compute_seq()
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\seq.py", line 168, in _compute_seq
    self._obj = gen()
                ^^^^^
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp_nrepl_async\nrepl_server.lpy", line 145, in ____do_handle_eval__for_5893_5929__lisp_fn_5930
    (basilisp.lang.compiler/compile-and-exec-form form
                            ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...\AppData\Roaming\Blender Foundation\Blender\5.0\extensions\.local\lib\python3.11\site-packages\basilisp\lang\compiler\__init__.py", line 194, in compile_and_exec_form
    last = getattr(ns.module, final_wrapped_name)()
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "...\Documents\projects\basilisp-playground\hello.lpy", line 53, in __lisp_expr___527
    (ops/hello)
  File "...\Documents\projects\basilisp-playground\ops.lpy", line 7, in hello
    (println "is that working?")
     ^^^^^^^
NameError: name 'basilisp_core' is not defined
  ```
