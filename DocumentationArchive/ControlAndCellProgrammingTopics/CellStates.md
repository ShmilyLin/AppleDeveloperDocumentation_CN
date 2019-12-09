# `Cell`状态

对于`NSCell`的某些子类（例如`NSButtonCell`），对象的值是其状态。它可以具有两个状态（`on`和`off`）或三个状态（`on`、`off`和`mixed`）。`mixed`状态对于`复选框`或`单选按钮`很有用，该`复选框`或`单选按钮`反映的功能状态仅对App中的某些项或当前选择项有效。例如，假设一个`复选框`使所选文本变为粗体，如果所有选定的文字均以粗体显示，则该文字会亮起。如果所有选定的文本都不为粗体，则将其关闭。如果文字是粗体和纯文本的组合，则表示混合使用。现在，假设你单击`复选框`。如果打开它，所有文本将变为粗体。如果将其关闭，所有文本将变为纯文本。如果选择`mixed`状态，文本将保持原样。

默认情况下，`NSCell`具有两种状态。你可以使用`setAllowsMixedState:`方法允许第三个状态。要直接设置`按钮`的状态，请使用`setState:`。要遍历所有可用状态，请使用`setNextState`。