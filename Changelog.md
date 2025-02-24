
[![download](https://img.shields.io/badge/Download-Installer-blue.svg)](https://markdownmonster.west-wind.com/download)
[![Web Site](https://img.shields.io/badge/Markdown_Monster-WebSite-blue.svg)](https://markdownmonster.west-wind.com)

### 2.8

*<small>not released yet</small>*

* **Enable Mermaid Charts By Default**  
With wider support of Mermaid in various rendering platforms including GitHub, Mermaid rendering is now enabled by default. There's still a Setting flag that can be used to turn checking for Mermaid code on and off which improves load and render speed very slightly. *Note: If you're updating a previous version, your current setting will not change so if it was set at default of `false` it'll continue to stay that way and have to be manually enabled. You can use Tools|Settings|Mermaid to set this value.*

* **Command Palette: Added Font Settings**  
You can now access the font settings in the Visual Settings Editor via `Ctrl-Shift-P Font`. Also added a tooltip to the font size dialog to point at the Settings and Command Palette shortcuts.

* **Folder Browser Keyboard Navigation now Previews**  
When navigating the folder browser with the up and down keys, the editor now displays a preview of documents similiar to the behavior when single clicking on a document. Editable (Markdown, text and other known editable formats) are opened in preview mode, meaning once you navigate off the document is closed or replaced by the next preview document, unless the document has been edited or explicitly opened as a full document.


* **Update: Default Font Size to 16px**  
Set default font-size a little smaller to prevent very low res displays from displaying to big of a font initially. This will make fonts smaller for hi-res displays, but people that have these are used to having to adjust font-sizes up typically.

* **Fix: Change Scrollbar Sizes for Editor and Preview**  
The default scrollbar sizes for the Editor and Previewer have been bumped up slightly to better work with hi-res displays and sizing has been switched from hard pixel sizing to `em` sizing. Previewer and Editor scrollbar styling can be applied in the generic `Editor/editor.css` and `PreviewThemes/MyTheme/theme.css` for the specifically active theme.


* **Fix: Folder Browser File Renaming Issues**  
Fix issue where rename operations would in some cases not save pending changes and wouldn't delete the originally renamed file. Error was introduced during async conversion and due to timing issues. Fixed. [#986](https://github.com/RickStrahl/MarkdownMonster/issues/986)

### 2.7

*<small>October 18th, 2022</small>*

* **Add File Info Tooltips for Preview Tabs**  
Preview tabs now show the filename and display a tooltip that has file information in the same way as editor documents do.

* **Add Image Size to Image File Tooltips**  
Images in the Folder Browser and open Tabs now display image tooltips that include image size (width x height) and image DPI.

* **Preview Tab File Names and Tooltip**  
Preview tabs for non-document files now show the filename and file tooltip info just like document tabs. Previously, non-document tabs behaved differently due to the missing document instance.

* **Command Palette: Add Speech/Read Aloud Commands**  
Add commands for reading aloud to the command palette. Access via *Speak* or *Read Aloud* keywords.

* **Command Palette: Many more Commands Added**  
All List operations (plain, numbered and checkbox), Emojii, YouTube embedding, Find in document, Find Files, Find in Files, among otherrs. To access Command Palette press `Ctrl-Shift-P` or use the searchbox in the Title bar.

* **Fix: Refresh Cached Images from Clipboard**  
Fixed issue where pasting an image from the clipboard would not properly refresh the preview and scroll to the top of the preview - until next cursor movement. Also fixed caching issue where pasting new same name image would cache and not show the new image.

* **Fix: *Open With...* From Folder Browser**  
Open With stopped working apparently due to a framework change that related to the `UseShellExecute` setting which has to be explicitly set off to open the dialog.

* **Fix: Startup Path Fixup for `CommonFolder`**  
Fixed issues with the common folder location that requires that some files and folders to be stored on the local machine. Previously the `InternalCommonFolder` was erroneously the same as `CommonFolder` causing some look up issues

* **Fix: Folder Browser External File Update and File Info**  
Fix issue where newly added files and files that have changed did not reflect current file information. Change detection now reloads updated file information.

* **Fix: Right Click Focus in Folder Browser**  
Fix folder browser focus when right clicking on files. In some situations the selection of the previous item would not clear and the context menu would pop up for the previous selection. Updated logic to explicitly select on right click. Fixed.

* **Fix: Context Menu Key not working**  
Fix the Context Menu key on keyboards not working. Re-enabled, but behavior is not ideal as it displays at mouse cursor, not at editor position. 

* **Fix: Escape Pipe `|` Characters in Grid Tables**  
Pipe characters in Grid Tables have to be escaped and using pipes in Grid Tables prerviously broke Grid parsing as the `|` was interpreted as a column break. Fixed by now properly escaping `|` with `\|` in the Markdown editor and using plain `|` in the Table Editor.

* **Fix: Pull Issue with Pull when using Branch other than Master**  
Fixed issue with Pull not respecting the active Branch in the Git dialog. ([#976](https://github.com/RickStrahl/MarkdownMonster/issues/976))

* **Fix: Pop up Context Menu with Context Menu Key at Cursor Position**  
Fix issue where keyboard Context Menu key was not opening the context menu at the current cursor location.

* **Fix: Cached WebBrowser Environment Location**  
Fixed browser environment location which now properly uses the local machine common path, rather than a potentially shared common path. Sharing in a common path could cause corruption and unexpected browser lockups and crashes.

* **Fix: License Unregistering**  
Fixed issue with licenses getting unregistered due to a registration issue on the server end missing the version number. Fixed recent licenses by adding versions properly, and new licenses creating with product version supplied.

### 2.6
 
<small>June 30th, 2022</small>
 
* **[Drag and Drop Link Insertion from Document Outline into Editor](https://markdownmonster.west-wind.com/docs/_55o1bd4n1.htm)**  
You can now drag a document outline selection into the open Markdown Document as a link that points at the `#Hash` id in the document. <small>([#936](https://github.com/RickStrahl/MarkdownMonster/issues/936))</small>

* **[Support for Async Code Snippet Templates](https://markdownmonster.west-wind.com/docs/_5gs0uc49h.htm#c-code-execution)**  
Code Snippets now support `await` calls in C# expressions or code blocks. This is necessary for accessing many of the `Model.ActiveEditor` methods that effect editor behavior (most commonly `await Model.ActiveEditor.GetSelection()`). 

* **[Support for Structured Statements in Code Snippet Templates](https://markdownmonster.west-wind.com/docs/_5gs0uc49h.htm#c-code-execution)**  
C# snippets now also support structured code blocks using `{{% <statement> }}` that are directly embedded as code. This allows for `if` and `for` type structured statement blocks that can bracket other text or expression. But it also allows for arbitrary C# code blocks to be executed and act as integrated code.

* **Improved Snippet Startup Speed**  
With the new Roslyn integration which runs in-process,  startup speed of first snippet activation  is much improved even on a cold start. Additionally the `PreloadCSharpCompiler` configuration flag in the Snippets addin can reduce startup speed down to a fractional second.

* **Add Subscript and Superscript Markup Operations**  
Added sub and superscript to the Extra Markdown operation drop down menu which creates `<sub></sub>` and `<super></super>` wrappings around text selections.

* **Keybindings for Numbered List and CheckBox List**  
Added keybindings for number list (`ctrl-shift-l`) and checkbox list (`ctrl-alt-l`).

* **Many Updated Command Palette Commands**  
Added many additional Commands to the Command Palette including many more markup operations, a number of toggle settings, and view options.

* **Add ShortCut Keys to the Web Lookup links in Link Dialog**  
The link dialog now has shortcut keys for the `Search on Web` (alt-s) and `Search and Link` (alt-l) buttons in the Link Dialog to allow for better hands free operation of these two operations.

* **Add Preview And Sidebar Width to Window Presets**  
The Sidebar Window drop down now allows for setting the preview and sidebar panel widths in addition to a Window size. 

* **Update Ace Editor to v1.5**  
Updated to latest Ace Editor version (1.5.1). Several small additional tweaks to the markdown editor behavior for the editor.

* **Fix: Format PipeTable with Line Breaks in Header**  
Fix issue where line breaks (via `<br>`) in Pipe Table headers was breaking the formatter and resulted in not being able to format the table or edit it in the Table editor. The change now formates based on the full single line instead of the individual line lengths which - assuming the table width is not too wide - will still nicely format a table even with linebreaks. <small>([#959](https://github.com/RickStrahl/MarkdownMonster/issues/959))</small>

* **Fix: GridTable with leading Spaces in multi-line Cells**  
Fix issue where multi-line cells in a grid table would strip leading spaces resulting in potentially lost markdown formatting. <small>([#961](https://github.com/RickStrahl/MarkdownMonster/issues/961))</small>

* **Fix: GridTable white space issues**  
Fix issue where white space is is not cleaned up properly when deleting lines from a cell in a gridtable. 
<small>([#962](https://github.com/RickStrahl/MarkdownMonster/issues/962))</small>

* **Fix: Preview not rendering first Mermaid Diagram**  
Fixed issue where entering a first Mermaid diagram into a page will not render until the page or tab is fully refreshed. This is due to the way MM caches the page and only replaces content, so when Mermaid is added after the page is loaded the script was not available to transform Mermaid charts. Added logic to explicitly check for Mermaid script and refresh page if not found. <small>([#960](https://github.com/RickStrahl/MarkdownMonster/issues/960))</small>

* **Fix: Display full Git Error Messages for Commit and Push Operations**  
Change display of error messages so the full message is displayed instead of the status bar only message which is often truncated. Display a message box instead so the full error can be captured. Important due to the new Git Security `safe.directory` features that require (`git config --global --add safe.directory <path>`)


#### Breaking Changes

* **Recommend a full Uninstall/Reinstall**  
The updated Roslyn support in version 2.5.5 and later changes a number of runtime dependencies and it's recommended that if you were running a pre-2.5.5 version you completely uninstall Markdown Monster and reinstall in order to clean the installation folder of old dependencies.

* **Razor Support removed for Code Snippet Templates**  
Razor language support has been removed from the Snippets addin as the new C# script syntax supports similar functionality for scripting. Razor has been problematic and adds a host of dependencies and inhibit future migration to .NET 6.0. To migrate you can move your scripts to the [Handlebars style C# syntax](https://markdownmonster.west-wind.com/docs/_5gs0uc49h.htm#text-with-c-expressions).


### 2.5

<small>May 10th, 2022</small>

* **[Command Palette](https://markdownmonster.west-wind.com/docs/_6b10l43hf.htm) (ctrl-shift-p)**  
You now have a command palette that lets you search for most operations and apply them. There's a searchbox in the Windows title bar, where you can type commands to find and execute them. While this doesn't replace native shortcuts it provides for additional discovery of available commands and options.   
*commands are still being added but most common functionality is available now*

* **[Folder Browser Markdown Preview Modes](https://markdownmonster.west-wind.com/docs/_6bw0k5a23.htm)**  
Added a Folder Browser configuration switch `FolderBrowser.MarkdownPreviewMode` that lets you choose between the previous `EditorPreview` mode that displays a transitory document that is closed when another document is accessed **unless the document has been changed**, or the new `HtmlPreview` mode which displays the rendered Html view. Preview mode is triggered by a single click in the Folder browser, while double click (or **Open in Editor**) opens the document as a normal fully editable document.

* **Improved Document Loading**  
Updated the document load sequence to improve performance and consistency loading documents. Most performance gains can be seen around navigation from the folder browser which reduces extra document open/close operations by now reusing tabs in some situations. Overall better performance and less document load flicker.

* **Improved Preview Document Loading in Folder Browser** 
When clicking at editable documents in the Folder browser, documents are initially displayed in *Preview Mode* which is a transient tab that disappears until a change is made or - now - you click into the preview mode document. Improved how these tabs are created and they are now reused to provide quicker and much smoother navigation of Markdown documents.

* **Clicking into Preview Document now switches to Full Document**
Previously preview document tabs required changing text in the document to trigger becoming a 'normal', full document. Now, clicking into the documentis all it takes to make it a full, non-transitory tab.

* **Improved Markdown List UI on Toolbar**  
Added support for Checkbox Lists. The 3 list options now show on  drop down with the main button still adding a plain list as before. The three options are:  **Standard List**, **Numbered List**, **Checkbox List**. Also improved handling of single line selections or no selections on line which now always add the list operator *to the front of the line* unlike before at the cursor position.

* **Remove Leading White space on Extra Markdown Features Menu**  
This option on the Extra Features Dropdown strips all common leading white space from a multi-line selection. This is useful for stripping off white space from code pasted from a code editor that has indentation or other text that might be otherwise indented. Removes white space that is common to all lines of text. (then again for code use `alt-c` code pasting do this and fencing automatically)

* **Sticky Search Subfolders for Folder Browser File Searching**  
The subfolder option for inline and explicit search pane searches is now sticky via a `FolderBrowser.SearchInSubFolders` configuration setting. Once updated it's remembered across MM sessions. [#934](https://github.com/RickStrahl/MarkdownMonster/issues/934)

* **Add Drag and Drop Links from Favorites**  
You can now drag favorites into a document and link to the file in the same way you can for the Folder Browser. Not super practical unless the favorite link is relative to the current file or project.

* **WebLog Custom Fields Context Menu**  
Added a Custom Fields context menu which draws values from a user defined menu of custom weblog post values (such as `mt_githuburl`, `mt_location`, `mt_date`) etc. These are typically user defined values that have special meaning on the server, but can be painful to remember if you're using them for custom values. You can now define any custom keys in the Weblog configuration as `WeblogConfig.CustomFieldNames`.

* **Make Spell Underlining Stylable**  
Add logic to allow customizing the way the spell check highlighting looks via `editor-user-extesions.css` and the `.ace_marker-layer .misspelled` style. Allows changing colors, thickness etc. as other page elements. This was previously hardcoded in the custom spell check logic MM uses.

* **Fix: Cleanup Folder Browser Markdown Document Navigation**  
Fixed several issues related to document navigation in the Folder browser that resulted in overly janky document opening and occasionally double opened documents.

* **Fix: Folder Browser Double Click Flashes and Occasional Load Failures**  
Fix issues related to double clicking in the folder browser that occasionally would cause documents to double load or fail to load and display a blank document.

* **Fix: Non-intended Drag and Drop Operations**  
Fix problem where slight mouse movements while clicking would trigger drag and drop operations that could cause accidental file moves. Widened drag minimums and fixed location pinning that was off and previously resulted in over eager drag operations.

* **Fix: Html Edit/Format Table Detection Failing**  
Fixed issue where Edit and Format Table context menu choices were not working when trying to open the Table editor. [#932](https://github.com/RickStrahl/MarkdownMonster/issues/932)

* **Fix: Table Editor with Pipe char in Pipe and Grid Tables**  
Fix bug where editing or formatting a Pipe or Grid Table that contains **escaped pipe characters** - ie. `\|`- would create additional columns rather than capturing the pipe character. Fixed.
[#933](https://github.com/RickStrahl/MarkdownMonster/issues/933)

* **Fix: MM won't launch if an older WebView Runtime is installed**  
MM by default won't launch if an older WebView runtime is installed and prompt for re-installing the latest WebView runtime. Usually this is not a problem but in some cases an older version may be installed and the app should be allowed to run (such as when running Canary builds). You can now override this behavior via a
`System.IgnoreWebViewVersionMismatch=true` configuration setting.

* **Fix: Toggle External to Preview Browser**  
Fix issue where the internal preview would not display when toggling from external to internal previewer. Previously you had to manually toggle the Previewer's visibility. Now external -> internal properly shows the internal previewer activated.

* **Fix: Footnote Link Navigation in Previewer**  
Fix issue with clicking on Footnote links and references not navigating the document to the footnote. Fixed. [#937](https://github.com/RickStrahl/MarkdownMonster/issues/937)

### 2.4

<small>March 10th, 2022</small>

* **[You Tube Embedding Window](https://markdownmonster.west-wind.com/docs/_69d0zwck0.htm)**  
You can now embed YouTube videos into a document using the YouTube Widget on the toolbar. You can paste a YouTube Url (watch, embed or shortcut), preview the video, set a title and default resolution, then embed it into the page as an HTML fragment. The HTML is formatted to auto-size both horizontally and vertically adjusted to the width of the document.

* **[Twitter Tweet Embedding Information](https://markdownmonster.west-wind.com/docs/_69e0rchvh.htm)**  
MM doesn't include special UI to embed Tweets into your content as Twitter provides an easy way to pick up ready to paste HTML that you can paste into a Markdown document. However to make this process more discoverable we've added a shortcut Tweet toolbar button in the Extension Tags dropdown of the toolbar. This button links to a help topic that describes the two steps to create an HTML widget on Twitter and paste it into markdown.

* **[Updated Gist Embedding Addin](https://github.com/RickStrahl/GistIntegration-MarkdownMonster-Addin)**  
Although external, this add in is used by quite a few people. The addin has been updated with a few UI updates to make it quicker and easier to use. You can now also copy a Gist id or script tag for existing Gists, delete Gists. Save to and Load From Gist also have a host of updates to make it easier to access these options from the Gist Listing view.

* **Added Markdown HtmlEncode and UrlEncode Shortcuts**  
You can now easily HtmlEncode a block of text or UrlEncode a value using shortcuts on the Extended Markdown Operations dropdown from the toolbar.

* **Alt-X Shortcut for dropping down Extended Markdown Features**  
There's new Alt-X (default) shortcut key that drops down the Extended Markdown features from the toolbar for quick access. This menu has things like Upper/Lower Case, bolditalic, HtmlEncode, UrlEncode etc. Also updated the [documentation for Markdown Monster Shortcut keys](https://markdownmonster.west-wind.com/docs/_4rd0xjy44.htm).

* **Improved Markdown Quote Handling (ctrl-q)**  
Quote handling (`> content`) now better supports single line or no selections, prepending the quote mark at the beginning of the line. MM now also checks for already quoted lines and doesn't double quote any longer.

* **[Command Line Opening of Files using `filename:lineno` Syntax](https://markdownmonster.west-wind.com/docs/_5fp0xp68p.htm#editor-ui-commands-mm.exe)**  
In addition to the `--lineno` command line switch you can now also use `:lineno` at the end of a filename to open a file at that line. Example: `c:\temp\test.md:22`. The individual file lineno overrides the `--lineno` parameter which works only against the first opened file.

* **Support For Better Html Document Previews**  
There's now better raw HTML document editing support (ie. `.html files`) in Markdown Monster as previews now show related resource content. You get many of the same live preview benefits that are also available with Markdown documents. Images, styles, scripts and other related assets now correctly load in the previewer for HTML documents via an inject `<base>` tag that points back to the document's host folder. [#907](https://github.com/RickStrahl/MarkdownMonster/issues/907)

* **Addins: Fix Addin Repository Urls**  
Due to changes at GitHub related to branch names etc. we've had to change the way addins report their default Urls. The new Urls require providing a branch name (ie. `/tree/main` etc. suffix to repo). This is required since we can no longer assume a `master` or `main` branch.  
**This is a breaking change** - the new addin repository Urls break old applications so for older v2 versions the Addin Manager is broken. *Please update to latest*.

* **Addins: Add AdditionalDropdownMenuItems to AddinMenuItem**  
You can now add additional menu items to the Addin drop down menu on the Toolbar. This allows addins to be more obvious about features available by the addin **in one place**, in addition to optional integration into the Main Menu (which requires a little more work).

* **Addins: New `OnApplicationInitialized()` Handler**  
This handler replaces the `OnModelLoaded()` handled which more clearly identifies the purpose of this handler. This method is now set up to be the default Addin configuration method where the default Id, name and menu item configuration is placed instead of in `OnApplicationStart()`. The problem with `OnApplicationStart()` is that it fires before there is any app context - no Window, no Dispatcher, no Model. `OnApplicationInitialized()` ensures the Window is instantiated, a Dispatcher is available and the `AppModel` is available.  

* **Addins: Updated `dotnet new` and Visual Studio Addin Project Templates**  
We've updated both types of templates in line with the changes for `OnApplicationInitialized()` and cleaned up the templates and added additional comments to the generated addin and configuration classes.

* **Updated: [Mermaid](https://markdownmonster.west-wind.com/docs/_5ef0x96or.htm) and [MathMl](https://markdownmonster.west-wind.com/docs/_59l0mv2uw.htm) now work without requiring Allow Script Rendering**  
These two RenderExtensions provide diagram and math equation rendering into Markdown now work without explicitly requiring the `AllowRenderScriptTags` option to be set as they don't actually require JavaScript code inside of the rendered Markdown body any longer. They are still disabled by default but can now be enabled via just the `UseMermaid` and `UseMathematics` configuration settings. A restart is required for changes to these values as the RenderExtensions need to be reloaded.

* **Fix: Re-enabled the [Microsoft DocFx Markdown Parser](https://markdownmonster.west-wind.com/docs/_5750qtgr2.htm#the-official-microsoft-docfx-markdown-parser)**  
We temporarily had to remove the Microsoft DocFx parser, due to a dependency version conflict with the MarkDig parser. Now that MarkDig versions have been re-synced to the latest versions the `DocFx` Parser is available again from the Markdown Parser dropdown on the toolbar.

* **Fix: Focus with New and Non-Existing Documents from Command Line**  
Fixed focus issues for opening a new or non-existing document from the command line. Focus now starts in the editor.

* **Fix: Presentation Mode preserves Folder Browser Sidebar Visibility**  
When you use Presentation Mode to toggle between edit and presentation modes, MM now remembers and restores the preview state of the left folder browser sidebar.

* **Fix: GridTable LineFeed Issues**  
Fix Grid table edit and format table inputs when table cells have empty lines. These empty lines are no longer stripped. Fix extra linefeed at end of generated GridTable output/paste operations.
[#901](https://github.com/RickStrahl/MarkdownMonster/issues?q=is%3Aopen+is%3Aissue)

* **Fix: `markdownmonster:` Protocol Handler with text**  
Fix bug where the `markdownmonster:untitled.base64:<data>` handler was not assigning the document data passed into the newly opened document. Fixed.

* **Fix: GridTable Parsing with Back to Back Tables**  
Fix Grid Tables when tables are butted up against each other without separating lines. Note: This is legal but the preview won't actually render it and most Markdown parsers fail to render this correctly. Although the editor now supports this functionality, it's best to use a blank line between two tables to ensure it renders correctly regardless of parser. *[#904](https://github.com/RickStrahl/MarkdownMonster/issues/904)*

* **Fix Mermaid Rendering**  
Fix Mermaid rendering for certain Mermaid content by Html Encoding the body to render. Previously the unencoded text would fail to render correctly. Encoding is applied only the `` ```mermaid`` sections, not the raw Html `<div class="mermaid">` which is used as is meaning that user is responsible for encoding. [#911](https://github.com/RickStrahl/MarkdownMonster/issues/911)

### 2.3 

<small>January 14th, 2021</small>

* **[Support for Long Path Names](https://markdownmonster.west-wind.com/docs/_68d0r8rej.htm) (if enabled in Windows)**  
Added improved support for long path names in MM via manifest setting that allows you to open and save documents and assets with paths longer than the Windows `MAX_PATH` (255 chars). It now also works for many of the external application integrations. For this to work, Long Path Names have to be enabled in Windows (10/11) via registry or group policy setting.

* **Improved Document Load Time**  
We've improved the way editor and preview documents get loaded, which now load faster, with less flicker and without the occasional brief document load error page displayed.

* **Add File Updated and Created to Folder Browser Tooltip**  
Files and folders now display both created and updated dates in the File and Folder Browser.

* **Document Tab ToolTip now includes File Information**  
The document tab tooltip now displays file information including file size and updated and creation times, using similar format to what's used for tooltips in the Folder Browser.

* **Move Symbol Configuration for Italic and Soft Line Breaks Characters**  
Moved the Symbol configuration that allows you to specify what symbols to use for italic (`*` or `_`) and Soft Line Breaks (`  ` or `\`) into the main Markdown configuration so it's visible in the interactive editor. Previously these two values were nested in a sub key below the Markdown configuration and not visible in the editor. These symbols are used by the Toolbar/Shortcut insertion operations.

* **Improved Drag and Drop Operations in the Folder Browser**  
Updated drag and drop logic that affects initial drag state activation to be less sensitive resulting in fewer accidental drag operations. Also fixed various selection and drop issues as well as better supporting dropping shell files into the Folder Browser.

* **Fix: Folder and File Visibility when a Filter is Set**  
Fix issue where new files or folders added would not respect the search filters and show up regardless of the filter settings.

* **Fix: Lockups on opening Documents**  
Fixed issue with lockups when opening documents in some situations such as after search, dragging items. 

* **Fix: Document Title Display with Full Path when switching from Preview** Fix an issue when switching from a Preview document to an edited document where the tab title would display the path even though there's no duplicate item. Correct behavior is to display only the filename when a single file with that name is open.

### 2.2

<small>November 23rd, 2021</small>

* **Import from JSON to Markdown Table**  
You can now import JSON object arrays as Markdown tables from file or the clipboard. Field names are mapped to headers values as row content. An optional field exclusion list can be applied.

* **Move Table Rows Up and Down**  
You can now move table rows in the Table Editor, up and down via context menu or `alt-up` and `alt-down`.

* **Keyboard Navigation for Common Table Editor Cell and Row Operations**  
You can now use keyboard navigation for moving rows up and down (`alt-up`, `alt-down`) and moving columns left and right (`alt-left`, `alt-right`). You can also insert rows above and below using (`alt-shift-up`, `alt-shift-down`).

* **Copy To Clipboard for Markdown Tables in Table Editor**  
The Markdown Table Editor has a new Copy button to copy the currently active table in the editor to Markdown and the clipboard. This allows using the editor for easy pasting of Markdown Tables into other applications.

* **mmCli cleanup-webview Command to clear WebView Environment**  
Added command line helper to clear out the WebView Environment that MM uses. The environment is private and separate from global settings, and only used for MM's local rendering of generated content.


* **Spellchecking: Look up on Web**  
The spell checking context menu now has an option to **Lookup on Web** when a spell checking error is found. This is useful if you have no match in the list of suggestions and need to find out correct spelling. Opens Search page in your specified search engine.

* **Add Neeva and Brave to configurable Search Engines for Lookups**  
Add the Neeva and Brave search engines to the list of supported search engines for various lookup operations. Look up operations are available for finding and embedding URLs, and the spell checker for example.

* **Copy Favorites Path to Clipboard on Favorites Context Menu**  
You can now copy the current favorite item's path to the clipboard from the Favorites Context Menu.

* **Command Snippets: Warm up C# Compiler**  
If you're using snippets that contain C# code (Expressions or Razor) there's now a configuration option that allows preloading the C# compiler to speed up first compiled snippet operation. Also fix code focus delay issue with Snippet insertion.

* **Fix: Update RelativePath Processing**  
Fix exceptions in Relative Path creation used for dropped and pasted files and images. Fix issue where invalid paths would cause a hard failure due to Path object exceptions.

* **Fix: Favorites Intra Section Drag and Drop**  
Fix issue where dragging a Favorite in section would not 'stay' in the new drop location and revert after short delay.

* **Fix: Control Tab Focus Handling**  
Fix various issues with Control Tab locking the UI and not focusing the cursor. Fixes Ctrl-Tab and Click focus with cursor becoming active in editor for each.

* **Fix: PDF Generation Intermediary HTML File Name**  
Fixed the intermediary HTML filename used when generating PDF files. Previously the HTML file generated was the same name as the PDF file, which could cause conflicts if the HTML file already existed prior to generation. Added `__` prefix to the temp file.

* **Fix: SnagIt Image Capture Embedding**  
Fix issue with SnagIt image embedding from the Screen Capture add-in. Previously, save operation failed silently. Fixed.

* **Fix: Physical Path Formatting for Links and Images**  
When embedding physical file locations into Markdown (in untitled documents mainly or if referencing non-relative locations) paths previously where using Windows style syntax with forward slashes. This worked previously but started failing recently with the WebView renderer. All paths - both physical and relative - are now embedded using URL style forward slashes even for Windows paths.

* **Update: Log more Exception Data**  
Exceptions now log both the top level and base exception to provide a little extra info on failures.


### 2.1

<small>October 12th, 2021</small>

* **Output Generation icons on main Toolbar**  
Added PDF, Print and HTML Output icons to the toolbar to make these features more discoverable and more easily accessible with a single click.

* **Basic Syntax Detection for Pasted Text into Empty Untitled Documents** When you paste content into a new `untitled` document, MM now tries to detect syntax and automatically sets the editor's syntax to this mode. This only applies if the document is empty otherwise the syntax is sticky.
 
* **Remember Table Embedding Mode in Table Editor**  
When you embed a table using the Table Editor window, your last selection is now preserved in a configuration setting `Editor.TablePasteMode`.

* **Set File Sort Order in Folder Browser**  
The context menu in the folder browser now has an option to set the file sort order to Name, Date Ascending and Date Descending. The file order setting is tracked via sticky configuration in `FolderBrowser.FileOrder`.

* **Optional File Browser File Tooltips**  
You can now optionally enable a new `FolderBrowser.ShowToolTips` configuration option to show file information when hovering over files and folders. The tooltip shows the file's full name, parent folder, file size and last write date.

* **PDF specific Preview Theme**  
Added a **Pdf Output** Preview Theme that can be used when printing output to PDF. This theme is specifically designed to work around the differences in PDF output which include printing code with non-syntax coloring, and special font handling in order for code snippets to display properly. You can copy and customize this theme as necessary.

* **PDF Output now lets you set the Theme**  
When you create PDF output via the **Save To -> Save to PDF** dialog, you can now select the theme that is used to render the document. Due to limitations of the PDF rendering we recommend you use the printing specific **Pdf Output** theme which is the default, but any theme will work and you can create your own custom themes for printing.

* **Change: Markdown Link Rendering**  
Changed Markdown link rendering to remove underscore using regular display to make it easier to read links that might have underscores in them. Links now display without link underscore, and only show the underscore when hovering to indicate that the link can be navigated (via Ctrl-Click). There's now also a tooltip to notify you of ctrl-click behavior. 

* **Update: PDF Generation Tools**  
Update to latest tool version of wkhtml2pdf for PDF generation which fixes a number of small rendering quirks in the PDF generation engine. Also added some rudimentary support for emoji rendering in PDF documents since that seems a common theme.

* **Update: [Markdown Monster Addin Templates](https://markdownmonster.west-wind.com/docs/_4ne0s0qoi.htm)**  
Both the Visual Studio and `dotnet new` Markdown Monster Addin templates have now been updated to support v2 Addin projects. The addin interfaces have changed to mostly `Task` based `async`, to make it easier to interact with the async document functionality required for many editor interactions. If you need to update a v1 project to v2, you will need to convert the main addin entry points to updated async signatures (`Task` or `async Task`) instead of the old `void` method types.

* **Fix: Alt Key Handling**  
Fixed a number of issues around `alt` key handling. Fixed issue where some editor commands like `alt-shift` and `alt-ctrl` selection weren't working. This is due to the custom menu activation handling which requires `alt` plus a small delay to trigger now vs. simultaneous key press for `alt` key chords. Editor alt chord commands are expected to be **simultaneous** press operations to work. This fixes block selections, block column selections and a host of other alt key based editor operations.

* **Fix: Favorites Tree Data Entry**  
Fix various issues with the Favorites list where entering a new item would add two items and focus would switch unpredictably. You can now also navigate the list with the keyboard with `Enter` opening the item with editor focus and `Space` opening without editor focus.

* **Fix: Allow Render Scripts State Switches**  
Fix issue where switching the allow render state flag on the menu or in settings wouldn't affect the actual rendering and still allow rendering scripts and `iframe` when rendered. Fixed binding for menu, and updated the refresh mechanism so that open documents are updated with the new setting and refreshed (from menu update).

* **Fix: Startup Menu Folder Opening**  
Fix issue Startup Screen folder opening issues where clicking on the folder icon next to the file, would not reliably open the Folder Browser. Fixed.

* **Fix: Tabs not auto-activating when loading from CLI**  
When loading files from the command line files would not open properly in the editor, with tabs opened but not activated and showing an empty preview. Fixed.

* **Fix: Search Settings in Settings Dialog**  
Fix issue with Search Settings entry which was hanging up and not immediately refreshing the entered text. Reduced delay and ensured that operation occurs in dispatched mode to see the change.

* **Fix: WordPress Publishing Thumbnail Image Failure**  
Fix issue with the WordPress publishing mechanism where if thumbnails are published the addin would fail due to a data type error.

* **Fix: EnableBulletAutoComplete**  
Fix this setting so it works on initial document load. Previously the setting only worked after the document was 're-activated'. Fixed.

* **Fix: Edit CenteredMode Pixel Width in Menu**  
Fixed focus issue in the Centered Mode editor document width that determines how wide the editor column to actually edit is. This allows creating of white space around text if the size of the overall edit pane is larger. Fixed issue where focus could not be set easily in the menu option, which made it hard to edit the value. Fixed.

* **Fix: Configuration Editor Click to Jump to Json Editor Links**  
Several configuration options that edit a collection of items, have links in the configuration editor. These links now properly open the JSON configuration file and jump to the appropriate section in the JSON document. Also fixed focus issue for JSON activation by closing the visual editor.

* **Fix: Remember last document location in Recent Documents**  
Last document location was no longer saving when documents were closed (due to async changes). Value is now picked up again before saving and applied when recent documents are opened.

* **Fix: Adding links as Link Collections**  
Fixed issue where **Add Link Collection** in the Paste Link dialog was failing and not producing a link.

### 2.0.5 - Official release of v2.0

<small>July 20th, 2021 &bull; [Release Blog Post](https://weblog.west-wind.com/posts/2021/Jul/22/Markdown-Monster-20-is-here)</small>

* **Use WebView2 and Chromium for all Web Rendering including Editor**  
Markdown Monster now uses a Chromium based browser for **all Web rendering** including the Editor, the Preview, the Table Editor, Code Windows, and Browser Dialogs. Previously only the Preview was optionally enabled by using the Chromium Preview addin. The Addin is no longer needed as all content always uses the Chromium engine. This improves rendering fidelity and also provides better responsiveness due to asynchronous rendering of content which allows for larger content to be displayed and synced while typing.

* **Table Editor Improvements**  
With Chromium rendering a number of odd IE browser bugs are fixed that affected navigation and selection in the old version. Table Editor can now **Move Columns** to the left or right.

* **64 bit Application**  
With the removal of the IE based Web Browser control, Markdown Monster can now run as 64 bit application again. 32 bit mode is still possible on 32 bit systems as well.

* **Allow Swapping Editor and Preview Location**  
You can now swap the editor and preview location via a new **View->Swap Editor and Preview Location** menu option and a via Editor/Preview Splitter Context Menu.

* **New Splitter Context Menu**  
Added a new context menu that displays options for swapping editor and preview, entering presentation mode and toggling the preview display.

* **[Track Active Document in Folder Browser](https://markdownmonster.west-wind.com/docs/_4wu1cjyka.htm)**  
As a heavily requested feature, we've added support for optional document tracking in the folder browser. Using the `FolderBrowser.TrackDocumentInFolderBrowser` configuration switch (also via  a toggle button in the Folder Browser) any time you change the document the Folder Browser navigates to that file.

* **Improved Folder Browser Navigation**  
Folder browser navigation now shows previews for most text type documents in 'inactive' mode that is temporary until the next document is accessed. Documents become 'active' once you edit the document or double click to explicitly open for editing. Single click now also previews any non-edit formats externally, like PDFs, Office docs, etc. Executables open selected in Explorer but are not executed. Drag and Drop start operations are now less twitchy. 

* **Move Support Binaries out of Root Folder**  
Support binaries are now moved out of the root folder into a `BinSupport` sub folder to avoid ending up on the User's path and causing naming conflicts. Only applications that should be visible on the user path now are: `MarkdownMonster`, `mm` and `mmcli`.

* **Make Settings HelpText Selectable**  
You can now select the help text associated with a configuration setting in the Settings window. This allows picking up URLs and other fixed values more easily. (#817)

* **Dev: Add Debug Editor and Preview Template Paths**  
Added configurable Editor and Preview Template paths that are configurable and allow pointing the template folders to the original development folder, rather than the deployed applications' folders. This allows making changes to the Html/Web templates without having to recompile code. Settings are `System.DebugEditorHtmlTemplatesPath` and `System.DebugPreviewHtmlTemplatesPath` and they default to `.\Editor` and `.\PreviewThemes` which are fixed up at runtime.

* **Fix: Remove WebViewPreviewer Addin from 1.x Installs**  
Added logic to remove the WebViewPreviewer Addin from v1 which throws an error. If found this addin is now explicitly removed at startup since the code has moved inline.

* **Fix: PDF Generation Errors**
Fix issue where repeated output to PDF would report an error for PDF generation even when the PDF was generated.

* **Fix: PDF Code Snippet Background**  
Fix issue where the PDF output for code snippets was not properly applying the background color. Works in HTML but not for the PDF generator. Added custom print style sheet overrides for `pre > code` style explicitly to match highlightjs color theme.

* **Fix: Folder Browser Click and DoubleClick Behavior**  
Fix issues where clicking would not allow keyboard navigation after click, folder opening wasn't opening folders on first click, and preview operations could hang.


### 1.28.4

<small>July 2nd, 2021</small>

* **Fix addin loading for new Addin Repository Urls**  
Due to the upgrade to v2 all the Addin repository URLs have been broken for v1. This update fixes these URLs and can now again load v1 versions. Note for all older versions addins will no longer load from the addin manager as all addins have been updated for v2.


### 1.28 
<small>June 8th, 2021</small>


* **Create Link from Document Outline Anchor**  
You can now create a link in selected text from a header link in the document outline. A new context item creates a markdown link from the current text selection with the header ID for the link navigation.

* **Hierarchical Configuration Settings for Project, Marker Files**  
You can now override global configuration settings via JSON file settings in Markdown Monster Project Files (in the `Configuration` node), or in the `.markdownmonster` marker file. In both cases you can use JSON to override default configuration settings like font-size, editor and preview themes, formatting, line numbers etc.

* **Add Default Search Engine Configuration Option**  
For Web lookups you can now select a Search Engine (DuckDuckGo, Google, Bing) for opening the browser on a search page. Set via the new `WebBrowserSearchEngine` configuration setting in settings.

* **Set Table Type when using Edit Table**  
When editing Markdown or HTML tables, the table type is now properly set when the table editor is opened. Previously the default Pipe Table was used.

* **Updates to the Table Editor**  
Fix some navigation issues. Update editing field height to provide more consistent display of new fields when they are injected. Smaller font size - previously the font-size was larger than the default template.

* **Fix: Open From Url GitHub Repo Fixups for `Main`**  
When extrapolating repository URLs MM now checks for `main` in addition to `master` branches for default documents and for repo URL fixups.

* **Fix: Table Editor auto sizing for Table Cell Editing**  
Table cells now auto-grow in height as you are editing them when adding linefeeds or overflowing at the end of the line.

* **Fix: Table Editor Crash**  
Fix Table Editor crash when reformatting mismatched table column counts. If a table had fewer columns for a row it would crash in some situations. Missing columns are now auto-created as empty columns.

* **Fix: Drag and Drop Selection in the Folder Browser**  
Fix issue where selecting an item would not always drag the correct item (due to invalid tree item selection). Items are now explicitly selected before dragging.

* **Fix: Search Panel Result Selection Behavior**  
Search panel result clicks now open search results in preview-only mode, only if the tab is not already open. Double click now opens the document as non-preview document. Fixes issue where a search result in an existing window might close an already open window.

### 1.27
<small>April 30th, 2021</small>

* **[Rewritten Table Editor](https://markdownmonster.west-wind.com/docs/_53a0pfz0t.htm)**  
Completely revamped the Markdown Table Editor to better support larger tables and quicker editing support. Editing now uses the current theme in the editor, and there's an optional previewer which also uses the current Preview Theme. There's new support for sorting and alignment of columns, as well as improved output and parsing support, plus much more.

* **[Search Web and Search Web and Link on Editor Context Selection Menu](https://markdownmonster.west-wind.com/docs/_4xs10gaui.htm#embed-web-links)**  
New option to allow searching for content on the Web by opening the browser from the selected text and another option that performs a search and displays a list of matches with URLs on a sub menu that can be auto-linked to the selected text.

* **[Web Search and Search Web Links on the URL Dialog](https://markdownmonster.west-wind.com/docs/_4xs10gaui.htm#embed-web-links)**  
The same two search options from above are also available in the `ctrl-k` URL Link dialog as links below the text input. Clicking the links searches the Web with the display link. For the Browser search any URLs on the clipboard automatically replace the URL text if it's empty. For the inline search, a list selection fills the field.

* **Search Weblog Folder**  
New Menu option on the Weblog folder that lets you search the WebLog folder for posts using the built-in [Find in Files Search](https://markdownmonster.west-wind.com/docs/_5y715t8co.htm#find-in-files) functionality.

* **Preview Sync Improvements**  
Refactored some of the logistics in Preview Sync which should improve responsiveness of preview refreshes. There should now be fewer odd instances where preview is not refreshing automatically. Also updated  `Left-ctrl` which forces an immediate refresh, spellcheck and stats update.  

* **Drag and Drop Files into Editor as Links**  
When you drag and drop a document file (Markdown, html, pdf, zip) from Explorer or the File Browser into the editor, the file is now linked rather than 'opened'. The link is created as `file.ext` with a document relative path. 

* **[Document Outline Line Selection and Navigation](https://markdownmonster.west-wind.com/docs/_55o1bd4n1.htm)**  
Document Outline Navigation now moves the cursor position to the selected line in addition to scrolling to the appropriate Viewport position. When navigating by keyboard, ENTER and SPACE selects, and TAB moves the focus into the editor.

* **Add Folder Opening to Recent File List**  
There are now small folder icons next to files in the Recent Files dialog to allow opening of the associated folder in the Folder Browser to facilitate quicker access to files.

* **Markup for Empty Selections puts Cursor into Selections**   
When using shortcuts for Markdown markup like `ctrl-b` or `ctrl-i` for empty selections, MM now moves the cursor into the generated empty Markup. So `Ctrl-b` generates `**~**` where `~` denotes the cursor position (`~` not generated).

* **Improved Large Document Support**  
Added improvements to make MM work better with very large documents, by reducing preview refresh overhead, dynamically expanding the refresh timeout and tweaking the update process. Also - Using the built-in Chromium addin as the previewer now refreshes off the UI thread so that refreshes no longer freeze the editor while updating the preview for large documents.

* **Add mmCli Path Expansions for Environment Vars and ~ Home Path**  
Fix `mmcli.exe` to respect current folder and relative files for input and output files as well as expand Environment Variables and `~` for the Home Directory folder.

* **Add Editor Option for No AutoCompletions**  
You can now optionally disable all editor completions via a new `NoAutoComplete` Editor configuration option. This option disables all key expansions like quote and bracket completions, list bullet expansion etc. for a raw editor experience.

* **Fix: Browser Executable using Default Browser**  
Fix *View in External Browser* when the default browser executable is left blank - defaults to the system browser but executes using command line to allow for URLs with `#hash` extensions.

* **Accessibility Updates**  
Some adjustments to the accessibility features in the file browser and search features.

* **Fix Cut Behavior from Context Menu**  
Fix broken Context Menu Cut behavior which was deleting the text but not putting it on the clipboard. 

* **Fix: Preview To Editor Sync in IE Mode**  
Fix issue where preview to editor sync mode jumps the cursor to the top of the editor when typing.

* **Fix: Open Folder Browser when no Document Active**  
Fix issue where the various folder browser menu options weren't enabled when no document was active. Also fixed hotkeys.

* **Fix: PreviewWebRootPath in `.mdproj` Files not respected**  
* Fix issue where the `PreviewWebRootPath` value in the `.mdproj` files wasn't respected in some situations. The file is now checked on every render operation so changes in the `.mdproj` are immediately reflected.

* **Fix: Multi-Selection Issues in Folder Browser**  
Fixed several issues with inconsistent behavior with multi-selected files in the Folder browser. Reduced selection jitter and better handle accidental starting drag and drop operations.

* **Fix: Chromium Initial Preview Refresh Issue**  
Fix issue where the Chromium Previewer would occasionally not display content when first loading Markdown Monster or when switching from IE view to Chromium Preview. Caused by async load of the Preview browser, we now explicitly check for completion and if not ready wait for the browser to be ready to preview.

### 1.26
<small>February 4, 2020</small>

* **Chromium Previewer Browser Addin**  
Added a built-in addin that can toggle between the native IE based preview browser and a new WebView2 based Edge Chromium  Preview browser. This addin provides better compatibility with common browsers and allows support for some related technologies like Mermaid Charts to render natively.

* **Folder Browser Find Files Search Box**  
Changed the Find Files Search Box to be always visible in the Folder browser above the browser instead of an explicit dropdown panel. This search finds and filters by file name in the tree and shows a tree based match filter. The search box sits above the directory tree is now always visible and accessible via Ctrl-F from within the browser. You can optionally specify to search in sub folders.

* **Update Find in Files to Incremental Search**  
Change the Find in Files sidebar to use live searching instead of using an explicit Search button. Better handle results display and navigation in the result view.

* **Updated Find in Files Operation** 
Find in Files searches content inside of files to find matching content. The result displays a straight list with match counts for the files. Selected files are opened in the editor with the search term selected in the Find box (and Replace box if you specify Replace text).

* **Update Open Document Change Detection**  
Updated logic to handle change detection on open documents. When documents are open and unchanged, the document is immediately updated with changes from disk. If the open document has changes and the underlying document changes, nothing happens until you save. A new dialog allows you to choose between your version, their version or to run the configure Git Diff tool to compare versions and merge changes.

* **Add PDF Page Sizes to Save To PDF**  
Added all additional supported PDF print formats to the paper type dropdown on the PDF Export dialog. Adds all Ax and Bx types as well as various named types.

* **Favorites Click Behavior Update**  
Favorite clicks now open documents initially in preview mode until you type into the editor. Preview mode documents close as soon as another tab is opened or accessed. This behavior is now the same as the main folder browser. Double clicking forces the opened document to be a permanently open document. Unlike the folder browser, a single click forces the cursor into the Favorite document selected.

* **[Markdown Monster Web Server Enhancements](https://markdownmonster.west-wind.com/docs/_5s1009yx1.htm)**  
Markdown Monster includes a local Web server that can now be used to open new or existing documents and retrieve document content from the active document. Added support for retrieving the active document's content. Added Web page examples that interact with Markdown Monster. There are also new `-startwebserver` and `-stopwebserver` flags to start and stop the Web server to ensure that the local server is running. Added Web Browser HTML samples in  `SampleDocuments\BrowserIntegration` that demonstrate how to interact with MM from a Web page. 

* **Update Mermaid Rendering in the Preview**  
Mermaid support in MM has always been minimal since it uses the Internet Explorer engine for the preview pane. Mermaid recently removed their already terrible support for IE completely, so MM now renders a placeholder rather than the Mermaid chart in the default (IE based) previewer. The placeholder includes a clickable link that opens your default browser and displays the document containing the diagram and navigates to the Id of the mermaid diagram. Note in the Chromium addin previewer, Mermaid charts are properly rendered inline.


* **Fix: Preview Refresh for Ctrl-key operations**  
Fix issue where some common ctrl-key operations (ctrl-z, ctrl-x etc.) would not immediately update the preview until manual key entry into the editor is performed. Changed operation that the `ctrl` key now triggers a preview refresh for all ctrl-key operations. This also means that the `ctrl` key becomes the effective 'immediate refresh' key that you can use to force a preview refresh even when no preview sync is in use.

* **Fix: Weblog YAML Parsing for customFields**  
Fix bug where an empty `customFields` value would cause the Weblog Entry to not pre-load values back into the Weblog Publish dialog for repeated publishing. Fixed issue and changed defaults to not render empty field in the first place.


* **Fix: Links in Headers for Document Outline**  
Fix bug where links in headers where showing incorrectly in the Document viewer. Fix parses links and retrieves the text properly for display in the Document Outline. Also fixed in the TOC embedding logic.

* **Fix: Blog Post MetaData**   
Fixed a regression in posting to a blog where server generated values on new posts - the PermaLink and FeaturedImageUrl - were not updated in the meta data. These values are now updated and written back into the FrontMatter meta data again. Fix bug where PostId was not updating in captured meta data after posting.

* **Fix: Split View Editor Styling**  
Fix bug where split view would not open with the same styling as the main view if the theme was not the default theme.

* **Fix: Theme Switching Issues**  
Fixed bug that would crash MM when switching themes in MM Multi-Window mode. Also fixed timeout delay for forcing a restart after theme switching which previously would launch the updated instance too quickly and so fail to load in Single Use mode.

* **Fix: Various Open In Explorer Operations**  
Fixed various **Open In Explorer** operations where folders would not open properly in Explorer when the path contained inconsistent path delimiters. This broken in the Git Explorer as well as manually entered mixed paths.

* **Fix: Preview to Editor Sync**  
Preview to Editor sync was not working correctly due to an omission check.

* **Fix: Chromium Previewer Addin ScrollSync**  
Fixed scroll issue in the WebView2 control interop that would cause scroll failures when scrolling the preview and trying to sync the editor. Fixed with non-cached interop object instances to avoid potential operational overlap (WebView2 bug).

* **Fix: mmCli Html Package Exports**  
Fix issue where HTML self-contained Package exports were failing due to an assembly binding error. Added `.config` file to ensure correct bindings are used.

* **Fix: mmCli Relative File Paths**  
Fix file path translation for relative paths.

* **Fix: Jekyll Publish Flag**  
When publishing to a Jekyll flag, fix the publish flag to correctly set the publish status as published or hidden.

### 1.25
<small>November 12, 2020</small>

* **Multi-File Selection in Folder Browser**  
You can now select multiple files in the folder browser and perform many of the common operations on multiple files. You can open multiple files, copy and paste and drag and drop multiple files among folders or to Explorer, delete multiple files and so on. Also updated FolderBrowser API for addins to allow `GetSelectedItem()` and `GetSelectedItems()`. Multi-select also works with keyboard using `Ctrl-arrow` or `Shift-Arrow` for multi-select and range selects respectively.

* **Updates to Folder Browser Operations**  
Cleaned up folder browser file management tasks: New file now focuses the editor with the new empty document. Folder browser navigation now stays focused on the active selected item in more situations so you can perform another task like edit and then jump back to the Folder Browser (`alt-v-f`) and continue navigating the tree. Improved keyboard navigation functionality. `Ctrl-N` is now used as the default key in the Folder browser for new files. New files are created with a name editor in the folder browser and are then opened in the editor. This differs from `Ctrl-N`/**File -> New** in the editor which creates an `Untitled` document which prompts for filename only when saving.

* **File Stem Selection in Folder Browser**  
When selecting files for renaming in the folder browser, the filename without extension is now highlighted when first entering the name editor. Makes it quicker and more reliable to rename a file. Also fix file renaming message when edited filename is not changed.

* **Default Image Location for Untitled Doc Images**   
When saving images into a new document that has no filename, the default image save folder now defaults to the open folder browser location (instead of *Documents*). Subsequent saves for the same document remember the last image save location.
  
* **New command line option to open MM document at specific Line**  
You can now use the new `-line` command line option to open a document loaded from the command line at the specified line number.

* **FrontMatter in Blog Posts: Preserve Custom Properties**  
Added support for preserving top level properties in FrontMatter when Weblog Meta data is created. Previously the FrontMatter was serialized directly into the Weblog Meta structure and written back out using just that schema which lost custom props. They are now maintained.

* **Improve Jekyll Post MetaData Handling**  
Related to the FrontMatter improvements for blog posts, the meta data for Jekyll blog content has been updated to better support the category and tags lists.

* **Allow for `.markdownmonster` as Root Folder Indicator and External Configuration**  
Set up addin handlers that can find `.markdownmonster` file and use it for custom project level addin configuration. For example this JSON file can contain custom, project level configuration that can be used to stored for an addin. For example, a Deployment addin might hold server/auth configuration.

* **Add `pagebreak` Default Snippet to Snippet Manager**  
Added a `pagebreak` default snippet to the Snippet Manager Addin, so it's there by default when MM first creates the Snippet Manager defaults. This is optional and can be removed but is one useful use-case of using a snippet.



* **[Addins: Updated Markdown Monster Add-in Project Visual Studio Extension](https://markdownmonster.west-wind.com/docs/_4ne0s0qoi.htm)**  
The [Markdown Monster Addin Project Extension](https://marketplace.visualstudio.com/items?itemname=rickstrahl.markdownmonsteraddinproject) now creates much simpler, SDK style .NET projects. Projects now run and debug out of the box after running the New Project Template without additional manual configuration, as was required by the older version. It's also considerably easier now to configure for custom MM install locations using the raw XML Project file.

* **Addins: Add `ContextMenuOpening` Events to various Context Menu Renderers**  
Added static  `ContextMenuOpening` events to the various context menus that are dynamically generated such as the editor, tab, folder browser preview context menus. These events can be hooked and allow adding (or removing) of menu options at runtime, typically from Addin code. Handler is passed the ContextMenuWrapper class and the actual `ContextMenu` instance as Event parameters.

* **Fix: Icon Placement on multi-monitor Setups**  
Fix odd bug where the MM icon would not show on the correct screen in some multi-monitor scenarios. While at it also fixed the startup icon flash when loading MM onto a non-main screen.

* **Fix: Set Editor Position offset to be properly 1 based**  
The editor position now properly shows the Line and Row position in the status bar as 1 based. ie top of the document is `Ln 1, Col 1` rather than `Ln 0, Col 0`.


* **Fix: File Encoding bug in the Embed Url Dialog**  
Fixed issue where files with spaces in the filename would not URL encode correctly. New behavior doesn't encode but replaces spaces with `%20` in order to allow the Markdown Parser to properly parse Urls.


* **Fix: Window Outline showing on multiple Windows desktops**  
Provided a workaround for a problem whereby MM casts an 'outline frame' onto any other Windows desktops on which MM is not actually running. Fixed by removing the 'glow window' outline functionality and using a flat frame 1 pixel border instead.

* **Fix: Window Focus when externally activating**  
Fix issue where externally opened documents would not receive focus if MM was already running. Fixed so that focus now always goes into the editor when opening documents from Explorer or other shell executed applications.


### 1.24
<small>September  3rd, 2020</small> 

* **Add additional Code Fencing inline Syntax Colorings**   
Added additional inline syntax colorings for the following languages: `csharp`, `typescript`, `json`, `typescript`, `powershell`. You now get syntax colored text as you type or paste inside of triple backtick fenced code blocks.

* **Additional File Browser Icons and Editing Syntax Support**  
Added additional icons that can display in the Folder Browser including `Dart` and `Dockerfile` files. Both file types can now also be edited in MM. Also fix additional icons for various external document types.

* **Add Menu Shortcuts for Document File and Shell Operations** 
Added shortcuts to quickly navigate the Folder Browser to the active document's location, open the Terminal or Explorer on the Tools menu. Added shortcut mnemonics to make them easier to be  discoverable.

* **Better File Encoding Support**  
You can now set the file encoding for documents. Additional non UTF/Unicode encodings have been added. You can use **Load additional Encodings...** to load up all encodings available. Choosing an encoding will try to reload the document with the new encoding .

* **Improved Code Snippet Syntax for Html to Markdown Conversions**  
Worked with [ReverseMarkdown](https://github.com/mysticmind/reversemarkdown-net) to add better support for capturing syntax for many common services including GitHub, highlightJs, Atlassian and Confluence. For most snippets the syntax should now be applied to code-fenced blocks.

* **Refactor Preview Context Menu UI**  
Change the order of context menu items to show the most context sensitive items on top. Options like *Copy/Edit Image* and *Copy Id to Clipboard* now show on top of the menu if relevant.

* **Copy Image to Clipboard from Preview**  
There is now a context menu options to copy an image to the clipboard from the Preview Browser.

* **Updated Heading ID to Clipboard**  
You can now use the context menu in the previewer or the editor to copy the generated document html `id` attribute value to the clipboard. This makes it easier to paste relative links. As a reminder you can also get this Id from the Document Outline sidebar's context menu.

* **Open Image in Image Editor or in Image Link Form from Editor**  
You can now right click on an image link in the editor and use the option to open then image in your preferred image editor, or open the image in the link dialog (from which you can copy the image to the clipboard or resize the image).

* **Improved Application Title Bar Configuration Options**  
The title bar now has a new `TitlebarDisplayMode` configuration property that has options for displaying, just the filename, the full path, or the filename plus the parent path on the title bar. Tabs continue to display the filename by default and the filename plus parent path *if multiple files with the same name are open*. The new option to display filename plus parent path makes it easier to differentiate documents in the task bar.

* **Paste Improvements**  
Updated the editor paste behavior to use native editor paste behavior for text while deferring images and file paste operations to the Editor shell. This improves paste performance and reliability of text copy and paste operations.

* **Statusbar Text Tooltip**  
The status bar now also shows a multi-line tooltip for extra long messages that might overflow the status bar area. 

* **Switch to MahApps 2.1**  
Switched MM to use latest MahApps Metro UI framework. This provides a number of enhancements plus better stability and consistency for many UI operations.

* **Light Theme Enhancements**  
In light of the MahApps update the light theme has seen a number of updates for better consistency and color contrast in a few areas.

* **Fix: Preview Window Disappearing when editing non-Markdown Files**  
Fix bug that caused the active document syntax type to be turned to an invalid syntax when opening a non-Markdown document. Refactored `EditorSyntax` onto the document itself rather than on the Editor which would cause assignment issues.

* **Fix: SnagIt Screen Capture and File Saving**  
As of SnagIt 2020 the SnagIt Addin from TechSmith was broken due to a bug in the file saving mechanism. Modified the way file saving works by capturing to clipboard and saving the clipboard content. This works around the SnagIt bug and should hopefully future proof the SnagIt regression that keeps cropping up. As a bonus we now get better file location support using MM's document/project file location settings. 

* **Fix: Screen Capture Timer for Built-in Capture**  
Fix the screen capture timer used with with built-in capture when delaying captures.

* **Fix: Add hot key for Add-ins Menu on the Toolbar**  
Added a keyboard mnemonic to the **Tools -> Add-_ins** menu item so it becomes possible to navigate to the add-in list via keyboard. Some addins have been updated with keyboard shortcuts so for example the Azure Blob Addin is accessible via `alt-t-i-b`

* **Fix: Images from Clipboard not showing in Image Previews**  
Fixed issue with WPF clipboard that failed to retrieve images from the clipboard properly. Used alternative image retrieval. This fixes missing preview images in the the Paste Image and Azure Blob Storage Addin (update required to see the fix).

* **Fix Recent Documents Dropdrown Layout**  
Cleaned up the layout of recent menu lists on the Recent Files menu, and on the startup page.

* **Fix: File Encoding and Save Bug**  
Fixed issue where file saving under certain circumstances with non-UTF8 encodings would cause the file not save. Fixed by assigning default encoding and fixing up encoding lookup failures as well as adding additional logging around encoding for notification or save problems.

* **Fix Jekyll Image Publishing**  
Fix bug with images published to a Jekyll Blog. All but the last image were deleted by the post handler previously. Related: Also updated the Preview URL generator used to navigate to the generated URL which should work much better than before for the post title as well as the categories to match the Jekyll snake case conversions.

* **Fix: Light Theme Crashes**  
Fix several bugs related to light theme and missing resources. 


### 1.23 
*<small>June 9th</small>*

* **[Local Jekyll Weblog Publishing Support](https://markdownmonster.west-wind.com/docs/_5rv00rx4i.htm#setting-up-the-jekyll-publishing-configuration) (Preview)**  
Added support for 'publishing; blog posts to a local Jekyll installation. Works by letting you write your blog content as a MM Weblog post and publishing the content into the Jekyll `_posts` folder structure and creates images in the `_assets` folder by post name. Simplifies: Post creation, asset management, re-editing and re-publishing to other blog platforms, makes posts more portable.

* **[Support for Opening Empty/Untitled Documents with Preset Text](https://markdownmonster.west-wind.com/docs/_4x313dneu.htm#open-a-new-document-with-pre-filled-text)**  
You can now open a new untitled document with preset text by using a custom filename format on the command line. Use `mm untitled.base64,base64text`, `mm "untitled.text,This is a new document"`, `mm untitled.urlencoded,this+is+new` to open a document with the specified encoding format. Base64 is recommended due to the need to encode line breaks and extended characters but for simple string text and urlencoded can also work.

* **[New `mm -base64text` Command Line Option](https://markdownmonster.west-wind.com/docs/_5fp0xp68p.htm#base64text)**  
This is an alternate syntax for the `mm untitled.base64,base64Text` option, and provided mainly to provide a clear and obvious documentation point that might be easier to remember and look up. Allows opening a new document with preset text. If launching from the command line or using `CreateProcess` from another application this is the recommended approach for passing new document data to MM.

* **[Open Markdown Monster from a browser with `markdownmonster:` Application Protocol](https://markdownmonster.west-wind.com/docs/_5rj1cknrj.htm)**  
Markdown Monster now installs a `markdownmonster:` Application Protocol Handler which allows opening MM from a within a browser. . You can use `markdownmonster:untitled.text,New Document Text` as well as the other new options using the `mm untitled.` syntax mentioned above.

* **[Built-in local Web Server to allow Browsers Open Text Markdown Monster](https://markdownmonster.west-wind.com/docs/_5s1009yx1.htm)**  
Added WebSocket support to allow opening Markdown text in MM via a browser connection. Socket server listens to incoming document requests and if sent opens a specific document. This is similar to the `markdownmonster:untitled` functionality recently added, but unlike Application Protocols which are limited to 2046 bytes of data, this mechanism allows for large Markdown content to be opened in MM. The WebSocket Server  is disabled by default and can be auto-started whenever MM starts via the `WebSocket.AutoStart` configuration switch.

* **Document Syntax Improvements**  
The Document object now internally tracks the editor syntax associated with it. It is assigned based on the filename extension and mapped to editor associations - just as before. But the Syntax is now separately tracked from the doc type, so that you can change the syntax and affect editor and preview behavior. It's now possible to use the Preview with with `.txt` files for example, if the syntax is set to `markdown`.

* **Improve Configuration Backups to Folder**  
Updated folder backups to choose the Configuration folder `.\backups` sub-folder for folder backups. You can now pick a path and the backup is created as a subfolder **below** that folder in the format of `yyyy-MM-dd-Markdown-Monster-Backup`.

* **Text Only Linking (Ctrl-Shift-K) Improvements**  
When using the text only link shortcut Markdown Monster now automatically pastes and selects URLs from the clipboard. If there's a URL on the clipboard (any https link) it will be automatically injected.



* **Switch to embedded Debug Symbols**  
Debug information is now embedded in the Exe. Removes the original pdb file and reduces distribution footprint by a 1.8mb.

* **Fix: Several Table Parsing Issues**  
Fixed several recurring issues with invalid table imports from unbalanced or mis-formatted tables. Unbalanced tables (with rows that have more columns than headers) are now adding additional headers as needed to balance the table. Added a number of additional out of bounds checks when parsing incoming column data.

* **Fix: Jekyll Pathing issues**  
Fixed a path issue Jekyll publishing if path was entered with trailing slash.

* **Fix: Recursive Loading Issue with Shell Mapped Files**  
Fix issue where a shell mapped file would cause infinite load loops when opened from the shell or the command line. Fixed.

* **Fix: Link Dialog Spaces to %20**  
Automatically fix up any spaces in a typed in url to `%20`. We're not URL encoding the entire URL because more than likely a URL pasted into the textbox (or auto-injected) is already URL encoded so we don't want to end up double encoding, but spaces are one of the most common 'encoded' values that will break Markdown rendering of a URL.

* **Fix: Fonts in Preview Themes**  
We had recently switched to Emojii versions of common fonts as the primary fonts (like Segoi Emojii) but it turns out these fonts are inferior in quality to the regular fonts (like Segoe UI). This should bring font rendering back to smoother text in the preview and also for rendered HTML output in external browsers and exports.

### 1.22
*<small>April 22nd, 2020</small>* 

* **[New Markdown Monster CLI](https://markdownmonster.west-wind.com/docs/_5fp0xp68p.htm#cli-commands)**  
Added new `mmCLI.exe` executable that automates a number of Markdown tasks. You can convert Markdown to HTML in several ways, import HTML into Markdown (with some limitations), convert markdown to PDF as well as perform a number miscellaneous operations. This replaces some of the original Markdown Monster command line switches, but the old executable retains some of the original switches that pertain to administrative tasks like registration, launching etc.

* **[New MarkdownToHtml, MarkdownToPdf and HtmlToMarkdown Command Line Commands](https://markdownmonster.west-wind.com/docs/_5fp0xp68p.htm#cli-commands)**  
As part of the new separated command line tool the command line now supports converting documents between Markdown and HTML and PDF as well as converting documents from HTML to Markdown. Uses `mmcli.exe`.

* **[Additional Site Relative Root Path `/` Overrides](https://markdownmonster.west-wind.com/docs/_5fz0ozkln.htm)**  
Added additional site overrides for root `/` path resolution in the previewer. The new additions look up the folder hierarchy for a `.markdownmonster`, `_toc.json` or `docfx.json` file, or any `<yourProject>.mdproj` file. These overrides happen after the existing checks for YAML `previewWebRootPath` header, and the `PreviewWebRootPath` in an open project file.

* **Close Tabs To Right**  
Added option to the Tab Context and Window Menu to close tabs to the right of the currently active tab.

* **Folder Browser Drag and Drop Improvements**  
You can now drag and drop files from the folder browser into external applications using the standard Windows file dragging protocol. You can also drag open document tabs as files into other applications using the same mechanims. Files dragged from the folder browser into the editor surface either open the document, or embed an image as relative links or ask to save for external paths.

* **Remember PDF Export Settings**  
The PDF export window now remembers its settings so the next time the window is opened the existing settings are preserved.

* **Additional Paper Size Options for PDF Output**  
Added additional paper sizes for PDF output: Letter, Legal, A4, B3.

* **Remember common settings in Link Dialog**  
The link dialog now remembers the last folder used to select a file, for the 'Open in New Window' and 'Use Link References' and checkboxes. These values are stored in the configuration and saved across shutdowns.

* **Download and Embed Web Image Link as Local File**  
New context menu option for image links in the editor allows to convert a Web image URL into a local image by downloading and saving the file to the local disk and re-linking the new relative (if possible) path.

* **Text only Link and Image Embedding**  
Added additional hotkeys to add links (`ctrl-shift-k`) and images (`alt-shift-i`) using text only insertion. Select text and the link/image is wrapped around the text with the cursor inside of the link brackets (similar to the way Github does this).

* **Change h1..h6 Header Insertion Behavior**  
Header insertions for `h1`..`h6` now prefix the current string with the header prefix instead of just prefixing the current selection. It also strips off existing headers so you can change a header value to a new header type.

* **Don't allow usage of non-fixed Width Fonts**  
Changed behavior of Editor Font assignment so that only fixed-width fonts are allowed. The editor used in MM doesn't support propportional fonts, so a fixed-width font has to be used in order for the editor to track correctly. Also updated the description for the Options setting window.

* **Show Linefeed Mode in Statusbar**  
The statusbar now shows the active Linefeed mode. You can click on the mode and jump to setting the global setting to edit in the visual Settings Editor.

* **Statusbar re-arrangements**  
Move around some of the toolbar status items by grouping like items together and making common things a more visible. Also added additional tooltips to those items that didn't have them.

* **Fix up Copy to Clipboard with CR/LF**  
Fix up Ctrl-C copy behavior for text to force CR/LF to the clipboard  even if the editor is running LF only mode. This fixes issues for editors that don't support LF only and paste single lines of text.

* **Color Emoji Fonts in Preview Themes**  
Added specific emoji fonts for the preview themes so emojis now show in color instead of the default black and white.

* **Initial Support for RTL Text (experimental)**  
There is initial support for paragraph based RTL editing by setting the **Enable Right To Left** Editor Setting, and using `Alt-Shift-R` and `Alt-Shift-L` to toggle between RTL and LTR modes respectively. This is still rough and under consideration but if you want to play with this please check out [this issue on Github](https://github.com/RickStrahl/MarkdownMonster/issues/646).

* **Update Registration File Storage for better Shared Drive Operation**  
Modify storage location of `Registered.key` to be stored in the install folder if permissions allow with a backup in the common folder. Install folder storage gives each machine accessing a potentially shared configuration its own machine specific registration file which fixes an issue where shared configurations using DropBox, OneDrive etc. would override the machine specific registration files, resulting in installations as showing not registered.

* **[Improved DocFx Handling in Default Markdown Parser](https://markdownmonster.west-wind.com/docs/_5750qtgr2.htm)**  
Enhanced support for `[!include]` and `[!lang-javascript]` syntax to support the recently added PreviewWebRootPath sniffing, so paths to `/` and `~/` can be resolved. Also improved display of Info/Warning/Note etc.

* **Preview: Added dedicated DocFx Markdown Parser**  
Added the official DocFx parser as a markdown parser you can use to render documents. You can now pick that parser (which also uses Markdig as MM) to render DocFx documents. Rendering features for DocFx features are still limited and there are also problems with this parser. Adding for preliminary experimentation with DocFx content. Feedback welcome.

* **Markdown Rendering Error Display**  
Markdown rendering errors will now display an error page, rather than displaying either a blank page or not clearing the previous page. The error page shows the active Markdown Parser and a detailed code trace for potential debugging.

* **Improve Windows Placement on Application Startup**  
MM now will check if MM is rendering off screen when starting up. It's possible to get MM to start in 'negative' space if you size down from a large 4k display to a 1080p display for example, and MM will move the window into the viewable ViewPort area if it's hidden or even partially offscreen. 

* **Snippets Addin Window Placement**  
The Snippets addin now by default remembers its last window position and ensures that - like the main form - it's visible on the desktop. Initial startup will launch centered in the main app window.

* **Addins: Support for Colors in the MM Console**  
The new Markdown Monster Console that was recently added for addin developers, now implements coloring of console output. The parameters were there previously but didn't do anything.

* **Fix: Save Dialog on Shutdown on wrong Screen**  
Fix issue where the Save dialog with changed content will pop up on the wrong monitor during shutdown by forcing the owner before the main window gets released.

* **Fix: Open from URL**  
Fixed timing issue with Open From URL that caused open operation to not show a document. Fixed with new `EditorDocument.TabLoadingCompleted` event also available to addins to manipulate the document after startup.

* **Fix: UseMathematics and AllowMarkdownScriptTags**  
Add additional notes to the Configuration for `UseMathematics` and `MermaidDiagrams`  that point out that script execution has to be enabled in order to work.

* **Fix: Empty Context Menu on Various Window Controls**  
Fixed bug related to an empty context menu popping up on right clicking in various areas of the main form.


### 1.21
*<small>January 27th, 2020</small>* 

* **Major Overhaul of Editor/Preview Sync in Two-Way Sync Mode**  
Remove a number of issues that caused editor jankiness due to recursive editor and preview syncing. The preview is now more conservative in scrolling the editor so that any two-way recursion issues have been minimized. This fixes jumpiness at the top and bottom of the document (especially in code snippets) as well as unexpected cursor movements during keyboard scrolling. Made a few additional tweaks to the document syncing and scroll functionality which improves editor performance for plain editing and provides more reliable preview sync updates for code blocks and other large block objects in the markdown text.

* **Scroll, Click and Keyboard Navigation Performance Improvements**  
All navigation operations no longer update the preview but only scroll the preview and highlight the relevant new location in the preview which improves navigation performance especially in very large documents. It's now to edit multi-megabyte documents with the preview enabled (although the actual refreshes will still be slow).

* **Large Document Editing Performance Improvements**  
Large documents (2500 lines or more) now throttle the amount of preview refreshes that occur since that can significantly affect the editor performance blocking the editor while the preview refreshes. Timeout is automatically bumped so you can continue to edit at full speed, until stopping for several seconds (instead of the 120ms default timeout on 'normal' sized documents).

* **[Navigation Only Preview](https://markdownmonster.west-wind.com/docs/_5ch1bv9en.htm)**  
Added a new preview **NavigationOnly** preview sync mode, which does not implicitly update the preview on changes, but still allows navigation of the preview as you move through the editor. In this mode, Refresh operations are explict using a new explicit **Refresh Preview (Ctrl-Shift-R)** option on the **Edit** menu. This allows you to edit your very large documents without preview refreshes slowing down editing, and only explicitly refreshing the document to see your changes, all while still being able to navigate the document and scroll the preview.

* **New Console Output Window for Addins to display Output**   
For addin developers there's now a new `Window.ConsolePanel` that is accessible through the Addin's `Model.Console` property. You can `WriteLine()` and `Write()` to the panel, and use `Clear()`, `Hide()` or `Show()` to display status messages from processing. Writing to the Console makes it visible. This can be useful for addins that want to do things like provide progress info or for provide messages for linting etc. 

* **Add *Open Document in new Tab* to Context Menu for Relative Markdown File Links**  
There's a new context menu option that lets you navigate relative Markdown file links in the editor by opening them in a new (or existing) editor tab. Supported file types are opened in an editor tab, everything else is opened the Windows default viewer. HTTP links are opened in the browser.

* **Clickable Links in Editor**  
Links are now clickable in the text editor. Links are underlined and are control click-able,  which displays the link in the appropriate editor. Hyperlinks are opened in the browser, supported documents are opened in the editor and any others are opened in the appropriate Windows associated shell editors.

* **[PreviewWebRootPath in Project](http://markdownmonster.west-wind.com/docs/_5fz0ozkln.htm)**  
Added a new project property which provides a WebRoot Path for translating site relative URLs that start with `/` when the preview HTML is rendered. This allows finding related resources from some site generators or simply when working on deeply nested projects where the rootpath may be buried many levels below the current document. This change is in addition to the `previewWebRootPath` YAML header that already existed, and now is complimented by a `PreviewWebRootPath` project setting that applies to any file rendered while a project is open.

* **Switch to 64-bit version of wkhtmltopdf**  
Switched our PDF generation helper to use the 64 bit version of wkhtmltopdf in order to support conversion of larger documents. Previously PDF conversions of very large documents would fail due to out of memory errors - this update should help with that.

* **[Updated Editor Key Binding Configuration](http://markdownmonster.west-wind.com/docs/_59l0izpoe.htm#editor-commands)**  
Refactored the command binding logic to make it easier to create custom bindings to currently unmapped editor operations. Also allow for key mappings to custom created template expansions through simple key mappings. (note: this may break some existing key bindings. To reset: delete `MarkdownMonster-KeyBindings.json` in config folder)

* **Add KeyBindings Button to Configuration Form**  
Added a button that opens the `MarkdownMonster-KeyBindings.json` file in the editor for editing. Note: Changes to this file require a restart in order to be applied.


* **Add Toolbar DropDown for Additional Editor Operations**  
The main toolbar now has a new dropdown at the end of the editor operations, that provide additional editor insertion operations that are less common but were not discoverable before. Added operations: `<small>`, `<mark>` and `<u>` (underscore) as well as inserting a Page Break (for PDF generation or printing).

* **Addins: Added `Westwind.Scripting` Component to the main Markdown Monster Project**   
The scripting library used in the Snippets and Commander addins has been moved into the main Markdown Monster property, which now makes it available to the main project and all addin projects. This was done to consolidate the 'dynamic scripting' code used in both **Snippets** and **Commander** Addins, which now use the same shared scripting library for dynamic code execution using the same exact Roslyn C# compiler and runtimes.

* **Fix: HTML Rendering and Preview Sync**  
Fix preview HTML editor wonkiness (#609). Refactor HTML document sync separately from the Markdown document sync for greatly improved HTML preview sync to the editor position when editing or scrolling HTML content.


* **Fix: Two-way Code Editor Preview Sync Jumpiness**  
Resolved issue in two-way sync preview mode that was causing the editor to jump when editing or pasting into large blocks of text or code at the top or bottom of the editor. Finally found a solution to separating actual scroll events from explicitly navigated scroll events and refresh operations.

* **Fix: Ctrl-+ Zooming Size Issues**  
Fixed issue where Ctrl-+ zooming would use native browser zooming while Ctrl+- would use the application zooming resulting in missized zoom control and huge browser controls on repeated zooming. Fixed.

* **Fix: Document Outline not closing when closing last document**  
Fix Document Outline issue when closing the last document where the Outline stayed active after the document was closed.

* **Fix: Code Badge Copy Code Linefeeds in Previewer**  
Previously the Code Badge copying would not properly handle line feeds in code snippets. It worked fine for external preview, but for the IE preview the line breaks were lost. Also remove code badges in Print CSS display mode so when printing to PDF the badges don't render. Removed for PDF and Print output.

* **Fix: Code Badge Horizontal Scolling**  
Fix issue with the code badge positioning when the code block is scrolled. Previously the code badge failed to stay pinned to the right in the scrolled content. This fix keeps it always pinned to the right of the code block.

* **Fix: Remove Depedendent ShimGen Exes from Chocolatey Distribution**   
Removed extra EXE files from the distribution for the Roslyn compiler and set up Chocolatey to not generate ShimGen files for the remaining non-MM exe files (pingo, wkhtmltopdf, vbcscompiler).

* **Fix: Edit->Allow Script Tags in Markdown Preview Updating**  
Fix behavior of the `Editor.MarkdownOptions.AllowScriptTags` flag when switched to immediately turn off script rendering and refresh the preview immediately. Use this flag if your preview is jittery due to rendering of script elements in your page (ie. Gists, Math expressions, Embbedded media scripts). These scripts can cause the preview to jump around alot as elements are dynamically inserted. By temporarily disabling script tags, the editor and preview are smooth while not rendering the executing the embedded script. You can now toggle with `Alt-E-T`

* **Fix: Don't render Math Script Expansion Math Expansion is turned off**  
Fixed issue where math code was still expanded even if `MarkdownOptions.UseMathematics` was still enabled.

* **Fix: Table Header Parsing**  
Fixed issue with table editing when selecting an existing table and importing into the table editor for re-editing or re-formatting. Fixed various edge case scenarios that previously crashed the importer.


### 1.20
*<small>November 8th, 2019</small>* 

* **Add Hotkeys to the Table Editor Context Menu**  
The table editor context menu now has shortcuts for all operations like Insert Row Above, Below and Insert Column left and right, as well as delete row and column. This makes the options hotkey enabled via `ContextMenu Key + B` for example for Add Row Below within a cell.

* **Format Table Editor Context Menu Option**  
In the Markdown editor you can now use the context menu over a Markdown or HTML table and re-format that table using the new **Format Table** context menu option.

* **Improved Preview Scrolling**  
We've tweaked the preview scroll behavior which should now result in better consistency when scrolling the editor as well as less latency between editor and preview in two-way sync mode. The overall change involves trying to keep the 'in-focus' content near the top for the synced editor or preview so it's easier to track relevant content in one consistent place. Click sync and cursor movement sync scrolls the current cursor position content near the top of the preview. Also fixed several issues that could on rare occasion 'bounce the editor' when the preview and editor refresh out of sync. Preview scroll should now be much more responsive for both editor->preview and preview->editor scrolling. 
* **Improved Spellcheck latency**  
Reduced latency in the spell checking algorithm by checking the document more frequently to avoid jarring highlight movement. Change marker update logic to remove old markers only after new ones have rendered which removes/reduces flicker.

* **Add Copy Code and Syntax Display to Generated HTML Code Snippets**     
Code snippets in the editor and exported to HTML (in the Preview or if exported) now show a transparent badge that allows copying the code to the clipboard with a simple button click. The badge also shows the syntax in use if any.

* **Add Open With to the Editor Context Menu**  
Add a new context menu option to **Open With...** that allows opening the current document in a different editor configured on the system.

* **Open Settings Folder in Configuration Window**  
The Configuration Settings window now has an additional button to quickly open the configuration folder where you find all related configuration files. Same as the Tools menu option.

* **Add Reset Button to the Settings Form**  
The Settings form now has an additional toolbar button to reset the Markdown Monster installation to installation defaults. Clicking the button backs up the configuration file and then resets all configuration settings to default, followed by a restart.

* **Update Application Theme Changing and Toggling**  
Fixed a few issues related to switching between light and dark themes. Application now properly restarts after switching or toggling themes. The application theme toggle now sits more noticeably on the top window bar to make it easier to find for new users.

* **Fix: Preview Sync Problems with Two-way Synching at bottom of Document**  
Fixed issue where in some cases the cursor would jump up from the bottom of the document when doing two-way preview syncing between the editor and the previewer.

* **Partial Fix: Display Bold and Italic in editor**  
Fix behavior of markdown text that uses both bold and italic in the editor: `***bold and italic***`. Text now correctly displays in editor as both text and italic. However, mixed mode like `_**bold and italic**_` still don't work in the editor. Note that all combinations do work for Markdown output generation.

* **Fix: Table Editor Insert New Row with Tab at End of List**  
Fixed tab behavior on the last column of the table: When pressing Tab on the last cell a new row is inserted and the cursor moved to the first column of the new row. This actually was supposed to work before and a new row was being inserted, but the UI wasn't properly refreshing. Fixed.

* **Fix: Table Editor Column Width Formatting when Embedding**  
Fixed regression that removed the column sizing logic that attempts to fix table widths to make the tables line up properly.

* **Fix: Alternate Single Quotes and Spellchecking of Apostrophied Words**  
Fixed issue where spell checking wasn't working correctly with 'special' single quotes (SmartyPants or imported from something like Word). Fixed by replacing special quotes with single quotes for handling apostrophied words.

* **Fix: Document Outline Refresh** 
The document outline refresh previously was to conservative in refreshing. Added logic to every editor preview refresh to check for outline updates. Tested with very large documents to ensure there's no major performance hit.

* **Fix: Multi-Binding KeyBoardBindings**  
Fixed issue where multiple keyboard bindings to the same command were not properly firing all the commands. Changed keybindings handler to use IDs as names with command names separate. Any duplicate `CommandName` entries, should use separate `Id` values.

* **Fix: Save Fails Silently**  
Fix bug where a failed Save Operation would fail to save files and not let you know that the save failed. Fixed - if file save fails there's now a status bar message and the Save As dialog pops up to provide a new filename or try again.

* **Fix: Document Outline Editor Navigation**  
Document outline navigation now locates the navigated editor at the top of the editor page. Previously it was closer to the middle and somewhat erratic. This is related to the previews point about more consistent scroll behavior that pushes the in focus content to the top of the preview or to the editor depending on which window you are scrolling.

* **Fix: MathJax and MathML Rendering**  
Fix bug that wouldn't properly auto-detect documents that contain math expressions. Fixed search logic and tweaked RenderExtension with some additional improvements.

* **Fix: Version Check Last Check Date**  
Fix version check shutdown logic to properly save the last check date.

* **Dev: Update to ACE Editor 1.4.6**  
Updated to the latest version of ACE Editor which fixes a few small bugs that have been plaguing the editor namely fenced HTML code block tag lock ups/slowdowns and end of document caret movement.


