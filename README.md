# print-delombok

A simple GitHub Action to print delomboked source files.

This is intended to work in conjunction with [delombok-action](https://github.com/sleberknight/delombok-action).

Here is example usage inside a CodeQL workflow:

```yaml
- name: Run Delombok
  uses: sleberknight/delombok-action@<current-version>
        
- name: Print the Delomboked code
  uses: sleberknight/print-delombok@<current-version>
```

Each delomboked source file name is printed followed by its contents, including line numbers. The line numbers are critical since CodeQL uses the line numbers of the delomboked code, even though it shows you (i.e. in the GitHub UI) the code from the original source file, i.e. that contain Lombok annotations. For example, you might get a CodeQL warning on line 56 in `Utils.java`, which refers to line 56 in the _delomboked_ `Utils.java`. But in the GitHub CodeQL UI, the code shown is the _original `Utils.java` code containing Lombok annotations_. By using this action, you can easily pinpoint the line in the delomboked source code that CodeQL displays in its warnings. You will need to go into the workflow output to see this, but this is way better than nothing!

## Configuration Options

You can configure the `delombokSourcePath` option, which is the path where the delomboked source files exist, relative to the workspace directory. The default value is `src-delombok` which is also the default value used in [delombok-action](https://github.com/sleberknight/delombok-action).

Example:

```yaml
- name: Print the Delomboked code
  uses: sleberknight/print-delombok@<current-version>
  with:
    delombokSourcePath: delombok-sources
```
