1. install the `EditorConfig` package in Sublime/Atom
2. create `.editorconfig` at the project root:
```
# EditorConfig helps developers define and maintain consistent
# coding styles between different editors and IDEs
# editorconfig.org

root = true


[*]

# Change these settings to your own preference
indent_style = space
indent_size = 2

# We recommend you to keep these unchanged
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false

[package.json]
indent_style = space
indent_size = 2

[bower.json]
indent_style = space
indent_size = 2

```

3. install the `SassBeautify` package in Sublime/Atom
4. run `SassBeautify` from the command palette