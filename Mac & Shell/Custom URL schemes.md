# Custom URL schemes

You can create applescripts that can accept their own URL schemes.

Originally found via [Zettelkasten.de](https://forum.zettelkasten.de/discussion/1041/archiving-external-sources#fn:1). With a [StackOverflow post](https://stackoverflow.com/questions/2418910/osx-defining-a-new-url-handler-that-points-straight-at-a-python-script/2499107#2499107) that elaborates on the specific technique.

> I implemented it as a simple AppleScript that I exported as a macOS application using the standard ScriptEditor that comes with macOS. The important part is that the exported app needs to know that it has an url-scheme, which can be set in its Info.plist file1. The AppleScript itself is very simple and just calls a python script zettelscheme.py that is embedded in the final application:

```
on open location this_URL
    set zettelscheme_script to (path to me)'s POSIX path & "Contents/Resources/Scripts/zettelscheme.py"
    do shell script "python " & zettelscheme_script & " " & "'" & this_URL & "'"
end open location
```

> This python script does a few things for me, but in its most basic form, it would simply open the zettel with the UID. It could look as follows:

```
import subprocess
import sys
import urlparse

if __name__ == '__main__':
    parsed = urlparse.urlparse(sys.argv[1])
    if parsed.scheme != 'zettel':
        raise(Exception('Invalid URL scheme ' + parsed.scheme))
        sys.exit(-1)

    zid = parsed.netloc
    subprocess.call(["open", 'thearchive://match/{}'.format(zid)])
```