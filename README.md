# SKCraft Launcher Bootstrap

## Mechanism

If the launcher does not appear to have been downloaded, the bootstrapper will download the latest launcher version, store it, and run it.

On next start up, the bootstrapper will start the existing downloaded version.

When you push an update, the launcher (not the bootstrapper) will download the new version, store it in the right place, and on next startup, the bootstrapper will start using this new version.

## Customizing

All the customization is done within the `src\main\resources\com\skcraft\launcher` folder.

* Replace `bootstrapper_icon.png` with your own program icon.
* Change `bootstrap.properties` with a text editor.
* Customize the language file in `lang`.

### User's Files

On Windows, the launcher will store its files within *My Documents*. On other operating systems, the launcher will store its files in the home directory.

The name of the folder can be customized in `bootstrap.properties` but the directory cannot.

### Update URL

The update URL should point to a file that looks like this:

```json
{
    "version": "4.2.2",
    "url": "http://example.com/launcher/versions/4.2.2.jar.pack"
}
```

This is the same file that the main launcher uses.

The URL within this file must point to the main launcher's jar file that has been compressed using the [pack200 tool](http://docs.oracle.com/javase/7/docs/technotes/tools/share/pack200.html) (that comes with the JDK).

## Compiling

1. The Java Development Kit (JDK) needs to be installed. This turns Java code into Java programs.
2. [Maven](https://maven.apache.org) needs to be installed as well. This program reads the "pom.xml" file and runs the JDK for you.

While in the same directory as this document, run the following in terminal or command prompt:

	mvn clean package

In the `target/` folder should be the resulting files.

## License

The launcher is licensed under the GNU General Public License, version 3.

Contributions by third parties must be dual licensed under the two licenses
described within LICENSE.txt (GNU General Public License, version 3, and the
3-clause BSD license).
