---
title: "Render a markdown table to docx with pandoc"
date: 2025-10-28T18:01:52-04:00
draft: false
---

Suppose you're like me, in the middle of editing a Word document, and you realize that you're fed up
with Word. So you tell it to a colleague, who happily tells you: use [pandoc](https://pandoc.org), it can render docx files!

So here you go, and you first try to convert this simple markdown:

```markdown
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu
fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
culpa qui officia deserunt mollit anim id est laborum.

| City           | Population | Immigrants (%) |
|:---------------|:-----------:|---------------:|
| Laval          | 440,000    | 31.5           |
| Gatineau       | 285,000    | 15.5           |
| Trois-Rivières | 140,000    | 4.5            |

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu
fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
culpa qui officia deserunt mollit anim id est laborum.
```

Then you run this command, with a lot of hope:

```shell
pandoc test.md -o test.docx
```

And.. lo and behold, it's ugly, because the table is not centered, among other things!

![](/images/ugly_word.png)

Are you surprised? So it turns out that you need a bit of extra work. First you need to create
a Word style reference file, like this:

```shell
pandoc --print-default-data-file=reference.docx > my-reference.docx
```

(`reference.docx` is an internal pandoc file, you don't have to worry about it.)

This file looks like this:

![](/images/pandoc_reference_file.png)

Now you need to edit the style of the table in the reference file, and here your adventure with Word's devastatingly horrible
UI begins:

![](/images/word_horrible_ui.png)

Then you need to go through these steps (set the table base style to your taste), and then click on "Table Properties":

![](/images/word_horrible_dialog1.png)

Which will bring you to this dialog where you can center your table:

![](/images/word_horrible_dialog2.png)

But at this point, your work is not done, because you have to go through the same steps, but this time apply your center formatting to the "Header row":

![](/images/word_horrible_dialog3.png)

For this last part, I have to give a huge thanks to OpenAI and their ChatGPT,
which was tremendously patient with me, because I could really not get it, for
the life of me! At this point, if everything is correct, your reference file should look like this:

![](/images/pandoc_reference_file_centered.png)

After saving the reference file, we are finally ready to use it with pandoc:

```shell
pandoc test.md --reference-doc=my-reference.docx -o test.docx
```

And of course it's perfect (I mean.. centered), and you are a little less dependent on Word than you were, maybe!

![](/images/nice_word.png)
