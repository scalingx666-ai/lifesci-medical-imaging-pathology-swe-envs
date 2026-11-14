# Issue

**Title:** Work around RichTextFX paste bug

## Description

It appears impossible to copy paste from the script editor, then paste it back to the script editor - at least on macOS. Trying to do so gives an exception

```
java.lang.ClassCastException: class java.nio.HeapByteBuffer cannot be cast to class [B (java.nio.HeapByteBuffer and [B are in module java.base of loader 'bootstrap')
	at org.fxmisc.richtext.ClipboardActions.paste(ClipboardActions.java:91)
	at qupath.lib.gui.scripting.richtextfx.CustomCodeArea.paste(CustomCodeArea.java:40)
	at org.fxmisc.richtext.GenericStyledAreaBehavior.lambda$static$1(GenericStyledAreaBehavior.java:87)
	at org.fxmisc.wellbehaved.event.template.InputMapTemplate.lambda$consume$0(InputMapTemplate.java:221)
	at org.fxmisc.wellbehaved.event.template.PatternActionTemplate.lambda$null$1(InputMapTemplate.java:425)
	at java.base/java.util.Optional.map(Optional.java:260)
	at org.fxmisc.wellbehaved.event.template.PatternActionTemplate.lambda$getInputHandlerTemplateMap$2(InputMapTemplate.java:425)
	at org.fxmisc.wellbehaved.event.template.InputHandlerTemplateMap.lambda$sequence$0(InputHandlerTemplateMap.java:25)
```

RichTextFX appears to be copying some formatted data, then assuming that this can be cast to a `byte[]` later if needed. Seemingly, it can't.

Presumably this is a recent regression caused by updating macOS or JavaFX.

The simplest workaround is to override the `paste` behavior (overriding `copy` should work too, but the `paste` override code is already there).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4657a94c5e67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.