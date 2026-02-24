## theDANE — the Danish Advanced Native Editor

**A fast, native Windows code editor with syntax highlighting, intelligent code reformatting, and a built-in hex editor.**

*© 1999–2026 Kim Bo Madsen / Components4Developers DK. All rights reserved.*

---

## Feature Overview

**Editor**
— Syntax highlighting for 11 languages · context-aware code completion · bracket and pair matching · code folding · bookmarks (numbered and unnumbered) · multi-caret editing with distribute paste · smart double-click selection expansion · block indent/unindent · line operations (move, duplicate, join, delete, comment toggle) · find & replace with regex and Find All results panel · unlimited undo/redo · zoom

**Code Reformatter**
— BNF-driven reformatter for Pascal with per-rule formatting directives · token-based reformatter for SQL, XML, JSON, HTML, JavaScript, C#, and CSS · named profiles per language with import/export · full configuration editor

**Hex Editor**
— Dual-pane hex/ASCII view · data inspector with 24 numeric and string formats (editable) · find in hex or text · full undo/redo · pane-aware copy (hex string or text) · theming with 8 built-in style sets

**Theming**
— 4 application themes (theDANE Dark, theDANE Light, Windows Dark, Windows Light) · per-language editor style sets (Visual Studio, Monokai, GitHub, Notepad++, and more) · all preferences remembered between sessions

**Workspace**
— Tabbed editing with tear-off/re-dock floating windows · recent files · Windows Explorer shell integration (right-click → Open / Open as Hex) · single-instance multi-file opening · optional splash screen · SHA-256 integrity verification

**Built With**
— Native Win32/Win64 Delphi application · no runtime dependencies · kbmVCL component suite · launches in under a second

---

## Getting Started

When you start theDANE, a splash screen appears briefly while the application loads. Click anywhere on the splash to dismiss it early. The main window then opens with a fresh empty editor tab, ready to type. If you prefer to skip the splash entirely, toggle it off under **Help → Show Splash on Startup**.

To open an existing file, use **File → Open** (`Ctrl+O`). The language is auto-detected from the file extension — you can always override it from the **Language** menu.

### Opening Files from Windows Explorer

You can register theDANE with Windows Explorer via **Help → Add Explorer Integration**. Once registered, right-clicking any file (or selection of files) in Explorer shows a **theDANE** cascading menu with two options:

- **Open in theDANE** — opens the file in a text/code editor tab
- **Open as Hex in theDANE** — opens the file directly in the hex editor

theDANE is a **single-instance application**: if it is already running, files opened from Explorer are added as new tabs in the existing window rather than spawning additional copies. This works seamlessly even when you select multiple files in Explorer and open them all at once — each file gets its own tab.

To remove the Explorer integration later, use **Help → Remove Explorer Integration**. No administrator rights are required for either operation.

---

## The Screen Layout

The main window is divided into four areas, from top to bottom:

### 1. Toolbar Strip

A horizontal strip at the very top of the window containing three dropdown controls and a settings button:

| Control | What it does |
|---------|-------------|
| **Profile** dropdown | Shows the active reformatter profile for the current language, e.g. `Profile (Pascal): Default *`. Pick a different profile to instantly change how Reformat works. |
| **⚙ button** | Opens the profile settings editor for the active profile. |
| **Theme** dropdown | Switches the entire application theme (window chrome, menus, dialogs, tabs, status bar). Your choice is remembered between sessions. |
| **Style** dropdown | Switches the editor color scheme for the current language. Each language has its own set of style presets (e.g. Visual Studio, Monokai, GitHub). Also remembered per-language. |

### 2. Tab Strip

A row of document tabs directly below the toolbar. The active tab is highlighted; all others are dimmed. Each tab shows the filename, or "Untitled" for new documents. A **● dot** appears before the name when the file has unsaved changes.

**What you can do with tabs:**

- **Click** a tab to switch to it.
- **Right-click** a tab for a popup menu: Close, Close All, Close Other Tabs, Close Tabs to the Left, Close Tabs to the Right.
- **Drag** a tab out of the strip to tear it off into a **floating editor window** that you can position anywhere on screen.
- **Drag** a floating editor window back onto the tab strip (or onto another editor) to **re-dock** it as a tab.

### 3. Editor Area

The central workspace. Depending on the file content, this is either a **code editor** or a **hex editor**.

**In code editor mode**, the area contains:

- A **gutter** on the left — shows line numbers, bookmark indicators, fold markers (▸/▾), and search-match markers.
- The **code area** — your syntax-highlighted source code with bracket matching, caret highlighting, and selection.
- A **Find Results panel** (bottom, hidden by default) — appears when you use Find All, listing every match with line number and preview. Double-click a result to jump to it.

**In hex editor mode**, the area contains:

- An **offset column** on the left — the byte address of each row.
- A **hex pane** in the center — byte values shown as two-digit hexadecimal numbers.
- An **ASCII pane** on the right — text representation of the bytes (non-printable bytes shown as dots).
- A **Data Inspector panel** (right side, hidden by default) — toggle with `Ctrl+I` to see the bytes at the cursor interpreted in 24 different numeric and string formats.

### 4. Status Bar

**Code editor mode**: cursor position (line and column), insert/overwrite mode (INS or OVR), the file path (or "Untitled"), the active language name, and the current zoom level as a percentage.

**Hex editor mode**: byte offset (hex and decimal), insert/overwrite mode, total file size in bytes, and the file path.

---

## Working with Files

### Creating and Opening

| Action | How |
|--------|-----|
| New empty tab | **File → New** or `Ctrl+N` |
| Open a file | **File → Open** or `Ctrl+O` |
| Open a file as hex | **File → Open as Hex** |
| Reopen a recent file | **File → Reopen Recent** — lists the last 10 files you opened, plus a **Clear Recent Files** option |

When you open a file, theDANE detects the language from the extension and applies the appropriate syntax highlighter, code completion set, and reformatter profile automatically.

### Saving

| Action | How |
|--------|-----|
| Save | **File → Save** or `Ctrl+S` |
| Save with a new name | **File → Save As** |

If you close a modified file, theDANE prompts you to save first.

### Closing

| Action | How |
|--------|-----|
| Close current tab | **File → Close** or `Ctrl+F4` |
| Close all tabs | Right-click any tab → **Close All** |
| Close other tabs | Right-click a tab → **Close Other Tabs** |
| Close tabs to the left | Right-click a tab → **Close Tabs to the Left** |
| Close tabs to the right | Right-click a tab → **Close Tabs to the Right** |
| Exit theDANE | **File → Exit** |

### Supported File Types

| Language | Extensions |
|----------|-----------|
| Pascal / Delphi | `.pas` `.dpr` `.dfm` `.inc` |
| SQL | `.sql` |
| XML | `.xml` `.xsd` |
| JSON | `.json` |
| HTML | `.html` `.htm` |
| JavaScript / TypeScript | `.js` `.ts` |
| C# | `.cs` |
| CSS | `.css` |
| Markdown | `.md` `.markdown` |
| Key/Value (INI) | `.ini` `.conf` `.properties` `.env` |

Files with unrecognized extensions open with no syntax highlighting (plain text mode). You can set the language manually from the **Language** menu at any time.

---

## Menu Reference

### File Menu

| Item | Shortcut | Description |
|------|----------|-------------|
| New | `Ctrl+N` | Create a new empty editor tab |
| Open... | `Ctrl+O` | Open a file from disk |
| Open as Hex... | — | Open a file directly in hex editor mode |
| Save | `Ctrl+S` | Save the current file |
| Save As... | — | Save with a new filename |
| Close | `Ctrl+F4` | Close the current tab |
| Reopen Recent | — | Submenu listing the last 10 opened files, with a Clear Recent Files option at the bottom |
| Exit | — | Close the application |

### Edit Menu

| Item | Shortcut | Description |
|------|----------|-------------|
| Undo | `Ctrl+Z` | Undo the last change |
| Redo | `Ctrl+Y` | Redo the last undone change |
| Cut | `Ctrl+X` | Cut selection to clipboard |
| Copy | `Ctrl+C` | Copy selection to clipboard |
| Paste | `Ctrl+V` | Paste from clipboard |
| Select All | `Ctrl+A` | Select the entire document |

### Search Menu

| Item | Shortcut | Description |
|------|----------|-------------|
| Find... | `Ctrl+F` | Open the Find dialog |
| Replace... | `Ctrl+H` | Open the Find & Replace dialog |
| Find Next | `F3` | Jump to the next match |
| Find Previous | `Shift+F3` | Jump to the previous match |
| Go to Line... | `Ctrl+G` | Jump to a specific line number |

### Format Menu

| Item | Shortcut | Description |
|------|----------|-------------|
| Reformat | `Ctrl+T` | Reformat the document using the active profile |
| Profiles | — | Submenu: New, Clone, Rename, Delete, Set as Default, Import, Export, Edit Settings |
| Reformatter Settings... | — | Open the raw configuration for the active profile |

### View Menu

| Item | Shortcut | Description |
|------|----------|-------------|
| Show Gutter | — | Toggle the line-number gutter |
| Show Status Bar | — | Toggle the bottom status bar |
| Zoom In | `Ctrl++` | Increase font size |
| Zoom Out | `Ctrl+-` | Decrease font size |
| Reset Zoom | `Ctrl+Num *` | Return to default font size |
| Editor Style | — | Submenu listing color schemes for the current language |
| Hex View | `Ctrl+Shift+H` | Toggle between code editor and hex editor for the current file |

### Language Menu

Lists all available languages: None, SQL, XML, JSON, HTML, Pascal, C#, JavaScript, CSS, Markdown, Key/Value. Selecting one changes the syntax highlighting, code completion, and reformatter profile for the current editor.

### Help Menu

| Item | Description |
|------|-------------|
| About theDANE... | Shows the splash image, application title, tagline, and copyright |
| Show Splash on Startup | Toggle: show or skip the splash screen on launch (checked = show) |
| Add Explorer Integration... | Register theDANE in the Windows Explorer right-click menu for all file types |
| Remove Explorer Integration | Unregister theDANE from the Explorer context menu |

The Explorer integration items are mutually exclusive — only the one relevant to the current state is shown.

---

## Editing Code

### Basics

theDANE behaves like any standard text editor: type to insert, use arrow keys to move, click and drag to select. A few things that make it feel productive from the start:

- **Auto-indent** — press `Enter` and the new line indents to match the surrounding context.
- **Insert / Overwrite** — toggle with the `Insert` key. The status bar shows INS or OVR so you always know which mode you are in.
- **Block indent / unindent** — select one or more lines and press `Tab` to indent or `Shift+Tab` to unindent the entire block. The selection is preserved so you can repeat the operation.
- **Bracket matching** — when the cursor is adjacent to a bracket, parenthesis, or language-level pair like `begin`/`end`, the matching counterpart is highlighted in both positions.

### Selecting Text

Standard click-and-drag or Shift+Arrow selection works as expected. theDANE also offers some powerful extras:

**Smart double-click** — rapid successive double-clicks expand the selection through increasing scopes:

1. **Word** — standard alphanumeric word (letters, digits, underscores)
2. **Extended Word** — connected identifiers like `MyObject.Property` or `path/segment`
3. **Full Line** — selects the entire current line (offered before inner block when the enclosing block spans multiple lines)
4. **Inner Block** — content inside the nearest enclosing pair (between the brackets, not including them)
5. **Outer Block** — same region but including the bracket/pair characters
6. **Next Enclosing Pair** — expand outward to the next nesting level
7. **Full Line(s)** — fallback: select all lines covered by the current selection
8. **Select All** — the entire document

**Scope selection** is also available from the right-click **Select Scope** submenu: Expand Selection, Shrink Selection, Word, Extended Word, Inner Block, Outer Block, Line. Expand Selection uses `Ctrl+W`, Shrink Selection uses `Ctrl+Shift+W`, and Line uses `Ctrl+L`.

### Multi-Caret Editing

Place additional cursors by holding `Alt` and clicking at different positions. Or create a vertical column of cursors by holding `Alt+Shift` and pressing `Up` or `Down`. Everything you type — characters, deletions, pastes — happens at all cursor positions simultaneously.

**Distribute Paste**: when pasting with multiple cursors active and the clipboard contains exactly the same number of lines as there are cursors, each clipboard line is pasted to its corresponding cursor.

### Line Editing

| Action | Shortcut |
|--------|----------|
| Select entire line | `Ctrl+L` |
| Delete line(s) | `Ctrl+Shift+K` |
| Duplicate line or selection | `Ctrl+D` |
| Move line up | `Alt+Up` |
| Move line down | `Alt+Down` |
| Insert blank line below | `Ctrl+Enter` |
| Insert blank line above | `Ctrl+Shift+Enter` |
| Join lines | `Ctrl+J` |
| Toggle line comment | `Ctrl+/` |
| UPPERCASE | `Ctrl+Shift+U` |
| lowercase | `Ctrl+U` |

### Word and Text Deletion

| Action | Shortcut |
|--------|----------|
| Delete word to the left | `Ctrl+Backspace` |
| Delete word to the right | `Ctrl+Delete` |

### Pair Navigation

| Action | Shortcut |
|--------|----------|
| Jump to matching pair | `Ctrl+B` |
| Jump and select to matching pair | `Ctrl+Alt+B` |

`Ctrl+B` moves the cursor to the matching counterpart without selecting anything. `Ctrl+Alt+B` selects the entire region between and including both pair delimiters.

This works with all paired constructs the highlighter understands: `()`, `[]`, `{}`, `begin`/`end`, `if`/`end`, XML open/close tags, and more.

### Document Navigation

| Action | Shortcut |
|--------|----------|
| Jump to start of file | `Ctrl+Home` |
| Jump to end of file | `Ctrl+End` |
| Select to start of file | `Ctrl+Shift+Home` |
| Select to end of file | `Ctrl+Shift+End` |
| Go to Line | `Ctrl+G` |

---

## Code Completion & Auto-Suggestion

theDANE provides context-aware code suggestions powered by each language's highlighter.

### How It Works

- Press **`Ctrl+Space`** to open the suggestion popup manually at any time.
- With **Auto Trigger on Type** enabled, the popup appears automatically as you type identifier characters (`a`–`z`, `_`, etc.) or after typing a `.` (dot).
- The list **filters live** as you continue typing — only matching entries remain visible.
- If you triggered manually and only **one match** remains, it is inserted automatically.

### Navigating the Popup

| Key | Action |
|-----|--------|
| `Up` / `Down` | Move through the list |
| `Page Up` / `Page Down` | Scroll the list |
| `Enter` or `Tab` | Accept the selected suggestion |
| `Escape` | Dismiss without accepting |

Typing a non-identifier character (space, parenthesis, semicolon, etc.) also dismisses the popup.

### What Gets Suggested

Each language highlighter builds its own suggestion list. For example:

- **Pascal** — keywords, directives, and identifiers found in the surrounding code (±100 lines around the cursor)
- **SQL** — keywords, data types, and built-in functions for the active dialect
- **C#** — language keywords, common constructs, and identifiers from surrounding code
- **JavaScript / CSS** — language keywords and common constructs

### Enabling / Disabling

Both **Code Completion** and **Auto Trigger on Type** can be toggled from the right-click **Options** submenu inside the editor.

---

## Finding & Replacing

### Find (`Ctrl+F`)

Opens an inline find dialog. Type your search term and press Enter or click Find Next. Options:

- **Case Sensitive** — match exact uppercase/lowercase
- **Whole Word** — match only when surrounded by non-word characters
- **Regular Expressions** — use regex pattern syntax
- **Direction** — search Forward or Backward through the document

### Find All

Searches the entire document and displays results in a **Find Results** panel at the bottom of the editor. Each entry shows the line number, column, and a preview of the line. Double-click any entry to jump to it. Matches are also marked with indicators in the gutter.

### Replace (`Ctrl+H`)

Opens the find-and-replace dialog. You can replace matches one at a time or use **Replace All** to replace every occurrence in the document at once. A count is shown when Replace All finishes.

### Quick Navigation

| Shortcut | Action |
|----------|--------|
| `F3` | Repeat the last search forward |
| `Shift+F3` | Repeat the last search backward |
| `Ctrl+G` | Go to a specific line number |

---

## Bookmarks

Bookmarks let you mark important lines so you can jump back to them quickly.

### Unnumbered Bookmarks

| Action | Shortcut |
|--------|----------|
| Toggle bookmark on current line | `Ctrl+F2` |
| Jump to next bookmark | `F2` |
| Jump to previous bookmark | `Shift+F2` |
| Clear all bookmarks | `Ctrl+Shift+F2` |

### Numbered Bookmarks (0–9)

| Action | Shortcut |
|--------|----------|
| Set/clear numbered bookmark 0–9 | `Ctrl+Shift+0` through `Ctrl+Shift+9` |
| Go to numbered bookmark 0–9 | `Ctrl+0` through `Ctrl+9` |

A line can have either one numbered or one unnumbered bookmark, not both. Bookmark indicators appear in the gutter. All bookmark operations are also available from the right-click **Bookmarks** submenu.

---

## Code Folding

Foldable regions (functions, blocks, XML elements, etc.) are detected automatically by the language highlighter.

- **Fold markers** appear in the gutter as small triangles: ▾ (expanded) or ▸ (collapsed). Click one to toggle.
- **Collapsed regions** show a ⋯ indicator on the fold line; the hidden lines are simply not rendered.
- **Fold Selection** — select a range of lines and fold them manually, even if they are not a natural language block.
- **Unfold Selection** — expand folds within the selected range or at the caret line.
- **Collapse All** — fold every detected region in the document at once.
- **Expand All** — unfold every region.

All folding operations are available from the right-click **Code Folding** submenu.

---

## Themes & Color Schemes

### Application Themes

The theme controls the entire application appearance — window chrome, menus, common dialogs, toolbar, tabs, and status bar.

| Theme | Description |
|-------|-------------|
| **theDANE Light** | Custom Nordic parchment palette (default) |
| **theDANE Dark** | Custom Nordic Forge dark palette |
| **Windows Dark** | Standard Windows 10 dark theme |
| **Windows Light** | Standard Windows light theme |

Switch themes from the **Theme** dropdown in the toolbar. Once you select a theme it becomes your default and is restored on next launch.

### Editor Style Sets

Independently from the theme, each language has its own set of **style sets** that control syntax coloring inside the editor. Choose from the **Style** dropdown in the toolbar.

Typical options across languages: Visual Studio, Visual Studio Dark, GitHub, Monokai, Notepad++, Google, theDANE, theDANE Dark. Some languages have extras — for example SQL includes an **SSMS** (SQL Server Management Studio) style.

Your chosen style set is stored **per language** and persisted between sessions. This means you can use Monokai for Pascal, GitHub for JSON, and Visual Studio Dark for SQL, and theDANE remembers all of them.

When viewing a file in hex editor mode without a syntax highlighter, the Style dropdown shows the hex editor's own style sets (Delphi, Visual Studio, Visual Studio Dark, Monokai, theDANE, theDANE Dark, GitHub, Notepad++).

---

## Code Reformatter

Press `Ctrl+T` (or **Format → Reformat**) to automatically reformat the current document according to configurable style rules. The reformatter settings dialog can also be opened directly with `Ctrl+Shift+R` from the right-click Options submenu.

### Two Engines

**Token-based reformatter** — available for SQL, XML, JSON, HTML, JavaScript, C#, and CSS. Operates on the token stream with configurable indentation and whitespace settings.

**BNF-driven reformatter** — available for Pascal/Delphi. This is a significantly more powerful approach: the source is parsed into a full syntax tree using a BNF grammar, and then re-emitted according to per-rule formatting directives. This gives fine-grained control over exactly how every language construct — every `begin`, `end`, `if`, `then`, `procedure` — is laid out.

### Pascal Reformatter: Configuration Reference

The Pascal reformatter is configured through a plain-text settings file (managed via profiles — see next section). The settings are divided into categories:

#### Indentation & Casing

| Setting | Description | Default |
|---------|-------------|---------|
| `IndentSize` | Spaces per indent level | 2 |
| `UseTabs` | Use tab characters instead of spaces | False |
| `SmartTab` | Align continuations to context (e.g. opening paren column) | False |
| `AlignToParenOnWrap` | Align wrapped argument lines to opening parenthesis | True |
| `KeywordCase` | Keyword casing: 0=No change, 1=UPPER, 2=lower, 3=Capitalize | 2 |
| `DirectiveCase` | Compiler directive casing (same values as KeywordCase) | 2 |

#### Blank Lines

| Setting | Description | Default |
|---------|-------------|---------|
| `PreserveBlankLines` | Keep blank lines from original source | True |
| `PreserveSourceLineBreaks` | Keep original line breaks in multi-line constructs | True |
| `MaxPreservedBlankLines` | Collapse consecutive blank lines to at most this many | 2 |
| `BlankLineBeforeComments` | Insert blank line before standalone comments | False |
| `StructuralBlankLines` | Insert blank lines between different declaration types | False |
| `BlankLineBeforeMultiLineBlocks` | Add blank line before blocks that exceed the threshold | True |
| `MultiLineBlockThreshold` | Minimum source lines to trigger the above | 3 |

#### Line Wrapping

| Setting | Description | Default |
|---------|-------------|---------|
| `MaxLineLength` | Auto-wrap threshold in columns (0 = disabled) | 0 |
| `WrapMinGain` | Minimum characters saved to justify a wrap | 10 |

#### Preprocessor Directives

| Setting | Description | Default |
|---------|-------------|---------|
| `IndentPreprocessorDirectives` | Indent code inside `{$IFDEF}` blocks | False |
| `PreprocessorIndentSize` | Spaces per preprocessor indent level (0 = use IndentSize) | 0 |

#### Trailing Comment Alignment

| Setting | Description | Default |
|---------|-------------|---------|
| `TrailingCommentAlignment` | None / Local / Global | None |
| `TrailingCommentMinSpaces` | Minimum spaces before a trailing comment | 2 |
| `TrailingCommentColumn` | Fixed column for alignment (0 = auto) | 0 |

#### Per-Rule Formatting

Every BNF grammar rule or keyword can have its own formatting directives. The settings file uses a simple `rulename: directive, directive, ...` syntax:

```text
begin: BreakBefore, BreakAfter, IncrementIndent
end: DecrementIndent, BreakBefore, BreakAfter
if: SpaceAfter
then: SpaceBefore, BreakAfter
else: BreakBefore, BreakAfter
procedure: BreakBefore, BlankLinesBefore=1
```

The full set of available directives:

| Directive | What it does |
|-----------|-------------|
| `BreakBefore` / `BreakAfter` | Insert a line break before or after |
| `BlankLinesBefore=N` / `BlankLinesAfter=N` | Insert N blank lines |
| `IncrementIndent` / `DecrementIndent` | Change the indent level for child content |
| `ForceIndentLevel=N` | Set indent to an absolute level |
| `SpaceBefore` / `SpaceAfter` | Insert a space |
| `NoSpaceBefore` / `NoSpaceAfter` | Suppress automatic spacing |
| `SmartIndent=N` | Dynamic or fixed column offset for Smart Tab |
| `WrapMode` | Control wrapping behavior for parenthesized content |
| `AllowWrapAfter` / `AllowWrapBefore` | Mark a legal wrapping point |
| `NoWrap` | Prevent wrapping here |
| `WrapIndent=N` | Override indent for wrapped continuation |
| `SaveAlignment` / `RestoreAlignment` | Save/restore column alignment (e.g. for try/except) |
| `ApplyIndentToLeadingComments` | Align comments above a construct to its indent level |

#### Debug

Set `DebugEnabled: True` in the profile to write a detailed log of every reformatter decision to a file (default `BNF_DEBUG.log` in the application folder). Useful when fine-tuning rules to understand why a construct is formatted a certain way.

---

## Reformatter Profiles

Profiles let you save and switch between different formatting configurations. Each language has its own independent set of profiles.

### Creating and Managing Profiles

All profile operations are under **Format → Profiles**:

| Action | Description |
|--------|-------------|
| **New Profile** | Creates a new profile with the language's default settings |
| **Clone Profile** | Duplicates the current profile under a new name |
| **Rename Profile** | Renames the current profile |
| **Delete Profile** | Removes the current profile |
| **Set as Default** | Marks the current profile as the default for this language (shown with `*`) |
| **Import Profile...** | Loads a `.cfg` file into the profile list |
| **Export Profile...** | Saves the current profile to a `.cfg` file |
| **Edit Profile Settings...** | Opens the raw configuration text in a dialog for full manual editing |

The **⚙ button** in the toolbar is a shortcut to **Edit Profile Settings** for the active profile.

### Where Profiles are Stored

Profiles are plain-text `.cfg` files, one per profile, organized by language:

```
Documents\ReformatterProfiles\Pascal\Default.cfg
Documents\ReformatterProfiles\Pascal\My Company Style.cfg
Documents\ReformatterProfiles\SQL\Default.cfg
...
```

Because they are simple text files, you can easily back them up, share them with colleagues, check them into version control, or copy them between machines.

### Switching Profiles

Use the **Profile** dropdown in the toolbar to switch between profiles for the current language. The default profile (marked with `*`) is applied automatically when you open a file in that language.

---

## SQL Dialect Support

The SQL highlighter supports multiple dialects, each adding its own set of keywords, data types, and built-in functions:

| Dialect | Highlights |
|---------|-----------|
| **ANSI SQL-92** through **SQL-2016** | Progressive standards — core SQL, CTEs, window functions, JSON support |
| **Oracle** | PL/SQL blocks, PACKAGE, CURSOR, NVL, DECODE, SYSDATE, DUAL |
| **MS SQL Server** | T-SQL, TRY/CATCH, RAISERROR, TOP, NVARCHAR, TRAN |
| **PostgreSQL** | PL/pgSQL, ILIKE, RETURNING, SERIAL, ARRAY, LATERAL |
| **MySQL** | AUTO_INCREMENT, LIMIT, ENGINE, CHARSET, ENUM |
| **SQLite** | AUTOINCREMENT, VACUUM, PRAGMA, ATTACH, GLOB |

---

## Hex Editor

Open any file in hex mode via **File → Open as Hex**, or toggle the current file with **View → Hex View** (`Ctrl+Shift+H`).

### Layout

The hex editor has a traditional three-column layout:

- **Offset column** (left) — the byte address of each row
- **Hex pane** (center) — bytes shown as two-digit hexadecimal values
- **ASCII pane** (right) — text representation (printable characters shown as-is, non-printable replaced with dots)

Press **`Tab`** to switch the active pane between hex and ASCII. The cursor and selection appear in both panes simultaneously, but the active pane is highlighted more prominently.

### Editing Bytes

- In the **hex pane**: type hex digits (0–9, A–F) to overwrite byte values.
- In the **ASCII pane**: type printable characters to overwrite.
- **Insert / Overwrite** modes: toggle with the `Insert` key, just like the code editor.
- Full **undo/redo** — multi-byte edits are grouped into a single undo step.
- **Cut / Copy / Paste** work as expected.

### Pane-Aware Copy

The right-click context menu adapts based on which pane your cursor is in:

| Active Pane | "Copy" produces... | Second copy option |
|-------------|--------------------|--------------------|
| **ASCII pane** | Printable text | Copy as Hex |
| **Hex pane** | Hex string (e.g. `4B 42 4D`) | Copy as Text |

### Data Inspector

Toggle with **`Ctrl+I`**. A panel appears on the right side showing the bytes at the cursor position interpreted as 24 different formats:

| Category | Formats |
|----------|---------|
| **Byte** | Binary, Octal, Hex, UInt8, Int8 |
| **16-bit** | UInt16 LE, UInt16 BE, Int16 LE, Int16 BE |
| **32-bit** | UInt32 LE, UInt32 BE, Int32 LE, Int32 BE, Float32 LE, Float32 BE |
| **64-bit** | UInt64 LE, UInt64 BE, Int64 LE, Int64 BE, Double LE, Double BE |
| **Strings** | ASCII, UTF-8, UTF-16 LE |

All numeric fields are **editable**: type a new value and press `Enter` to write it back into the file. Multi-byte writes are grouped into a single undo step. The inspector panel is resizable via a splitter.

**Zoom**: you can adjust the font size of the Data Inspector independently — right-click inside the inspector panel and choose **Increase Font Size** or **Decrease Font Size**. This setting is persisted between sessions.

### Hex Editor Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Shift+H` | Toggle hex view on/off for the current file |
| `Ctrl+C` | Copy (format depends on active pane) |
| `Ctrl+X` | Cut |
| `Ctrl+V` | Paste |
| `Ctrl+Z` | Undo |
| `Ctrl+Y` | Redo |
| `Ctrl+A` | Select All |
| `Ctrl+F` | Find (hex or text) |
| `F3` | Find Next |
| `Shift+F3` | Find Previous |
| `Ctrl+G` | Go to Offset |
| `Ctrl+I` | Toggle Data Inspector panel |
| `Tab` | Switch between Hex and ASCII pane |
| `Insert` | Toggle Insert / Overwrite mode |
| `Ctrl++` | Zoom in |
| `Ctrl+-` | Zoom out |
| `Ctrl+Num *` | Reset zoom |
| `Ctrl+Mouse Wheel` | Zoom in/out |

### Finding Bytes

Press `Ctrl+F` in the hex editor to open a find dialog with two search modes:

- **Hex bytes** — enter space-separated hex values (e.g. `4D 5A 90 00`)
- **Text (UTF-8)** — enter a text string to search for in the raw byte stream

Matches are found forward from the cursor. Use `F3` / `Shift+F3` to repeat the search forward or backward.

---

## Right-Click Context Menu (Code Editor)

Right-clicking inside the code editor shows a structured context menu:

**Top level:**

- Copy · Cut · Paste · Undo · Redo
- Find... · Replace...
- Jump to Matching Pair (`Ctrl+B`)
- Jump and Select to Matching Pair (`Ctrl+Alt+B`)

**Select Scope submenu:**

- Expand Selection (`Ctrl+W`) · Shrink Selection (`Ctrl+Shift+W`)
- Word · Extended Word · Inner Block · Outer Block · Line (`Ctrl+L`)

**Edit submenu:**

- Delete Line(s) (`Ctrl+Shift+K`) · Duplicate (`Ctrl+D`)
- Move Line Up (`Alt+Up`) · Move Line Down (`Alt+Down`)
- Insert Line Below (`Ctrl+Enter`) · Insert Line Above (`Ctrl+Shift+Enter`)
- Join Lines (`Ctrl+J`) · Toggle Line Comment (`Ctrl+/`)
- UPPERCASE (`Ctrl+Shift+U`) · lowercase (`Ctrl+U`)
- Go to Line (`Ctrl+G`)

**Bookmarks submenu:**

- Toggle Bookmark (`Ctrl+F2`)
- Toggle Numbered Bookmark → 0–9 (`Ctrl+Shift+0`..`9`); go to with `Ctrl+0`..`9`
- Next Bookmark (`F2`) · Previous Bookmark (`Shift+F2`)
- Clear All Bookmarks (`Ctrl+Shift+F2`)

**Code Folding submenu:**

- Fold Selection · Unfold Selection
- Collapse All · Expand All

**Reformat:**

- Reformat (`Ctrl+T`)
- Reformat Settings...

**Options submenu:**

| Option | Description |
|--------|-------------|
| Show Gutter | Toggle line numbers and fold markers |
| Show Status | Toggle the status area at the bottom of the editor |
| Show ScrollBars | Toggle scrollbar visibility |
| Show Tabs | Render tab characters as visible arrows |
| Show Line Breaks | Render line endings as visible markers |
| Show Spaces | Render spaces as visible dots |
| Show Control Chars | Render control characters |
| Read Only | Lock the file against editing |
| Insert Mode | Toggle insert/overwrite |
| Code Completion | Enable or disable the suggestion popup system |
| Auto Trigger on Type | Automatically show suggestions as you type |
| Use Tabs | Insert real tab characters (vs. spaces) |
| Tab Size | Sub-menu: 2, 4, or 8 |
| Smart Tabs | Context-aware indentation alignment |
| Configure Reformat... (`Ctrl+Shift+R`) | Open the reformatter settings editor |

---

## Complete Keyboard Shortcut Reference

### File

| Shortcut | Action |
|----------|--------|
| `Ctrl+N` | New file |
| `Ctrl+O` | Open file |
| `Ctrl+S` | Save |
| `Ctrl+F4` | Close tab |

### Editing

| Shortcut | Action |
|----------|--------|
| `Ctrl+Z` | Undo |
| `Ctrl+Y` | Redo |
| `Ctrl+X` | Cut |
| `Ctrl+C` | Copy |
| `Ctrl+V` | Paste |
| `Ctrl+A` | Select All |
| `Ctrl+L` | Select Line |
| `Ctrl+D` | Duplicate line/selection |
| `Ctrl+J` | Join lines |
| `Ctrl+/` | Toggle line comment |
| `Ctrl+Shift+U` | UPPERCASE |
| `Ctrl+U` | lowercase |
| `Ctrl+Shift+K` | Delete line(s) |
| `Ctrl+Backspace` | Delete word left |
| `Ctrl+Delete` | Delete word right |
| `Alt+Up` | Move line up |
| `Alt+Down` | Move line down |
| `Ctrl+Enter` | Insert line below |
| `Ctrl+Shift+Enter` | Insert line above |
| `Tab` | Indent selection / insert tab |
| `Shift+Tab` | Unindent selection |
| `Insert` | Toggle Insert / Overwrite |
| `Shift+Insert` | Paste (alternative) |
| `Ctrl+Insert` | Copy (alternative) |
| `Ctrl+W` | Expand Selection (progressive scope) |
| `Ctrl+Shift+W` | Shrink Selection |

### Navigation

| Shortcut | Action |
|----------|--------|
| `Ctrl+G` | Go to Line |
| `Ctrl+B` | Jump to matching pair |
| `Ctrl+Alt+B` | Jump and select to matching pair |
| `Ctrl+Home` | Jump to start of file |
| `Ctrl+End` | Jump to end of file |
| `Ctrl+Shift+Home` | Select to start of file |
| `Ctrl+Shift+End` | Select to end of file |

### Find & Replace

| Shortcut | Action |
|----------|--------|
| `Ctrl+F` | Find |
| `Ctrl+H` | Replace |
| `F3` | Find Next |
| `Shift+F3` | Find Previous |

### Bookmarks

| Shortcut | Action |
|----------|--------|
| `Ctrl+F2` | Toggle bookmark |
| `Ctrl+Shift+0`..`9` | Toggle numbered bookmark |
| `Ctrl+0`..`9` | Go to numbered bookmark |
| `F2` | Next bookmark |
| `Shift+F2` | Previous bookmark |
| `Ctrl+Shift+F2` | Clear all bookmarks |

### Zoom

| Shortcut | Action |
|----------|--------|
| `Ctrl++` | Zoom in |
| `Ctrl+-` | Zoom out |
| `Ctrl+Num *` | Reset zoom |
| `Ctrl+Mouse Wheel` | Zoom in/out |

### Code Completion

| Shortcut | Action |
|----------|--------|
| `Ctrl+Space` | Open suggestion popup |
| `Enter` or `Tab` | Accept suggestion |
| `Escape` | Dismiss popup |
| `Up` / `Down` | Navigate suggestions |
| `Page Up` / `Page Down` | Scroll suggestions |

### Reformatting

| Shortcut | Action |
|----------|--------|
| `Ctrl+T` | Reformat document |
| `Ctrl+Shift+R` | Open reformatter settings |

### Hex Editor

| Shortcut | Action |
|----------|--------|
| `Ctrl+Shift+H` | Toggle hex view |
| `Ctrl+I` | Toggle Data Inspector |
| `Tab` | Switch hex/ASCII pane |

---

## Settings & Persistence

theDANE remembers your preferences automatically:

| Setting | Where stored |
|---------|-------------|
| Application theme | Windows Registry (`HKCU\Software\theDANE`) |
| Editor style set per language | Windows Registry |
| Recent files (last 10) | Windows Registry |
| Hex inspector font size | Windows Registry |
| Show splash on startup | Windows Registry |
| Explorer shell integration | Windows Registry (`HKCU\Software\Classes`) |
| Reformatter profiles | `Documents\ReformatterProfiles\` (portable `.cfg` files) |

No configuration files need to be edited manually to get started — everything is managed through the UI.

---

## Verifying File Integrity

Each release of theDANE is accompanied by a `theDANE.sha256` file containing the SHA-256 hash of the executable. This lets you confirm that the `.exe` you downloaded is the exact file that was published — unmodified and uncorrupted.

Open a terminal in the folder containing `theDANE.exe` and run one of the following commands:

**PowerShell:**

```powershell
(Get-FileHash theDANE.exe -Algorithm SHA256).Hash
```

**Command Prompt:**

```cmd
certutil -hashfile theDANE.exe SHA256
```

Compare the output with the contents of `theDANE.sha256`. If the two strings match exactly, the file is authentic.

---

## Advanced: Under the Hood

This section is for those curious about the technology and architecture behind theDANE.

### Built With

theDANE is written entirely in **Object Pascal (Delphi)** using the **VCL** (Visual Component Library) framework. It compiles to a native Win32/Win64 executable with no external runtime dependencies.

### kbmVCL Components

The editing engine, syntax highlighters, and reformatter are provided by the **kbmVCL** component suite from Components4Developers. The key components used are:

| Component | Role |
|-----------|------|
| `TkbmVCLSyntaxMemo` | The core editor control — handles text editing, multi-caret, undo/redo, selection, code folding, bracket matching, code completion, bookmarks, and rendering |
| `TkbmVCLHexEditor` | The hex editor control — dual-pane byte editing, data inspector, find, and undo |
| `kbmSyntaxMemoTypes` | Tiered line storage layer — adaptive string/rope representation per line, tiered list for the line collection |

**Syntax highlighters** (one per language):

| Unit | Language |
|------|----------|
| `kbmSyntaxHighlighterPascal` | Pascal / Delphi — includes a full BNF grammar and reformatter |
| `kbmSyntaxHighlighterSQL` | SQL — multi-dialect keyword sets (ANSI, Oracle, MSSQL, PostgreSQL, MySQL, SQLite) |
| `kbmSyntaxHighlighterXML` | XML — tags, attributes, entities, CDATA, DOCTYPE, processing instructions |
| `kbmSyntaxHighlighterJSON` | JSON — keys, strings, numbers, booleans, escape sequences |
| `kbmSyntaxHighlighterHTML` | HTML — with embedded CSS/JS awareness |
| `kbmSyntaxHighlighterJavaScript` | JavaScript / TypeScript — template literals, regex, JSX-aware |
| `kbmSyntaxHighlighterCSharp` | C# |
| `kbmSyntaxHighlighterCSS` | CSS — selectors, properties, values, units |
| `kbmSyntaxHighlighterMarkdown` | Markdown |
| `kbmSyntaxHighlighterKeyValue` | INI / Properties / .env files |

**Reformatter infrastructure:**

| Unit | Role |
|------|------|
| `kbmSyntaxHighlighterReformatter` | The BNF-driven and token-based reformatter engines |
| `kbmSyntaxHighlighterReformatterProfiles` | Profile management (load, save, import, export, clone) |
| `kbmSyntaxHighlighterReformatterSettings` | Reformatter settings editor UI and style sets |

### Application Units

| Unit | Role |
|------|------|
| `theDANE.dpr` | Main project file — startup sequence, single-instance management, VCL style resource linking |
| `uMain.pas` | Main form — tab management, menus, toolbar, profile system, theme switching, shell integration, single-instance file handoff |
| `uEditor.pas` | Editor frame — wraps `TkbmVCLSyntaxMemo`, manages file I/O, status updates |
| `uThemeManager.pas` | VCL style loading, switching, and runtime color queries for legacy controls |
| `uProfileSettings.pas` | Profile configuration editor dialog |
| `uSplash.pas` | Splash screen with timed display, fade-out animation, and optional quick-start mode |

### Performance: Handling Large Files

theDANE is designed to remain responsive even with very large files and extremely long lines. Several architectural decisions make this possible:

**Viewport-only rendering.** The paint cycle only processes lines that are actually visible on screen. The editor tracks a `TopLine` (the first visible line) and computes how many lines fit in the current window height. Only those lines — plus a small buffer — are measured, styled, and drawn. Scrolling simply updates `TopLine` and repaints. This means a 100,000-line file renders no slower than a 100-line file, because only ~40–60 lines are painted per frame regardless of file size.

**Incremental syntax highlighting.** The lexer does not re-tokenize the entire file on every keystroke. Instead, each line caches its end-of-line lexer state (e.g. "inside a block comment", "inside a string"). When a line is edited, only that line and any following lines whose start-state might have changed are re-lexed. For typical edits deep in a file, this means just 1–3 lines are re-processed. A full re-lex is only triggered when switching languages or loading a new file.

**On-demand fold scanning.** Code folding regions are scanned within a configurable window around the viewport (default: 500 lines above and below). Folds outside this window are not tracked, keeping memory use and scan time bounded. The scan range shifts as you scroll, and previously scanned regions are cached until the viewport moves beyond a threshold.

**Tiered line storage.** Internally, lines are managed by a unified storage layer that adapts its representation to the content. Short, ordinary lines are stored as simple native strings with reference-counted copy-on-write semantics — insertions and deletions are just list splices with minimal overhead. When a line grows beyond a configurable threshold (default 4 KB), the storage transparently promotes it to a tiered rope-like structure, which keeps insert, delete, and substring operations efficient even on extremely long lines (e.g. minified JavaScript or large single-line JSON). If the line later shrinks below half the threshold, it is automatically demoted back to a simple string to avoid unnecessary overhead. The same tiered principle is applied to the line list itself, so inserting or deleting lines in the middle of a million-line file does not trigger large block moves. This dual-tier approach means theDANE handles both typical source files and pathological edge cases — huge files, enormous single lines — without requiring any manual configuration.

### Limitations at Scale

While the editor handles large files well, a few features have inherent scaling characteristics worth knowing about:

**Pair matching** searches the entire file when looking for a matching bracket or `begin`/`end`. For files with tens of thousands of deeply nested constructs, a pair match at the top of a very large file may take a noticeable moment. In practice this is rarely an issue because most pair jumps involve nearby constructs.

**Code folding** is bounded by the fold scan distance (default 500 lines around the viewport). Fold markers for regions that start or end far outside this window may not appear until you scroll closer. You can increase the scan distance if needed, at the cost of slightly higher CPU use during scrolling.

**Find All** searches the entire file linearly and highlights every match in the gutter. On very large files (hundreds of thousands of lines), Find All may take a moment to complete.

### Theme System

The four application themes are implemented as **VCL Style** packages (`.vsf` files). The VCL style engine skins every standard control — including common dialogs like File Open and File Save — through `TStyleManager.SystemHooks`.

Custom `.vsf` files can be deployed in two ways:

1. **External**: place `.vsf` files in a `styles` subfolder next to the `.exe`. They are discovered and loaded automatically at startup.
2. **Embedded**: compile `.vsf` files into a Windows resource (`.res`) and link them into the executable at build time.

A handful of legacy controls that the VCL style engine cannot reach (the `TTabSet` control and some programmatically created labels) are themed manually by querying color values from the active style at runtime through helper functions in `uThemeManager`.

---

*theDANE — the Danish Advanced Native Editor · forged by kbm · Components4Developers*
