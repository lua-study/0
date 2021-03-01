Solarized Colorscheme for IntelliJ IDEA
=======================================

Original Solarized color scheme developed by Ethan Schoonover    

Adapted for IntelliJ IDEA by:  
Adam Vandenberg    
Johan Kaving  

Visit the [Solarized homepage]
------------------------------

See the [Solarized homepage] for screenshots,
details and color scheme versions for Vim, Mutt, popular terminal emulators and
other applications. These versions can also be found in the main [Solarized repository]
on GitHub.

Unfortunately the IntelliJ subtree in the main repository has not been updated and is out-of-sync with this
repository.

For IntelliJ this [IntelliJ-only repository] is therefore recommended over the main repository.

[Solarized homepage]:   http://ethanschoonover.com/solarized
[Solarized repository]: https://github.com/altercation/solarized
[IntelliJ-only repository]:  https://github.com/jkaving/intellij-colors-solarized

Status
------------

These color scheme files are primarily tested with the latest version of IntelliJ IDEA Community Edition.
They might work with other versions of IntelliJ IDEA as well as other JetBrains tools
(e.g. PhpStorm and PyCharm).

This table lists the languages (and other sections under `Preferences | Editor | Colors & Fonts`)
for which the syntax highlighting has been adapted to the Solarized color scheme:

 
	 
		 Language/Section 
		 Supported 
		 Note 
	 
	 
		 ActionScript 
		  Yes  
		  
	 
	 
		  Android Logcat  
		  Yes  
		  
	 
	 
		  Apache Config  
		  Yes  
		  
	 
	 
		  BEMHTML  
		  Yes  
		  
	 
	 
		 Bash 
		  Yes  
		 ( BashSupport  1.1beta14 or later) 
	 
	 
		  Buildout config  
		  Yes  
		  
	 
	 
		 C 
		  No  
		  
	 
	 
		 C++ 
		  No  
		  
	 
	 
		 CMD 
		  Yes  
		  
	 
	 
		 CSS 
		  Yes  
		  
	 
	 
		 Clojure Templates 
		  Yes  
		  
	 
	 
		  CoffeeScript  
		  Yes  
		  
	 
	 
		 Custom Templates 
		  Yes  
		  
	 
	 
		  Dart  
		  Yes  
		  
	 
	 
		 Debugger 
		  Yes  
		  
	 
	 
		 Diff 
		  Yes  
		  
	 
	 
		  Django / Jinja2 Template  
		  Yes  
		  
	 
	 
		 ERB 
		  Yes  
		  
	  
	 
		  Erlang  
		  Yes  
		  
	  
	  
		 File Status 
		  Yes  
		  
	 
	 
		 General 
		  Yes  
		  
	 
		 
		  Gherkin (Cucumber)  
		  Yes  
		  
		 
	 
		  Google Go  
		  Yes  
		  
	 
	 
		 GQL 
		  Yes  
		  
	 
	 
		  Groovy  
		  Yes  
		  
	 
	 
		  HAML  
		  Yes  
		  
	 
	 
		 HTML 
		  Yes  
		  
	 
	 
		  Haskell  
		  Yes  
		  
	 
	 
		  JFlex  
		  Yes  
		  
	 
	 
		 Jade 
		  Yes  
		  
	 
	 
		 Java 
		  Yes  
		  
	 
	 
		 JavaScript 
		  Yes  
		  
	 
	 
		 JSP 
		  Yes  
		  
	 
	 
		  Jodd props file  
		  Yes  
		  
	 
	 
		  Kotlin  
		  Yes  
		  
	 
	 
		  LESS  
		  Yes  
		  
	 
	 
		 Localization file 
		  Yes  
		  
	 
	 
		  Lua  
		  Yes  
		  
	 
	 
		  Mako Template  
		  Yes  
		  
	 
	 
		  Markdown  
		  Yes  
		  
	 
	 
		 Objective-C 
		  Yes  
		  
	 
	 
		 PHP 
		  Yes  
		  
	 
	 
		 Properties 
		  Yes  
		  
	 
	 
		 Python 
		  Yes  
		  
	 
	 
		 ReST file 
		  Yes  
		  
	 
	 
		 RegExp 
		  Yes  
		  
	 
	 
		 Ruby 
		  Yes  
		  
	 
	 
		  Rust  
		  Yes  
		  
	 
	 
		  SASS  
		  Yes  
		  
	 
	 
		 SQL 
		  Yes  
		  
	 
	 
		  Scala  
		  Yes  
		  
	 
	 
		 Tea 
		  Yes  
		  
	 
	 
		  Twig  
		  Yes  
		  
	 
	 
		 XML 
		  Yes  
		  
	 
	 
		  XPath  
		  Yes  
		  
	 
	 
		  YAML  
		  Yes  
		  
	 
 


Installation
------------

### Option 1: Install using "Import Settings..."

1. Clone this repository

2. Go to `File | Import Settings...` and specify the `intellij-colors-solarized` directory or the `settings.jar` file.
 Click `OK` in the dialog that appears.

3. Restart IntelliJ IDEA

4. **macOS**   
   * Go to `Preferences | Editor | Colors Scheme` and select one of the new color themes.

   **Windows / Linux**   
   * Go to `File | Settings... | Editor | Color Scheme` and select one of the new color themes.

### Option 2: Manual installation

1. Clone this repository

2.  Copy `Solarized Dark.icls` and `Solarized Light.icls` to your IntelliJ IDEA preferences
    color directory. The directory varies, depending on which JetBrains IDE you are using.

    *The colors directory may need to be created.*

    It is typically in:

    **macOS**
    * `~/Library/Preferences/IntelliJIdeaXX/colors` [(IntelliJ IDEA Ultimate Edition)][IntelliJ IDE settings],
    * `~/Library/Preferences/IdeaICXX/colors` [(IntelliJ IDEA Community Edition)][IntelliJ IDE settings],
    * `~/Library/Preferences/WebIDE70/colors` [(PHPStorm 7.0)][PHPStorm IDE settings],
    * `~/Library/Preferences/WebIDE80/colors` [(PHPStorm 8.0)][PHPStorm IDE settings],
    * `~/Library/Preferences/WebStorm8/colors` [(WebStorm 8.0)][WebStorm IDE settings].

    **Linux**
    * `~/.  /colors` Generic path,
    * `~/.IdeaICXX/config/colors` [(IntelliJ IDEA)][IntelliJ IDE settings],
    * `~/.PyCharmXX/colors` [(PyCharm)][PyCharm IDE settings].

    **Windows**
    * `%USERPROFILE%\.IdeaICXX\config\colors` [(IntelliJ IDEA Community Edition)][IntelliJ IDE settings],
    * `%USERPROFILE%\.PyCharm40\config\colors` [(PyCharm 4.5 Community Edition)][PyCharm IDE settings].

3. Restart IntelliJ IDEA

4. **macOS**   
   * Go to `Preferences | Editor | Colors Scheme` and select one of the new color themes.

   **Windows / Linux**   
   * Go to `File | Settings... | Editor | Color Scheme` and select one of the new color themes.

[IntelliJ IDE settings]: https://www.jetbrains.com/idea/help/project-and-ide-settings.html
[PHPStorm IDE settings]: https://www.jetbrains.com/phpstorm/help/project-and-ide-settings.html
[PyCharm IDE settings]: https://www.jetbrains.com/pycharm/help/project-and-ide-settings.html
[WebStorm IDE settings]: https://www.jetbrains.com/webstorm/help/project-and-ide-settings.html

Darcula
-------
Depending on the Look and Feel that you use the background
color for editor tabs will be different. The default L&amp;F has a light gray
background, while the Darcula L&amp;F has a dark background.

It is hard to find colors that work equally well on both light and dark backgrounds,
and therefore the `settings.jar` file contains Darcula versions of the color schemes. 
The only difference from the regular versions is that these color schemes inherit
their default colors from the Darcula theme rather than from Default.

Note About Fonts
-----------------
Unfortunately, font settings are included in the color settings files.
You should probably modify these in `Preferences | Editor | Colors & Fonts | Font`
after adding the color schemes to your IntelliJ IDEA installation.

Note About Committing Changes
-----------------------------
If you want to commit updates to the ICLS color scheme files, make sure to run the `buildjar.sh` script before committing to generate
an updated `settings.jar` file as well.
*The script has been tested on OS X, on other operating systems you're on your own.*


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)