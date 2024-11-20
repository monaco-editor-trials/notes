# 🌈 Theming

Monaco editor is native part of VS Code but they have own theming system. [Monarch](https://microsoft.github.io/monaco-editor/monarch.html) is the syntax highlighting system used in Monaco editor. We can't think theming wtihout syntax highlighting. In this case we can't use VS Code themes directly but if we provide the same syntax highlighting rules, we can align Monaco editor with VS Code themes.

## 🎨 Theming

Monaco editor has a theming system called `editor` which is a part of `monaco.editor.IStandaloneThemeData`. We can provide the theme data to Monaco editor by calling `monaco.editor.defineTheme` method. The theme data is a JSON object which contains the colors for different parts of the editor.

```ts
monaco.editor.defineTheme('myCustomTheme', {
    base: 'vs-dark',
    inherit: true,
    rules: [
        { token: 'comment', foreground: 'ffa500', fontStyle: 'italic' },
        { token: 'keyword', foreground: 'ff0000' },
        { token: 'number', foreground: '0000ff' },
    ],
    colors: {
        'editor.foreground': '#F8F8F2',
        'editor.background': '#272822',
        'editorCursor.foreground': '#F8F8F0',
        'editor.lineHighlightBackground': '#3E3D32',
        'editorLineNumber.foreground': '#75715E',
        'editor.selectionBackground': '#49483E',
        'editor.inactiveSelectionBackground': '#3B3A32',
    }
});
```

In the above example, we have defined a theme called `myCustomTheme` which is based on `vs-dark` theme. We have provided the colors for different parts of the editor like `editor.foreground`, `editor.background`, `editorCursor.foreground`, etc. We have also provided the syntax highlighting rules for `comment`, `keyword`, and `number` tokens.

## 🎨 Using VS Code Themes

We can use the VS Code themes in Monaco editor by providing the same syntax highlighting rules. We can get the syntax highlighting rules for a theme by using the `getTheme` method of `monaco.editor.IStandaloneThemeData`. We can then use these rules to define a theme for Monaco editor.

```ts
const vsDarkTheme = monaco.editor.getTheme('vs-dark');
monaco.editor.defineTheme('vs-dark', vsDarkTheme);
```

In the above example, we have defined a theme called `vs-dark` for Monaco editor which is based on the `vs-dark` theme of VS Code. We have used the `getTheme` method to get the syntax highlighting rules for the `vs-dark` theme and then used these rules to define the theme for Monaco editor.
