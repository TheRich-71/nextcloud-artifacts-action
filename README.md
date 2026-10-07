# Nextcloud Artifact Upload Action
This project was initially started by trympet and included recent additions by MrVauxs

It's purpose is to upload artifacts to Nextcloud and output a shareable URL.

### Example:
Simple example. Globbing is supported. 

```yaml
on:
  pull_request:
  push:
jobs:
  build-test:
    name: Build & Test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v7                               # checkout the repo

      - name: Nextcloud Artifact
        uses: TheRich-71/nextcloud-artifacts-action@v1
        with:
          name: 'my-artifact'                                   # Name of the artifact
          path: 'bin/**/*.exe'                                  # Globbing supported
          nextcloud-url: 'https://nextcloud.example.com'        # Nextcloud URL
          nextcloud-username: ${{ secrets.NEXTCLOUD_USERNAME }} # Username from repository secret
          nextcloud-password: ${{ secrets.NEXTCLOUD_PASSWORD }} # Password from repository secret
          no-zip: false                                         # Optional, set to true if you have one file only AND do not want a zip-file
          if-no-files-found: 'warn'                             # Optional, maybe warn error or ignore
```
