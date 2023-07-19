# ken-markup

ken-markup is a markup language made for family websites of ken-zone.

[Here](https://ken-markup.vercel.app) is a demo website of ken-markup (in Korean).

## Usage 

1. Install the module 

    ```bash
    $ npm i ken-markup
    ```

1. Import the module 

    ```js
    import Translator from 'ken-markup'
    ```

    *You can import it with a different name (i.e. instead of Translator) if you want.*

1. Translate the text

    ```js
    translatedText = Translator.translate(originalText);
    ```

## Features

* It converts text into HTML elements.
* It supports enough grammar to write basic articles.
* It makes an index-table and footnotes automatically.
* Anyone can design it since it returns raw HTML code.

## Grammar

* \*\*bold**
* \//italic//
* \~~delete~~
* \_\_under__
* ^^sup^^
* ,,sub,,
* \[\[link]]

    You can show different text to the text of the link by using `|`;

    ```
    ex) [[name|link]]
    -> name // The href will be the link
    ```

    *If you want to add some rules to the link text, you can override `parseAnchorLink` method of the class.*

* \(\(note))

    You can set the index of notes as texts by using `|`.

    ```
    ex) ((index|note))
    -> [index] // The content will be the note
    ```

* \# title

    Title grammar has five levels which can be changed by a count of `#`.

    ```
    ex)
    # title 1.
    ## title 1.1.
    ## title 1.2.
    # title 2.
    ```

* :[table]:

    Table grammar starts with `:[` and ends with `]:`.

    To divide columns, insert `][` between the line.

    To divide rows, insert `\n][` into the end of the line that you want to break.

    ```
    ex)
    :[cell(0,0)][cell(0,1)
    ][cell(1,0)][cell(1,1)]:
    ```

* :(unordered list):

    Unordered list grammar starts with `:(` and ends with `):`.

    To divide items, insert `\n)(` into the end of the line that you want to break.

    ```
    ex)
    :(item1
    )(item2):
    ```

* :{ordered list}:

    The difference between ordered and unordered is only the change from `(` to `{`.

    ```
    ex)
    :{item1
    }{item2}:
    ```

* horizontal rule

    Four `-` are converted into a horizontal rule, which can be used to seperate sections or contents.

    ```
    ex)
    ----
    ```
    *Before this grammar, there should be a line break (\n).*