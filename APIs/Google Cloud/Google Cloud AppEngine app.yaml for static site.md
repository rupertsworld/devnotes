# Google Cloud: AppEngine app.yaml for static site
Assuming all static files are in a folder called `www`.

```yaml

runtime: python27
api_version: 1
threadsafe: true

handlers:
- url: /
  static_files: www/index.html
  upload: www/index.html

- url: /(.*)
  static_files: www/\1
  upload: www/(.*)

```
