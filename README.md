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
