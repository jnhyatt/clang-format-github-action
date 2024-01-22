# Clang Format Github Action

An action that check code format using `clang-format` tool. Suitable for project built on C, C++, C#, Objective-C.

[Clang: a C language family frontend for LLVM
](https://clang.llvm.org/)

## Feature:
- It automatic checks the source file's code format, and if there is any code format violation, it exits with a nonzero status.
- Suggest commands for fixing the formation violated file.

## Inputs

### `sources`
Sources to check by this action. It can be a single file, regex of a folder or multiple selectors separated by comma (`,`).

Default: `"**/*"`.  That means all files in this repository.

Example: If your repository contains many files other than C file, you can try with specific extension like:

`"src/*.h,src/*.c"`

or, for all nested folder

`"src/**/*.h,src/**/*.c"`

### `excludes`
Sources to exclude from this action. It can be a single file, regex of a folder or multiple selectors separated by comma (`,`).

Default: `""`.

### `style`
The style for `clang-format`. Possible value are: `LLVM, GNU, Google, Chromium, Microsoft, Mozilla, WebKit`. If your repository has a `.clang-format` file in the root directory then you can use `file` option here.

Default: `LLVM`

## Sample Workflow File
Create a file in `.github/workflows/` folder with:

```
name: Clang Format Checker
on: [push]
jobs:
  clang-format-checking:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: RafikFarhad/clang-format-github-action@v3
        with:
          sources: "src/**/*.h,src/**/*.c,test/**/*.c"
```

It will check for code formation violation on every `push` to GitHub.

## Version

This action uses `clang-format` version 12.

| Clang Version | Action |
|---------|---------------|
| 14 | RafikFarhad/clang-format-github-action@v3 |
| 12 | RafikFarhad/clang-format-github-action@v2.1.0 |
| 10 | RafikFarhad/clang-format-github-action@v1.0.1 |

Kudos to
- [@silkeh](github.com/silkeh) for his awesome [docker image](https://hub.docker.com/r/silkeh/clang).
- [@LinkTed](github.com/LinkTed)
- [@aadeg](github.com/aadeg)
- [y-guyon](https://github.com/y-guyon)

## Contribution

Feel free to submit PR and/or raise issue.

🌞 Thanks for using 🌞
