Her Majesty's PHP Interpreter
===================

This is the britanised fork of the official PHP Interpreter located at http://git.php.net.
I am looking for people who would like to help me britanising keywords.

Pull Requests
=============
I accept pull requests via github. Discussions are done on github.

Changed keywords
================
| Original Keyword | Britanised Keyword |
| :--------------- | :----------------- |
| new              | nouveau            |
| die              | cheerio            |
| if               | perchance          |
| endif            | finish_perchance   |
| elseif           | otherwise_perchance|
| else             | otherwise          |
| switch           | what_about         |
| endswitch        | finish_what_about
| case             | perhaps            |
| default          | on_the_off_chance  |
| break            | splendid           |
| echo             | announce           |
| class            | upper_class, middle_class, working_class |
| throw            | eject              |
| goto             | colonize           |

How to change keywords
======================
They are located in the following file: `Zend/zend_language_scanner.l`<br>
Inside this file you might want to look for line with the following comment `/* compute yyleng before each rule */`

Shortly after this comment you'll find a lot of keyword definitions like the following
```
<ST_IN_SCRIPTING>"exit" {
	RETURN_TOKEN(T_EXIT);
}
```

Perhaps you want to Britanise the *exit* keyword to say *abandon* ?
First thing to would be to change the line that says:
```
<ST_IN_SCRIPTING>"exit" {
```

To:

```
<ST_IN_SCRIPTING>"abandon" {
```

Then if you want to be able to compile *phar.php* you might want to navigate to `ext/phar` and look for files called

* *build_precommand.php*
* *phar/clicommand.inc*
* *phar/directorygraphiterator.inc*
* *phar/directorytreeiterator.inc*
* *phar/invertedregexiterator.inc*
* *phar/phar.inc*
* *phar/phar.inc*
* *phar/pharcommand.inc*

And change their contents to match the change. For example if there are any *exit* keywords within the code, you'll want to change then to *abandon* or you wont be able to finish compilation.

COMPILING
=========
1. Run `./buildconf`
2. Run `./configure --prefix <where_to_install_php>`
3. Run `make`
4. Run `make install`

That's it.<br>
Just a note that the first call to `make` can take a lot of time.
