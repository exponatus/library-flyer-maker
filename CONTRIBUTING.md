# Contributing to Library flyer maker

Thank you for helping! This tool is made for libraries, and the best ideas come from people who work in them. You don't need to be a programmer to contribute.

- [Report a problem](#report-a-problem)
- [Suggest an idea](#suggest-an-idea)
- [Translate the interface](#translate-the-interface)
- [Change the code](#change-the-code)

## Report a problem

Open an [issue](../../issues/new/choose) and choose **Something doesn't work**. Please tell us:

- what you did and what happened,
- your browser and operating system,
- a screenshot, if you can.

A project file (*Save and export → Save project*) helps a lot. Remove anything private before you attach it.

No GitHub account? Write to alexander.ananyev@tuebingen.mpg.de.

## Suggest an idea

Open an [issue](../../issues/new/choose) and choose **Idea or wish**. Describe what you want to do in your library, not only the button you imagine. Example flyers are very welcome.

## Translate the interface

The interface is available in English, German and Russian. Adding a language takes about an hour.

**The easy way:** open an issue with the **Translation** template, or write an e-mail. We'll send you the texts as a simple list and add your translation to the tool.

**The direct way:** open `library-flyer-maker.html` in a text editor (not a word processor) and scroll down to the last `<script>` block.

1. **Texts.** Find `const I18N = {`. Copy the whole `en: { … }` block, paste it after the last language, and change `en` to the code of your language (for example `fr`). Translate the texts inside the quotes.
   - Keep words in curly brackets, such as `{name}` or `{n}`, exactly as they are.
   - `quote` sets the quotation marks of your language, for example `"« {v} »"` for French.
   - Keep `appName` as "Library flyer maker".
2. **Example flyer.** Find `const EXAMPLES = {`. Copy the `en: { … }` block the same way and translate it. Use neutral example texts that every library will recognise as examples, and keep `example.org` in the links.
   Descriptions of resources should stay under 60 characters and names under 34.
3. **Placeholder check.** Find `const PLACEHOLDER_RE` and add the typical example phrases of your language (for example the library name and address placeholders), so the tool can remind people to replace them.
4. **Language menu.** Find `const UI_LANGS` and add a line, for example `{ code: "fr", name: "Français", flag: "fr" }`.
   Flags are drawn by the function `flagSVG`. Flags made of three stripes are easy to add there, following the German and Russian examples.
5. **Automatic choice.** In `function detectLang`, add your language so that the tool opens in it for people whose browser uses that language.
6. **Test.** Open the file in your browser, switch to your language, and go through every tab, the check list, *My flyers* and the templates. Long words can break the layout, so look at the buttons and tabs too.

Then open a pull request, or send us the file.

## Change the code

### Principles

- **One file.** The tool must keep working when someone double-clicks a single HTML file.
- **Offline and private.** No requests to other servers, no tracking, no web fonts from the internet.
- **For non-technical users.** Clear words, sensible defaults, helpful checks. Every action can be undone.
- **Accessible.** Everything works with the keyboard, has a visible focus and a label for screen readers.
- **Print first.** What you see in the preview is what gets printed.

### Where things are

The last `<script>` block contains the app, in this order: interface texts, example content, language list and flags, the text-layer font, then the app itself (state, validation, undo/redo, page rendering, checks, editor, events, storage, export). The three script blocks before it are bundled libraries; please don't edit them by hand.

### Before you open a pull request

Please test in at least Chrome and Firefox (and Safari if you can):

- [ ] The file opens by double-click, with no errors in the browser console.
- [ ] Editing texts, colors, layouts and templates updates the preview.
- [ ] Undo and redo work, also with the keyboard.
- [ ] Drag and drop of resources works, also into another section.
- [ ] *Download PDF*, *Download image* and *Print* each give exactly one A4 page that matches the preview.
- [ ] Links in the PDF can be clicked, and the text can be found with the search function.
- [ ] *Save project* and *Open project* work.
- [ ] *My flyers*: new, duplicate, open, delete and undo work; flyers are still there after reloading the page.
- [ ] All interface languages look right.
- [ ] A narrow window (phone size) is still usable.

Add a line to `CHANGELOG.md` under a new "Unreleased" heading.

### Updating a bundled library

Replace the whole content of the matching `<script>` block with the new minified file from the library's official release, update the version number in the comment at the top of the file and in `README.md`, and run the test list above.

## Be kind

Be friendly and patient, especially with people who are new to GitHub. Many contributors are librarians, not developers, and their knowledge is what makes this tool useful.

## License

By contributing, you agree that your contribution is licensed under the [GNU General Public License v3.0 or later](LICENSE), like the rest of the project.
