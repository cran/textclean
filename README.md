textclean   
============


[![Project Status: Active - The project has reached a stable, usable
state and is being actively
developed.](http://www.repostatus.org/badges/0.1.0/active.svg)](http://www.repostatus.org/#active)
[![Build
Status](https://travis-ci.org/trinker/textclean.svg?branch=master)](https://travis-ci.org/trinker/textclean)
[![Coverage
Status](https://coveralls.io/repos/trinker/textclean/badge.svg?branch=master)](https://coveralls.io/r/trinker/textclean?branch=master)
[![](http://cranlogs.r-pkg.org/badges/textclean)](https://cran.r-project.org/package=textclean)

![](tools/textclean_logo/r_textclean.png)

**textclean** is a collection of tools to clean and process text. Many
of these tools have been taken from the **qdap** package and revamped to
be more intuitive, better named, and faster.


Table of Contents
============

-   [Functions](#functions)
-   [Installation](#installation)
-   [Contact](#contact)
-   [Demonstration](#demonstration)
    -   [Load the Packages/Data](#load-the-packagesdata)
    -   [Check Text](#check-text)
    -   [Row Filtering](#row-filtering)
    -   [Stripping](#stripping)
    -   [Subbing](#subbing)
        -   [Multiple Subs](#multiple-subs)
        -   [Match, Extract, Operate, Replacement Subs](#match-extract-operate-replacement-subs)
        -   [Stashing Character Pre-Sub](#stashing-character-pre-sub)
    -   [Replacement](#replacement)
        -   [Contractions](#contractions)
        -   [Emojis](#emojis)
        -   [Emoticons](#emoticons)
        -   [Grades](#grades)
        -   [HTML](#html)
        -   [Incomplete Sentences](#incomplete-sentences)
        -   [Internet Slang](#internet-slang)
        -   [Kerning](#kerning)
        -   [Names](#names)
        -   [Non-ASCII Characters](#non-ascii-characters)
        -   [Numbers](#numbers)
        -   [Ratings](#ratings)
        -   [Ordinal Numbers](#ordinal-numbers)
        -   [Symbols](#symbols)
        -   [White Space](#white-space)
        -   [Word Elongation](#word-elongation)
        -   [Tokens](#tokens)

Functions
============


The main functions, task category, & descriptions are summarized in the
table below:

<table>
<colgroup>
<col width="34%" />
<col width="17%" />
<col width="48%" />
</colgroup>
<thead>
<tr class="header">
<th>Function</th>
<th>Task</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>mgsub</code></td>
<td>subbing</td>
<td>Multiple <code>gsub</code></td>
</tr>
<tr class="even">
<td><code>fgsub</code></td>
<td>subbing</td>
<td>Functional matching replacement <code>gsub</code></td>
</tr>
<tr class="odd">
<td><code>sub_holder</code></td>
<td>subbing</td>
<td>Hold a value prior to a <code>strip</code></td>
</tr>
<tr class="even">
<td><code>swap</code></td>
<td>subbing</td>
<td>Simultaneously swap patterns 1 &amp; 2</td>
</tr>
<tr class="odd">
<td><code>strip</code></td>
<td>deletion</td>
<td>Remove all non word characters</td>
</tr>
<tr class="even">
<td><code>drop_empty_row</code></td>
<td>filter rows</td>
<td>Remove empty rows</td>
</tr>
<tr class="odd">
<td><code>drop_row</code>/<code>keep_row</code></td>
<td>filter rows</td>
<td>Filter rows matching a regex</td>
</tr>
<tr class="even">
<td><code>drop_NA</code></td>
<td>filter rows</td>
<td>Remove <code>NA</code> text rows</td>
</tr>
<tr class="odd">
<td><code>drop_element</code>/<code>keep_element</code></td>
<td>filter elements</td>
<td>Filter matching elements from a vector</td>
</tr>
<tr class="even">
<td><code>replace_contractions</code></td>
<td>replacement</td>
<td>Replace contractions with both words</td>
</tr>
<tr class="odd">
<td><code>replace_emoji</code></td>
<td>repalcement</td>
<td>Replace emojis with word equivalent or unique identifier</td>
</tr>
<tr class="even">
<td><code>replace_emoticon</code></td>
<td>repalcement</td>
<td>Replace emoticons with word equivalent</td>
</tr>
<tr class="odd">
<td><code>replace_grade</code></td>
<td>repalcement</td>
<td>Replace grades (e.g., &quot;A+&quot;) with word equivalent</td>
</tr>
<tr class="even">
<td><code>replace_html</code></td>
<td>replacement</td>
<td>Replace HTML tags and symbols</td>
</tr>
<tr class="odd">
<td><code>replace_incomplete</code></td>
<td>replacement</td>
<td>Replace incomplete sentence end-marks</td>
</tr>
<tr class="even">
<td><code>replace_internet_slang</code></td>
<td>replacment</td>
<td>Replace Internet slang with word equivalents</td>
</tr>
<tr class="odd">
<td><code>replace_kern</code></td>
<td>replacement</td>
<td>Replace spaces for &gt;2 letter, all cap, words containing spaces in between letters</td>
</tr>
<tr class="even">
<td><code>replace_names</code></td>
<td>replacement</td>
<td>Replace common first/last names</td>
</tr>
<tr class="odd">
<td><code>replace_non_ascii</code></td>
<td>replacement</td>
<td>Replace non-ascii with equivalent or remove</td>
</tr>
<tr class="even">
<td><code>replace_number</code></td>
<td>replacement</td>
<td>Replace common numbers</td>
</tr>
<tr class="odd">
<td><code>replace_ordinal</code></td>
<td>replacement</td>
<td>Replace common ordinal number form</td>
</tr>
<tr class="even">
<td><code>replace_rating</code></td>
<td>repalcement</td>
<td>Replace ratings (e.g., &quot;10 out of 10&quot;, &quot;3 stars&quot;) with word equivalent</td>
</tr>
<tr class="odd">
<td><code>replace_symbol</code></td>
<td>replacement</td>
<td>Replace common symbols</td>
</tr>
<tr class="even">
<td><code>replace_white</code></td>
<td>replacement</td>
<td>Replace regex white space characters</td>
</tr>
<tr class="odd">
<td><code>replace_token</code></td>
<td>replacement</td>
<td>Remove or replace a vector of tokens with a single value</td>
</tr>
<tr class="even">
<td><code>replace_word_elongation</code></td>
<td>repalcement</td>
<td>Replace word elongations with shortened form</td>
</tr>
<tr class="odd">
<td><code>add_comma_space</code></td>
<td>replacement</td>
<td>Replace non-space after comma</td>
</tr>
<tr class="even">
<td><code>add_missing_endmark</code></td>
<td>replacement</td>
<td>Replace missing endmarks with desired symbol</td>
</tr>
<tr class="odd">
<td><code>make_plural</code></td>
<td>replacement</td>
<td>Add plural endings to singular noun forms</td>
</tr>
<tr class="even">
<td><code>check_text</code></td>
<td>check</td>
<td>Text report of potential issues</td>
</tr>
<tr class="odd">
<td><code>has_endmark</code></td>
<td>check</td>
<td>Check if an element has an end-mark</td>
</tr>
</tbody>
</table>

Installation
============

To download the development version of **textclean**:

Download the [zip
ball](https://github.com/trinker/textclean/zipball/master) or [tar
ball](https://github.com/trinker/textclean/tarball/master), decompress
and run `R CMD INSTALL` on it, or use the **pacman** package to install
the development version:

    if (!require("pacman")) install.packages("pacman")
    pacman::p_load_gh(
        "trinker/lexicon",    
        "trinker/textclean"
    )

Contact
=======

You are welcome to:    
- submit suggestions and bug-reports at: <https://github.com/trinker/textclean/issues>    
- send a pull request on: <https://github.com/trinker/textclean/>    
- compose a friendly e-mail to: <tyler.rinker@gmail.com>    

Demonstration
=============

Load the Packages/Data
----------------------

    if (!require("pacman")) install.packages("pacman")
    pacman::p_load(dplyr)
    pacman::p_load_gh("trinker/textshape", "trinker/lexicon", "trinker/textclean")

Check Text
----------

One of the most useful tools in **textclean** is `check_text` which
scans text variables and reports potential problems. Not all potential
problems are definite problems for analysis but the report provides an
overview of what may need further preparation. The report also provides
suggested functions for the reported problems. The report provides
information on the following:

1.  **non\_character** - Text that is `factor`.
2.  **missing\_ending\_punctuation** - Text with no endmark at the end
    of the string.
3.  **empty** - Text that contains an empty element (i.e., `""`).
4.  **double\_punctuation** - Text that contains two punctuation marks
    in the same string.
5.  **non\_space\_after\_comma** - Text that contains commas with no
    space after them.
6.  **no\_alpha** - Text that contains string elements with no
    alphabetic characters.
7.  **non\_ascii** - Text that contains non-ASCII characters.
8.  **missing\_value** - Text that contains missing values (i.e., `NA`).
9.  **containing\_escaped** - Text that contains escaped (see
    `?Quotes`).
10. **containing\_digits** - Text that contains digits.
11. **containing\_html** - Text that potentially contains HTML markup.
12. **indicating\_incomplete** - Text that contains endmarks that are
    indicative of incomplete/trailing sentences (e.g., `...`).
13. **potentially\_misspelled** - Text that contains potentially
    misspelled words.

Here is an example:

    x <- c("i like", "<p>i want. </p>. thet them ther .", "I am ! that|", "", NA, 
        "&quot;they&quot; they,were there", ".", "   ", "?", "3;", "I like goud eggs!", 
        "bi\xdfchen Z\xfcrcher", "i 4like...", "\\tgreat",  "She said \"yes\"")
    Encoding(x) <- "latin1"
    x <- as.factor(x)
    check_text(x)

    ## 
    ## =============
    ## NON CHARACTER
    ## =============
    ## 
    ## Text is a factor.
    ## 
    ## *Suggestion: Consider using `as.character` or `stringsAsFactors = FALSE` when reading in
    ## 
    ## ==========================
    ## MISSING ENDING PUNCTUATION
    ## ==========================
    ## 
    ## The following observations were missing ending punctuation:
    ## 
    ## 1, 3, 4, 5, 6, 8, 10, 12, 14, 15
    ## 
    ## The following text is missing ending punctuation:
    ## 
    ## 1: i like
    ## 3: I am ! that|
    ## 4: 
    ## 5: NA
    ## 6: &quot;they&quot; they,were there
    ## 8:    
    ## 10: 3;
    ## 12: bißchen Zürcher
    ## 14: \tgreat
    ## 15: She said "yes"
    ## 
    ## *Suggestion: Consider cleaning the raw text or running `add_missing_endmark`
    ## 
    ## 
    ## =====
    ## EMPTY
    ## =====
    ## 
    ## The following observations were empty:
    ## 
    ## 4, 8
    ## 
    ## The following text is empty:
    ## 
    ## 4: 
    ## 8:    
    ## 
    ## *Suggestion: Consider running `filter_empty`
    ## 
    ## 
    ## ==================
    ## DOUBLE PUNCTUATION
    ## ==================
    ## 
    ## The following observations were double punctuation:
    ## 
    ## 2
    ## 
    ## The following text is double punctuation:
    ## 
    ## 2: <p>i want. </p>. thet them ther .
    ## 
    ## *Suggestion: Consider running `textshape::split_sentence`
    ## 
    ## 
    ## =====================
    ## NON SPACE AFTER COMMA
    ## =====================
    ## 
    ## The following observations were non space after comma:
    ## 
    ## 6
    ## 
    ## The following text is non space after comma:
    ## 
    ## 6: &quot;they&quot; they,were there
    ## 
    ## *Suggestion: Consider running `add_comma_space`
    ## 
    ## 
    ## ========
    ## NO ALPHA
    ## ========
    ## 
    ## The following observations were no alpha:
    ## 
    ## 4, 7, 8, 9, 10
    ## 
    ## The following text is no alpha:
    ## 
    ## 4: 
    ## 7: .
    ## 8:    
    ## 9: ?
    ## 10: 3;
    ## 
    ## *Suggestion: Consider cleaning the raw text or running `filter_row`
    ## 
    ## 
    ## =========
    ## NON ASCII
    ## =========
    ## 
    ## The following observations were non ascii:
    ## 
    ## 12
    ## 
    ## The following text is non ascii:
    ## 
    ## 12: bißchen Zürcher
    ## 
    ## *Suggestion: Consider running `replace_non_ascii`
    ## 
    ## 
    ## =============
    ## MISSING VALUE
    ## =============
    ## 
    ## The following observations were missing value:
    ## 
    ## 5
    ## 
    ## *Suggestion: Consider running `filter_NA`
    ## 
    ## 
    ## ==================
    ## CONTAINING ESCAPED
    ## ==================
    ## 
    ## The following observations were containing escaped:
    ## 
    ## 14
    ## 
    ## The following text is containing escaped:
    ## 
    ## 14: \tgreat
    ## 
    ## *Suggestion: Consider using `replace_white`
    ## 
    ## 
    ## =================
    ## CONTAINING DIGITS
    ## =================
    ## 
    ## The following observations were containing digits:
    ## 
    ## 10, 13
    ## 
    ## The following text is containing digits:
    ## 
    ## 10: 3;
    ## 13: i 4like...
    ## 
    ## *Suggestion: Consider using `replace_number`
    ## 
    ## 
    ## ===============
    ## CONTAINING HTML
    ## ===============
    ## 
    ## The following observations were containing html:
    ## 
    ## 2, 6
    ## 
    ## The following text is containing html:
    ## 
    ## 2: <p>i want. </p>. thet them ther .
    ## 6: &quot;they&quot; they,were there
    ## 
    ## *Suggestion: Consider running `replace_html`
    ## 
    ## 
    ## =====================
    ## INDICATING INCOMPLETE
    ## =====================
    ## 
    ## The following observations were indicating incomplete:
    ## 
    ## 13
    ## 
    ## The following text is indicating incomplete:
    ## 
    ## 13: i 4like...
    ## 
    ## *Suggestion: Consider using `replace_incomplete`
    ## 
    ## 
    ## ======================
    ## POTENTIALLY MISSPELLED
    ## ======================
    ## 
    ## The following observations were potentially misspelled:
    ## 
    ## 2, 11, 12, 14
    ## 
    ## The following text is potentially misspelled:
    ## 
    ## 2: <p>i want. </p>. <<thet>> them <<ther>> .
    ## 11: I like <<goud>> eggs!
    ## 12: <<bißchen>> <<Zürcher>>
    ## 14: \<<tgreat>>
    ## 
    ## *Suggestion: Consider running `hunspell::hunspell_find` & `hunspell::hunspell_suggest`

And if all is well the user should be greeted by a cow:

    y <- c("A valid sentence.", "yet another!")
    check_text(y)

    ## 
    ##  ------- 
    ## No problems found!
    ## You are flawless! 
    ##  -------- 
    ##     \   ^__^ 
    ##      \  (oo)\ ________ 
    ##         (__)\         )\ /\ 
    ##              ||------w|
    ##              ||      ||

Row Filtering
-------------

It is useful to drop/remove empty rows or unwanted rows (for example the
researcher dialogue from a transcript). The `drop_empty_row` &
`drop_row` do empty row do just this. First I'll demo the removal of
empty rows.

    ## create a data set wit empty rows
    (dat <- rbind.data.frame(DATA[, c(1, 4)], matrix(rep(" ", 4), 
        ncol =2, dimnames=list(12:13, colnames(DATA)[c(1, 4)]))))

    ##        person                                 state
    ## 1         sam         Computer is fun. Not too fun.
    ## 2        greg               No it's not, it's dumb.
    ## 3     teacher                    What should we do?
    ## 4         sam                  You liar, it stinks!
    ## 5        greg               I am telling the truth!
    ## 6       sally                How can we be certain?
    ## 7        greg                      There is no way.
    ## 8         sam                       I distrust you.
    ## 9       sally           What are you talking about?
    ## 10 researcher         Shall we move on?  Good then.
    ## 11       greg I'm hungry.  Let's eat.  You already?
    ## 12                                                 
    ## 13

    drop_empty_row(dat)

    ##        person                                 state
    ## 1         sam         Computer is fun. Not too fun.
    ## 2        greg               No it's not, it's dumb.
    ## 3     teacher                    What should we do?
    ## 4         sam                  You liar, it stinks!
    ## 5        greg               I am telling the truth!
    ## 6       sally                How can we be certain?
    ## 7        greg                      There is no way.
    ## 8         sam                       I distrust you.
    ## 9       sally           What are you talking about?
    ## 10 researcher         Shall we move on?  Good then.
    ## 11       greg I'm hungry.  Let's eat.  You already?

Next we drop out rows. The `drop_row` function takes a data set, a
column (named or numeric position) and regex terms to search for. The
`terms` argument takes regex(es) allowing for partial matching. `terms`
is case sensitive but can be changed via the `ignore.case` argument.

    drop_row(dataframe = DATA, column = "person", terms = c("sam", "greg"))

    ##       person sex adult                         state code
    ## 1    teacher   m     1            What should we do?   K3
    ## 2      sally   f     0        How can we be certain?   K6
    ## 3      sally   f     0   What are you talking about?   K9
    ## 4 researcher   f     1 Shall we move on?  Good then.  K10

    drop_row(DATA, 1, c("sam", "greg"))

    ##       person sex adult                         state code
    ## 1    teacher   m     1            What should we do?   K3
    ## 2      sally   f     0        How can we be certain?   K6
    ## 3      sally   f     0   What are you talking about?   K9
    ## 4 researcher   f     1 Shall we move on?  Good then.  K10

    keep_row(DATA, 1, c("sam", "greg"))

    ##   person sex adult                                 state code
    ## 1    sam   m     0         Computer is fun. Not too fun.   K1
    ## 2   greg   m     0               No it's not, it's dumb.   K2
    ## 3    sam   m     0                  You liar, it stinks!   K4
    ## 4   greg   m     0               I am telling the truth!   K5
    ## 5   greg   m     0                      There is no way.   K7
    ## 6    sam   m     0                       I distrust you.   K8
    ## 7   greg   m     0 I'm hungry.  Let's eat.  You already?  K11

    drop_row(DATA, "state", c("Comp"))

    ##        person sex adult                                 state code
    ## 1        greg   m     0               No it's not, it's dumb.   K2
    ## 2     teacher   m     1                    What should we do?   K3
    ## 3         sam   m     0                  You liar, it stinks!   K4
    ## 4        greg   m     0               I am telling the truth!   K5
    ## 5       sally   f     0                How can we be certain?   K6
    ## 6        greg   m     0                      There is no way.   K7
    ## 7         sam   m     0                       I distrust you.   K8
    ## 8       sally   f     0           What are you talking about?   K9
    ## 9  researcher   f     1         Shall we move on?  Good then.  K10
    ## 10       greg   m     0 I'm hungry.  Let's eat.  You already?  K11

    drop_row(DATA, "state", c("I "))

    ##       person sex adult                                 state code
    ## 1        sam   m     0         Computer is fun. Not too fun.   K1
    ## 2       greg   m     0               No it's not, it's dumb.   K2
    ## 3    teacher   m     1                    What should we do?   K3
    ## 4        sam   m     0                  You liar, it stinks!   K4
    ## 5      sally   f     0                How can we be certain?   K6
    ## 6       greg   m     0                      There is no way.   K7
    ## 7      sally   f     0           What are you talking about?   K9
    ## 8 researcher   f     1         Shall we move on?  Good then.  K10
    ## 9       greg   m     0 I'm hungry.  Let's eat.  You already?  K11

    drop_row(DATA, "state", c("you"), ignore.case = TRUE)

    ##       person sex adult                         state code
    ## 1        sam   m     0 Computer is fun. Not too fun.   K1
    ## 2       greg   m     0       No it's not, it's dumb.   K2
    ## 3    teacher   m     1            What should we do?   K3
    ## 4       greg   m     0       I am telling the truth!   K5
    ## 5      sally   f     0        How can we be certain?   K6
    ## 6       greg   m     0              There is no way.   K7
    ## 7 researcher   f     1 Shall we move on?  Good then.  K10

Stripping
---------

Often it is useful to remove all non relevant symbols and case from a
text (letters, spaces, and apostrophes are retained). The `strip`
function accomplishes this. The `char.keep` argument allows the user to
retain characters.

    strip(DATA$state)

    ##  [1] "computer is fun not too fun"      "no it's not it's dumb"           
    ##  [3] "what should we do"                "you liar it stinks"              
    ##  [5] "i am telling the truth"           "how can we be certain"           
    ##  [7] "there is no way"                  "i distrust you"                  
    ##  [9] "what are you talking about"       "shall we move on good then"      
    ## [11] "i'm hungry let's eat you already"

    strip(DATA$state, apostrophe.remove = TRUE)

    ##  [1] "computer is fun not too fun"    "no its not its dumb"           
    ##  [3] "what should we do"              "you liar it stinks"            
    ##  [5] "i am telling the truth"         "how can we be certain"         
    ##  [7] "there is no way"                "i distrust you"                
    ##  [9] "what are you talking about"     "shall we move on good then"    
    ## [11] "im hungry lets eat you already"

    strip(DATA$state, char.keep = c("?", "."))

    ##  [1] "computer is fun. not too fun."      
    ##  [2] "no it's not it's dumb."             
    ##  [3] "what should we do?"                 
    ##  [4] "you liar it stinks"                 
    ##  [5] "i am telling the truth"             
    ##  [6] "how can we be certain?"             
    ##  [7] "there is no way."                   
    ##  [8] "i distrust you."                    
    ##  [9] "what are you talking about?"        
    ## [10] "shall we move on? good then."       
    ## [11] "i'm hungry. let's eat. you already?"

Subbing
-------

### Multiple Subs

`gsub` is a great tool but often the user wants to replace a vector of
elements with another vector. `mgsub` allows for a vector of patterns
and replacements. Note that the first argument of `mgsub` is the data,
not the `pattern` as is standard with base R's `gsub`. This allows
`mgsub` to be used in a **magrittr** pipeline more easily. Also note
that by default `fixed = TRUE`. This means the search `pattern` is not a
regex per-se. This makes the replacement much faster when a regex search
is not needed. `mgsub` also reorders the patterns to ensure patterns
contained within patterns don't over write the longer pattern. For
example if the pattern `c('i', 'it')` is given the longer `'it'` is
replaced first (though `order.pattern = FALSE` can be used to negate
this feature).

    mgsub(DATA$state, c("it's", "I'm"), c("<<it is>>", "<<I am>>"))

    ##  [1] "Computer is fun. Not too fun."             
    ##  [2] "No <<it is>> not, <<it is>> dumb."         
    ##  [3] "What should we do?"                        
    ##  [4] "You liar, it stinks!"                      
    ##  [5] "I am telling the truth!"                   
    ##  [6] "How can we be certain?"                    
    ##  [7] "There is no way."                          
    ##  [8] "I distrust you."                           
    ##  [9] "What are you talking about?"               
    ## [10] "Shall we move on?  Good then."             
    ## [11] "<<I am>> hungry.  Let's eat.  You already?"

    mgsub(DATA$state, "[[:punct:]]", "<<PUNCT>>", fixed = FALSE)

    ##  [1] "Computer is fun<<PUNCT>> Not too fun<<PUNCT>>"                                
    ##  [2] "No it<<PUNCT>>s not<<PUNCT>> it<<PUNCT>>s dumb<<PUNCT>>"                      
    ##  [3] "What should we do<<PUNCT>>"                                                   
    ##  [4] "You liar<<PUNCT>> it stinks<<PUNCT>>"                                         
    ##  [5] "I am telling the truth<<PUNCT>>"                                              
    ##  [6] "How can we be certain<<PUNCT>>"                                               
    ##  [7] "There is no way<<PUNCT>>"                                                     
    ##  [8] "I distrust you<<PUNCT>>"                                                      
    ##  [9] "What are you talking about<<PUNCT>>"                                          
    ## [10] "Shall we move on<<PUNCT>>  Good then<<PUNCT>>"                                
    ## [11] "I<<PUNCT>>m hungry<<PUNCT>>  Let<<PUNCT>>s eat<<PUNCT>>  You already<<PUNCT>>"

    mgsub(DATA$state, c("i", "it"), c("<<I>>", "[[IT]]"))

    ##  [1] "Computer <<I>>s fun. Not too fun."    
    ##  [2] "No [[IT]]'s not, [[IT]]'s dumb."      
    ##  [3] "What should we do?"                   
    ##  [4] "You l<<I>>ar, [[IT]] st<<I>>nks!"     
    ##  [5] "I am tell<<I>>ng the truth!"          
    ##  [6] "How can we be certa<<I>>n?"           
    ##  [7] "There <<I>>s no way."                 
    ##  [8] "I d<<I>>strust you."                  
    ##  [9] "What are you talk<<I>>ng about?"      
    ## [10] "Shall we move on?  Good then."        
    ## [11] "I'm hungry.  Let's eat.  You already?"

    mgsub(DATA$state, c("i", "it"), c("<<I>>", "[[IT]]"), order.pattern = FALSE)

    ##  [1] "Computer <<I>>s fun. Not too fun."    
    ##  [2] "No <<I>>t's not, <<I>>t's dumb."      
    ##  [3] "What should we do?"                   
    ##  [4] "You l<<I>>ar, <<I>>t st<<I>>nks!"     
    ##  [5] "I am tell<<I>>ng the truth!"          
    ##  [6] "How can we be certa<<I>>n?"           
    ##  [7] "There <<I>>s no way."                 
    ##  [8] "I d<<I>>strust you."                  
    ##  [9] "What are you talk<<I>>ng about?"      
    ## [10] "Shall we move on?  Good then."        
    ## [11] "I'm hungry.  Let's eat.  You already?"

### Match, Extract, Operate, Replacement Subs

Again, `gsub` is a great tool but sometimes the user wants to match a
pattern, extract that pattern, operate a function over that pattern, and
then replace the original match. The `fgsub` function allows the user to
perform this operation. It is a stripped down version of `gsubfn` from
the **gsubfn** package. For more versatile needs please see the
**gsubfn** package.

    fgsub(
        x = c(NA, 'df dft sdf', 'sd fdggg sd dfhhh d', 'ddd'),
        pattern = "\\b\\w*([a-z])(\\1{2,})\\w*\\b",
        fun = function(x) {paste0('<<', paste(rev(strsplit(x, '')[[1]]), collapse =''), '>>')}
    )

    ## [1] NA                            "df dft sdf"                 
    ## [3] "sd <<gggdf>> sd <<hhhfd>> d" "<<ddd>>"

### Stashing Character Pre-Sub

There are times the user may want to stash a set of characters before
subbing out and then return the stashed characters. An example of this
is when a researcher wants to remove punctuation but not emoticons. The
`subholder` function provides tooling to stash the emoticons, allow a
punctuation stripping, and then return the emoticons. First I'll create
some fake text data with emoticons, then stash the emoticons (using a
unique text key to hold their place), then I'll strip out the
punctuation, and last put the stashed emoticons back.

    (fake_dat <- paste(hash_emoticons[1:11, 1, with=FALSE][[1]], DATA$state))

    ##  [1] "#-o Computer is fun. Not too fun."        
    ##  [2] "$_$ No it's not, it's dumb."              
    ##  [3] "(*v*) What should we do?"                 
    ##  [4] "(-: You liar, it stinks!"                 
    ##  [5] "(-}{-) I am telling the truth!"           
    ##  [6] "(.V.) How can we be certain?"             
    ##  [7] ")-: There is no way."                     
    ##  [8] "*-* I distrust you."                      
    ##  [9] "*<:o) What are you talking about?"        
    ## [10] "//_^ Shall we move on?  Good then."       
    ## [11] "0;) I'm hungry.  Let's eat.  You already?"

    (m <- sub_holder(fake_dat, hash_emoticons[[1]]))

    ##  [1] "zzzplaceholderazzz Computer is fun. Not too fun."        
    ##  [2] "zzzplaceholderbzzz No it's not, it's dumb."              
    ##  [3] "zzzplaceholderczzz What should we do?"                   
    ##  [4] "zzzplaceholderdzzz You liar, it stinks!"                 
    ##  [5] "zzzplaceholderezzz I am telling the truth!"              
    ##  [6] "zzzplaceholderfzzz How can we be certain?"               
    ##  [7] "zzzplaceholdergzzz There is no way."                     
    ##  [8] "zzzplaceholderhzzz I distrust you."                      
    ##  [9] "zzzplaceholderizzz What are you talking about?"          
    ## [10] "zzzplaceholderjzzz Shall we move on?  Good then."        
    ## [11] "zzzplaceholderkzzz I'm hungry.  Let's eat.  You already?"

    (m_stripped <-strip(m$output))

    ##  [1] "zzzplaceholderazzz computer is fun not too fun"     
    ##  [2] "zzzplaceholderbzzz no it's not it's dumb"           
    ##  [3] "zzzplaceholderczzz what should we do"               
    ##  [4] "zzzplaceholderdzzz you liar it stinks"              
    ##  [5] "zzzplaceholderezzz i am telling the truth"          
    ##  [6] "zzzplaceholderfzzz how can we be certain"           
    ##  [7] "zzzplaceholdergzzz there is no way"                 
    ##  [8] "zzzplaceholderhzzz i distrust you"                  
    ##  [9] "zzzplaceholderizzz what are you talking about"      
    ## [10] "zzzplaceholderjzzz shall we move on good then"      
    ## [11] "zzzplaceholderkzzz i'm hungry let's eat you already"

    m$unhold(m_stripped)

    ##  [1] "#-o computer is fun not too fun"     
    ##  [2] "$_$ no it's not it's dumb"           
    ##  [3] "(*v*) what should we do"             
    ##  [4] "(-: you liar it stinks"              
    ##  [5] "(-}{-) i am telling the truth"       
    ##  [6] "(.V.) how can we be certain"         
    ##  [7] ")-: there is no way"                 
    ##  [8] "*-* i distrust you"                  
    ##  [9] "*<:o) what are you talking about"    
    ## [10] "//_^ shall we move on good then"     
    ## [11] "0;) i'm hungry let's eat you already"

Replacement
-----------

**textclean** contains tools to replace substrings within text with
other substrings that may be easier to analyze. This section outlines
the uses of these tools.

### Contractions

Some analysis techniques require contractions to be replaced with their
multi-word forms (e.g., "I'll" -&gt; "I will"). `replace_contrction`
provides this functionality.

    x <- c("Mr. Jones isn't going.",  
        "Check it out what's going on.",
        "He's here but didn't go.",
        "the robot at t.s. wasn't nice", 
        "he'd like it if i'd go away")

    replace_contraction(x)

    ## [1] "Mr. Jones is not going."            
    ## [2] "Check it out what is going on."     
    ## [3] "he is here but did not go."         
    ## [4] "the robot at t.s. was not nice"     
    ## [5] "he would like it if I would go away"

### Emojis

Similar to emoticons, emoji tokens may be ignored if they are not in a
computer readable form. `replace_emoji` replaces emojis with their word
forms equivalents.

    x <- read.delim(system.file("docs/r_tweets.txt", package = "textclean"), 
        stringsAsFactors = FALSE)[[3]][1:3]

    x

    ## [1] "Hello, helpful! ðŸ“¦âŒðŸ‘¾ debugme: Easy & efficient debugging for R packages ðŸ‘¨ðŸ»â€ðŸ’» @GaborCsardi https://buff.ly/2nNKcps  #rstats"
    ## [2] "Did you ever get bored and accidentally create a ðŸ“¦ to make #Rstats speak on a Mac? I have -> "                                            
    ## [3] "A gift to my fellow nfl loving #rstats folks this package is ðŸ’¥ðŸ’¥"

    replace_emoji(x)

    ## [1] "Hello, helpful! package cross mark alien monster debugme: Easy & efficient debugging for R packages man <f0><9f><8f><bb><e2><80><8d> laptop computer @GaborCsardi https://buff.ly/2nNKcps #rstats"
    ## [2] "Did you ever get bored and accidentally create a package to make #Rstats speak on a Mac? I have -> "                                                                                              
    ## [3] "A gift to my fellow nfl loving #rstats folks this package is collision collision "

### Emoticons

Some analysis techniques examine words, meaning emoticons may be
ignored. `replace_emoticon` replaces emoticons with their word forms
equivalents.

    x <- c(
        "text from: http://www.webopedia.com/quick_ref/textmessageabbreviations_02.asp",
        "... understanding what different characters used in smiley faces mean:",
        "The close bracket represents a sideways smile  )",
        "Add in the colon and you have sideways eyes   :",
        "Put them together to make a smiley face  :)",
        "Use the dash -  to add a nose   :-)",
        "Change the colon to a semi-colon ; and you have a winking face ;)  with a nose  ;-)",
        "Put a zero 0 (halo) on top and now you have a winking, smiling angel 0;) with a nose 0;-)",
        "Use the letter 8 in place of the colon for sunglasses 8-)",
        "Use the open bracket ( to turn the smile into a frown  :-("
    )

    replace_emoticon(x)

    ##  [1] "text from: http://www.webopedia.com/quick_ref/textmessageabbreviations_02.asp"                
    ##  [2] "... understanding what different characters used in smiley faces mean:"                       
    ##  [3] "The close bracket represents a sideways smile )"                                              
    ##  [4] "Add in the colon and you have sideways eyes :"                                                
    ##  [5] "Put them together to make a smiley face happy "                                               
    ##  [6] "Use the dash - to add a nose happy "                                                          
    ##  [7] "Change the colon to a semi-colon ; and you have a winking face winking with a nose winking "  
    ##  [8] "Put a zero 0 (halo) on top and now you have a winking, smiling angel angel with a nose angel "
    ##  [9] "Use the letter 8 in place of the colon for sunglasses glasses "                               
    ## [10] "Use the open bracket ( to turn the smile into a frown sad "

### Grades

In analysis where grades may be discussed it may be useful to convert
the letter forms into word meanings. The `replace_grade` can be used for
this task.

    text <- c(
        "I give an A+",
        "He deserves an F",
        "It's C+ work",
        "A poor example deserves a C!"
    )
    replace_grade(text)

    ## [1] "I give an very excellent excellent"
    ## [2] "He deserves an very very bad"      
    ## [3] "It's slightly above average work"  
    ## [4] "A poor example deserves a average!"

### HTML

Sometimes HTML tags and symbols stick around like pesky gnats. The
`replace_html` function makes light work of them.

    x <- c(
        "<bold>Random</bold> text with symbols: &nbsp; &lt; &gt; &amp; &quot; &apos;",
        "<p>More text</p> &cent; &pound; &yen; &euro; &copy; &reg;"
    )

    replace_html(x)

    ## [1] " Random  text with symbols:   < > & \" '"         
    ## [2] " More text   cents   pounds   yen   euro  (c) (r)"

### Incomplete Sentences

Sometimes an incomplete sentence is denoted with multiple end marks or
no punctuation at all. `replace_incomplete` standardizes these sentences
with a pipe (`|`) endmark (or one of the user's choice).

    x <- c("the...",  "I.?", "you.", "threw..", "we?")
    replace_incomplete(x)

    ## [1] "the|"   "I|"     "you."   "threw|" "we?"

    replace_incomplete(x, '...')

    ## [1] "the..."   "I..."     "you."     "threw..." "we?"

### Internet Slang

Often in informal written and spoken communication (e.g., Twitter,
texting, Facebook, etc.) people use Internet slang, shorter
abbreviations and acronyms, to replace longer word sequences. These
replacements may obfuscate the meaning when the machine attempts to
analyze the text. The `replace_internet_slang` function replaces the
slang with longer word equivalents that are more easily analyzed by
machines.

    x <- c(
        "TGIF and a big w00t!  The weekend is GR8!",
        "NP it was my pleasure: EOM",
        'w8...this n00b needs me to say LMGTFY...lol.',
        NA
    )

    replace_internet_slang(x)

    ## [1] "thank god, it's friday and a big hooray!  The weekend is great!"                   
    ## [2] "no problem it was my pleasure: end of message"                                     
    ## [3] "wait...this newbie needs me to say let me google that for you...laughing out loud."
    ## [4] NA

### Kerning

In typography kerning is the adjustment of spacing. Often, in informal
writing, adding manual spaces (a form of kerning) coupled with all
capital letters is used for emphasis (e.g., `"She's the B O M B!"`).
These word forms would look like noise in most analysis and would likely
be removed as a stopword when in fact they likely carry a great deal of
meaning. The `replace_kern` function looks for 3 or more consecutive
capital letters with spaces in between and removes the spaces.

    x <- c(
        "Welcome to A I: the best W O R L D!",
        "Hi I R is the B O M B for sure: we A G R E E indeed.",
        "A sort C A T indeed!",
        NA
    )

    replace_kern(x)

    ## [1] "Welcome to A I: the best WORLD!"              
    ## [2] "Hi I R is the BOMB for sure: we AGREE indeed."
    ## [3] "A sort CAT indeed!"                           
    ## [4] NA

### Names

Often one will want to standardize text by removing first and last
names. The `replace_names` function quickly removes/replaces common
first and last names. This can be made more targeted by feeding a vector
of names extractracted via a named entity extractor.

    x <- c(
        "Mary Smith is not here",
         "Karen is not a nice person",
         "Will will do it",
        NA
    )
     
    replace_names(x)

    ## [1] "  is not here"         " is not a nice person" " will do it"          
    ## [4] NA

    replace_names(x, replacement = '<<NAME>>')

    ## [1] "<<NAME>> <<NAME>> is not here" "<<NAME>> is not a nice person"
    ## [3] "<<NAME>> will do it"           NA

### Non-ASCII Characters

R can choke on non-ASCII characters. They can be re-encoded but the new
encoding may lack interpretability (e.g., ¢ may be converted to `\xA2`
which is not easily understood or likely to be matched in a hash look
up). `replace_non_ascii` attempts to replace common non-ASCII characters
with a text representation (e.g., ¢ becomes "cent") Non recognized
non-ASCII characters are simply removed (unless
`remove.nonconverted = FALSE`).

    x <- c(
        "Hello World", "6 Ekstr\xf8m", "J\xf6reskog", "bi\xdfchen Z\xfcrcher",
        'This is a \xA9 but not a \xAE', '6 \xF7 2 = 3', 'fractions \xBC, \xBD, \xBE',
        'cows go \xB5', '30\xA2'
    )
    Encoding(x) <- "latin1"
    x

    ## [1] "Hello World"             "6 Ekstrøm"              
    ## [3] "Jöreskog"                "bißchen Zürcher"        
    ## [5] "This is a © but not a ®" "6 ÷ 2 = 3"              
    ## [7] "fractions ¼, ½, ¾"       "cows go µ"              
    ## [9] "30¢"

    replace_non_ascii(x)

    ## [1] "Hello World"                 "6 Ekstrom"                  
    ## [3] "Joreskog"                    "bisschen Zurcher"           
    ## [5] "This is a (C) but not a (R)" "6 / 2 = 3"                  
    ## [7] "fractions 1/4, 1/2, 3/4"     "cows go mu"                 
    ## [9] "30 cent"

    replace_non_ascii(x, remove.nonconverted = FALSE)

    ## [1] "Hello World"                 "6 Ekstrom"                  
    ## [3] "Joreskog"                    "bisschen Zurcher"           
    ## [5] "This is a (C) but not a (R)" "6 / 2 = 3"                  
    ## [7] "fractions  1/4,  1/2,  3/4"  "cows go <c2> mu "           
    ## [9] "30<c2> cent "

### Numbers

Some analysis requires numbers to be converted to text form.
`replace_number` attempts to perform this task. `replace_number` handles
comma separated numbers as well.

    x <- c("I like 346,457 ice cream cones.", "They are 99 percent good")
    y <- c("I like 346457 ice cream cones.", "They are 99 percent good")
    replace_number(x)

    ## [1] "I like three hundred forty six thousand four hundred fifty seven ice cream cones."
    ## [2] "They are ninety nine percent good"

    replace_number(y)

    ## [1] "I like three hundred forty six thousand four hundred fifty seven ice cream cones."
    ## [2] "They are ninety nine percent good"

    replace_number(x, num.paste = TRUE)

    ## [1] "I like threehundredfortysixthousandfourhundredfiftyseven ice cream cones."
    ## [2] "They are ninetynine percent good"

    replace_number(x, remove=TRUE)

    ## [1] "I like  ice cream cones." "They are  percent good"

### Ratings

Some texts use ratings to convey satisfaction with a particular object.
The `replace_rating` function replaces the more abstract rating with
word equivalents.

    x <- c("This place receives 5 stars for their APPETIZERS!!!",
         "Four stars for the food & the guy in the blue shirt for his great vibe!",
         "10 out of 10 for both the movie and trilogy.",
         "* Both the Hot & Sour & the Egg Flower Soups were absolutely 5 Stars!",
         "For service, I give them no stars.", "This place deserves no stars.",
         "10 out of 10 stars.",
         "My rating: just 3 out of 10.",
         "If there were zero stars I would give it zero stars.",
         "Rating: 1 out of 10.",
         "I gave it 5 stars because of the sound quality.",
         "If it were possible to give them 0/10, they'd have it."
    )

    replace_rating(x)

    ##  [1] "This place receives best for their APPETIZERS!!!"                    
    ##  [2] " better for the food & the guy in the blue shirt for his great vibe!"
    ##  [3] " best for both the movie and trilogy."                               
    ##  [4] "* Both the Hot & Sour & the Egg Flower Soups were absolutely best !" 
    ##  [5] "For service, I give them terrible ."                                 
    ##  [6] "This place deserves terrible ."                                      
    ##  [7] " best stars."                                                        
    ##  [8] "My rating: just below average ."                                     
    ##  [9] "If there were terrible I would give it terrible ."                   
    ## [10] "Rating: extremely below average ."                                   
    ## [11] "I gave it best because of the sound quality."                        
    ## [12] "If it were possible to give them terrible , they'd have it."

### Ordinal Numbers

Again, some analysis requires numbers, including ordinal numbers, to be
converted to text form. `replace_ordinal` attempts to perform this task
for ordinal number 1-100 (i.e., 1st - 100th).

    x <- c(
        "I like the 1st one not the 22nd one.", 
        "For the 100th time stop those 3 things!",
        "I like the 3rd 1 not the 12th 1."
    )
    replace_ordinal(x)

    ## [1] "I like the  first  one not the  twenty second  one."
    ## [2] "For the  hundredth  time stop those 3 things!"      
    ## [3] "I like the  third  1 not the  twelfth  1."

    replace_ordinal(x, TRUE)

    ## [1] "I like the  first  one not the  twentysecond  one."
    ## [2] "For the  hundredth  time stop those 3 things!"     
    ## [3] "I like the  third  1 not the  twelfth  1."

    replace_ordinal(x, remove = TRUE)

    ## [1] "I like the    one not the    one."   
    ## [2] "For the    time stop those 3 things!"
    ## [3] "I like the    1 not the    1."

    replace_number(replace_ordinal(x))

    ## [1] "I like the  first  one not the  twenty second  one."
    ## [2] "For the  hundredth  time stop those three things!"  
    ## [3] "I like the  third  one not the  twelfth  one."

### Symbols

Text often contains short-hand representations of words/phrases. These
symbols may contain analyzable information but in the symbolic form they
cannot be parsed. The `replace_symbol` function attempts to replace the
symbols `c("$", "%", "#", "@", "& "w/")` with their word equivalents.

    x <- c("I am @ Jon's & Jim's w/ Marry", 
        "I owe $41 for food", 
        "two is 10% of a #"
    )
    replace_symbol(x)

    ## [1] "I am  at  Jon's  and  Jim's  with  Marry"
    ## [2] "I owe  dollar 41 for food"               
    ## [3] "two is 10 percent  of a  number "

### White Space

Regex white space characters (e.g., `\n`, `\t`, `\r`) matched by `\s`
may impede analysis. These can be replaced with a single space `" "` via
the `replace_white` function.

    x <- "I go \r
        to   the \tnext line"
    x

    ## [1] "I go \r\n    to   the \tnext line"

    cat(x)

    ## I go 
    ##     to   the     next line

    replace_white(x)

    ## [1] "I go to the next line"

### Word Elongation

In informal writing people may use a form of text embellishment to
emphasize or alter word meanings called elongation (a.k.a. "word
lengthening"). For example, the use of "Whyyyyy" conveys frustration.
Other times the usage may be to be more sexy (e.g., "Heyyyy there").
Other times it may be used for emphasis (e.g., "This is so gooood").

The `replace_word_elongation` function replaces these un-normalized
forms with the most likely normalized form. The `impart.meaning`
argument can replace a short list of known elongations with semantic
replacements.

    x <- c('look', 'noooooo!', 'real coooool!', "it's sooo goooood", 'fsdfds',
        'fdddf', 'as', "aaaahahahahaha", "aabbccxccbbaa", 'I said heyyy!',
        "I'm liiiike whyyyyy me?", "Wwwhhatttt!", NA)

    replace_word_elongation(x)

    ##  [1] "look"             "no!"              "real cool!"      
    ##  [4] "it's so good"     "fsdfds"           "fdf"             
    ##  [7] "as"               "ahahahahaha"      "aabbccxccbbaa"   
    ## [10] "I said hey!"      "I'm like why me?" "what!"           
    ## [13] NA

    replace_word_elongation(x, impart.meaning = TRUE)

    ##  [1] "look"                     "sarcastic!"              
    ##  [3] "real cool!"               "it's so good"            
    ##  [5] "fsdfds"                   "fdf"                     
    ##  [7] "as"                       "ahahahahaha"             
    ##  [9] "aabbccxccbbaa"            "I said hey sexy!"        
    ## [11] "I'm like frustration me?" "what!"                   
    ## [13] NA

### Tokens

Often an analysis requires converting tokens of a certain type into a
common form or removing them entirely. The `mgsub` function can do this
task, however it is regex based and time consuming when the number of
tokens to replace is large. For example, one may want to replace all
proper nouns that are first names with the word name. The
`replace_token` provides a fast way to replace a group of tokens with a
single replacement.

This example shows a use case for `replace_token`:

    ## Set Up the Tokens to Replace
    nms <- gsub("(^.)(.*)", "\\U\\1\\L\\2", lexicon::common_names, perl = TRUE)
    head(nms)

    ## [1] "Mary"      "Patricia"  "Linda"     "Barbara"   "Elizabeth" "Jennifer"

    ## Set Up the Data
    x <- textshape::split_portion(sample(c(sample(lexicon::grady_augmented, 20000), 
        sample(nms, 10000, TRUE))), n.words = 12)
    x$text.var <- paste0(x$text.var, sample(c('.', '!', '?'), length(x$text.var), TRUE))
    head(x$text.var)

    ## [1] "incidentals Alycia undertaxed like proclivity sensibles bradley Maria envy Forrest triazin stiffens?"           
    ## [2] "Carissa assists Gina bemingle Miles Colene educe Cortez Melita realisers congruence Bethel!"                    
    ## [3] "hisses bred voyageurs stabler hadleigh tapers Princess paucities junketer aversion Maryann oncologist."         
    ## [4] "Syreeta rehung tediously Anita hoers amplifying unlives mammeys Myrtice Blanche Trisha Cortez?"                 
    ## [5] "Susana kaliph downhill jubilee clearness sieved superintend Garret flops shiftlessness confers quarrier."       
    ## [6] "Mellissa contraindicated Michell Gracia joshed inactivating Willy saltbush oiliest tubules circulatory Glennie."

    head(replace_tokens(x$text.var, nms, 'NAME'))

    ## [1] "incidentals NAME undertaxed like proclivity sensibles bradley NAME envy NAME triazin stiffens?"      
    ## [2] "NAME assists NAME bemingle NAME NAME educe NAME NAME realisers congruence NAME!"                     
    ## [3] "hisses bred voyageurs stabler hadleigh tapers NAME paucities junketer aversion NAME oncologist."     
    ## [4] "NAME rehung tediously NAME hoers amplifying unlives mammeys NAME NAME NAME NAME?"                    
    ## [5] "NAME kaliph downhill jubilee clearness sieved superintend NAME flops shiftlessness confers quarrier."
    ## [6] "NAME contraindicated NAME NAME joshed inactivating NAME saltbush oiliest tubules circulatory NAME."

This demonstration shows how fast token replacement can be with
`replace_token`:

    ## mgsub
    tic <- Sys.time()
    head(mgsub(x$text.var, nms, "NAME"))

    ## [1] "incidentals NAME undertaxed like proclivity sensibles bradley NAME envy NAME triazin stiffens?"      
    ## [2] "NAME assists NAME bemingle NAME NAME educe NAME NAME realisers congruence NAME!"                     
    ## [3] "hisses bred voyageurs stabler hadleigh tapers NAME paucities junketer aversion NAME oncologist."     
    ## [4] "NAME rehung tediously NAME hoers amplifying unlives mammeys NAME NAME NAME NAME?"                    
    ## [5] "NAME kaliph downhill jubilee clearness sieved superintend NAME flops shiftlessness confers quarrier."
    ## [6] "NAME contraindicated NAME NAME joshed inactivating NAME saltbush oiliest tubules circulatory NAME."

    (toc <- Sys.time() - tic)

    ## Time difference of 7.30424 secs

    ## replace_tokens
    tic <- Sys.time()
    head(replace_tokens(x$text.var, nms, "NAME"))

    ## [1] "incidentals NAME undertaxed like proclivity sensibles bradley NAME envy NAME triazin stiffens?"      
    ## [2] "NAME assists NAME bemingle NAME NAME educe NAME NAME realisers congruence NAME!"                     
    ## [3] "hisses bred voyageurs stabler hadleigh tapers NAME paucities junketer aversion NAME oncologist."     
    ## [4] "NAME rehung tediously NAME hoers amplifying unlives mammeys NAME NAME NAME NAME?"                    
    ## [5] "NAME kaliph downhill jubilee clearness sieved superintend NAME flops shiftlessness confers quarrier."
    ## [6] "NAME contraindicated NAME NAME joshed inactivating NAME saltbush oiliest tubules circulatory NAME."

    (toc <- Sys.time() - tic)

    ## Time difference of 0.0790689 secs

Now let's amp it up with 20x more text data. That's 50,000 rows of text
(600,120 words) and 5,493 replacement tokens in 1.7 seconds.

    tic <- Sys.time()
    out <- replace_tokens(rep(x$text.var, 20), nms, "NAME")
    (toc <- Sys.time() - tic)

    ## Time difference of 1.721217 secs