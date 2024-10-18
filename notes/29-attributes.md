# Git Attributes File

By default, Git treats every file like plain text, but did you know you can configure Git to give you more powerful features?

With a Git attributes file, you can help Git understand your files better, starting with customizing how Git identifies code blocks when showing diffs, also known as [hunk headers](https://git-scm.com/docs/gitattributes#_defining_a_custom_hunk_header).

Start by copying the following into your global attributes file `~/.config/git/attributes`. This setup provides language-specific hunk headings, perfect for coding projects:

```shell
*.py diff=python
*.pyi diff=python
*.sh diff=bash
*.rs diff=rust
*.md diff=markdown
```

> [!TIP]
>
> `git log -L` and `git blame -L` can also use this configuration to follow changes to a function 🤯.

## Having file specific diff filter

Ever had trouble with binary files? Git lets you define **text conversion filters** that make binary files readable by converting them into text summaries. This way, you can easily compare the differences between two versions of a binary file.

### Diffing Document Files with Pandoc

Many documents are stored as binary files, and by default, Git doesn't show you any useful details—just “Binary files … differ.” But you can use the **pandoc** tool to convert these documents into markdown, allowing Git to display text differences.

How to do this? :thinking:

- Install pandoc tool.

- copy the following content into your global git configuration `git config --global --edit`

  ```ini
  [diff "pandoc-to-markdown"]
      textconv = pandoc --to markdown
      cachetextconv = true
  ```

- Finally, map file types to this filter in your global attributes file `~/.config/git/attributes`:

  ```shell
  # Use pandoc for diffing document files.
  *.ipynb diff=pandoc-to-markdown
  *.odt diff=pandoc-to-markdown
  *.rtf diff=pandoc-to-markdown
  *.docx diff=pandoc-to-markdown
  ```

### Diffing Media Files with ExifTool

When working with media files, Git’s default behavior provides little to no detail. To solve this, we’ll use the popular **ExifTool** to extract useful metadata for comparison.

When a diff changes a binary file, Git’s default output doesn’t give you any information
on the change. This lack of information makes it hard to be confident about binary file changes. 

For this one, we're going to use the famous `exiftool`

How to do this? :thinking:

- install exiftool

- define the text conversion tool in you global git configraution

  ```ini
  [diff "exiftool"]
      textconv = exiftool --composite -x 'Exiftool:*' -x 'File:*' -g0
      cachetextconv = true
      xfuncname = "^-.*$"
  ```

- Finally, map the media file types in your attributes file:

  ```shell
  # Use ExifTool for diffing media files
  *.avif diff=exiftool
  *.bmp diff=exiftool
  *.gif diff=exiftool
  *.jpeg diff=exiftool
  *.jpg diff=exiftool
  *.png diff=exiftool
  *.webp diff=exiftool
  ```