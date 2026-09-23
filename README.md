# IntelliJ Markdown CSS

Custom stylesheet for the Markdown preview in IntelliJ-based IDEs.

## Setup

IntelliJ loads a custom stylesheet only if the file lies inside the current project.
A path pointing to this repository from another project is rejected with an "Unsafe custom stylesheet" notification,
and the preview falls back to the default styles.
The setting is also per project, so repeat the steps below in every project.

1. Clone the repository:

   ```
   git clone https://github.com/mgryszko/intellij-markdown-css.git ~/p/intellij-markdown-css
   ```

2. Symlink the stylesheet into the project's `.idea` directory, which belongs to the project and is usually gitignored:

   ```
   ln -s ~/p/intellij-markdown-css/intellij-markdown.css <project>/.idea/markdown.css
   ```

3. Open Settings > Languages & Frameworks > Markdown, in the "Custom CSS" section check "Load from:"
   and enter the absolute path of the symlink, e.g. `/Users/me/projects/foo/.idea/markdown.css`.
   Use a plain path, not a `file://` URI.

4. Reopen the Markdown preview.

## Alternatives

- Copy the contents of `intellij-markdown.css` into the "CSS rules:" field in the "Custom CSS" section and check it.
  No project restriction applies, but later changes to this repository are not picked up.
- Add this repository as an extra content root of the project (Project Structure > Modules > Add Content Root)
  and point "Load from:" at the file directly.

## Notes

- The custom stylesheet replaces IntelliJ's default preview stylesheet instead of extending it.
  Elements not styled here fall back to plain browser defaults.
- "Load from:" accepts only a local file path. Remote URLs are not loaded.
