# Search and Replace

**This feature is a work in progress and updates your Strange Eons cards. Please backup your content before using this feature**

This feature allows a user to both search for and search/replace content in Strange Eons files.

## Usage

To open the feature r-click the Zoop menu on any file or folder and select `Search/replace`. The scope of subsequent searches is what you have selected here, either a single file or a folder and all descendants.

The search/replace dialog will then open. You can do multiple operations while this screen is open, you do not need to close/re-open each time.

There are three different modes

- Plain-text - Regular searching for and replacing with text
- Regular expression - Searches using a user-provied regular expression and can replace content using regular expression group references or a literal string
- Image paths - Specifically searches for image paths for example in encounter set and collection settings of cards and embedded `<image>` tags

Each mode has specific search options relevant to that mode. Typically there will be a control to enter search text and and one for replace text.

### Plain-text

Simple mode to allow searching for text.

**Search options**

- Case-sensitive - If unchecked all searches are case-insensitive (the default). If checked all searches are case-sensitive

### Regular expression

If you're familiar with regular expressions most standard constructs are supported. The full details can be found [in the JavaDocs](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html)

**Search options**

- Case-sensitive - If unchecked all searches are case-insensitive (the default). If checked all searches are case-sensitive

**Replace options**

- Replace mode - `Literal` is the default and easiest to use as it simply replaces the matched text with the provided string. `Regular expression` mode allows use of group references (e.g. $1) to the regular expression provided in the search options

### Image paths

Unlike other options if no search text is provided it will search all possible areas for image paths.

**Search options**

- Search within - Limit where to look for image paths
- Case-sensitive - If unchecked all searches are case-insensitive (the default). If checked all searches are case-sensitive

**Replace options**

- Replace action - `Search/replace path` is like a regular search/replace that will update the path strings as specified. `Change path separators` is for specifically updating path separators on paths while leaving the other path content untouched
- Change separator - Only available when `Change path separators` action is being used. The options are self-explanatory


After you have enter the options you can hit the `Search` button to do a search of matching content or a `Replace` to do a search/replace. Typically you will need to do a search first to identify and select the content to be replaced.

For a search the results will be shown in the results table at the bottom of the dialog. Each row represents one location in a card. If multiple locations (e.g. fields such as game text and keywords) on a single card matched you will see multiple entries per card.

To do a replace enter the appropriate replacement text (empty strings are allowed), select the rows in the table to perform the replace on and hit the `Replace` button. You will see a results preview where each change is highlighted (red strikeout for removals, green for additions). You can then hit `Replace` to confirm the replace operation or `Cancel` to abort. Regardless you will see the Zoop progress dialog logging the activity which you can review if you wish and then hit `Close`.
