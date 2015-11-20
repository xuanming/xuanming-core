# Route

Maybe route is not a proper name for this.

Route will build the map from source to destination.

## Source

1.  Page from content directory. Using the 

# Route Examples

## One to one with layout

    content
    `- page
      |- index.html
      |- about.html
      |- detail
      |  |- index.html
      |  |- location.html
      |  `- color.html
      `- news
         |- day.html
         `- week.html

## Pretty URLs with Directory indexes

    content
    |- page
    |  |- index.html
    |  |- about.html
    |  |- detail.html
    |  |- detail
    |  |  |- index.html
    |  |  |- location.html
    |  |  `- color.html
    |  |- news.html
    |  `- news
    |     |- day.html
    |     `- week.html
    `- data
       `- data.yml

Converted to:

    build
    |- index.html             # index.html is reserved
    |- about
    |  `- index.html
    |- detail
    |  |- index.html
    |  |- index               # this index.html has confliction, so it is also converted
    |  |  `- index.html
    |  |- location
    |  |  `- index.html
    |  `- color
    |     `- index.html
    `- news
       |- index.html
       |- day
       |  `- index.html
       `- week
          `- index.html

Another way to resolve confliction:

    build
    |- index.html             # index.html is reserved
    |- about
    |  `- index.html
    |- detail.html
    |- detail
    |  |- index.html          # this is another way to resolve confliction
    |  |- location
    |  |  `- index.html
    |  `- color
    |     `- index.html
    `- news
       |- index.html
       |- day
       |  `- index.html
       `- week
          `- index.html

User could set configuration to select which method to use for resolving
confliction.

## Book

    content
    |- page
    |  |- preface.md
    |  |- chapter1.md
    |  |- chapter2
    |  |  |- index.md
    |  |  |- section1.md
    |  |  `- section2.md
    |  |- chapter3.md
    |  |- chapter3
    |  |  |- section1.md
    |  |  `- section2.md
    |  |- Appendix1.md
    |  |- Appendix2.md
    |  `- copyright.md
    `- data
       |- toc.yml
       `- data.yml

Or just put the toc with the pages:

    content
    |- page
    |  |- toc.yml
    |  |- preface.md
    |  |- chapter1.md
    |  |- chapter2
    |  |  |- toc.yml
    |  |  |- index.md
    |  |  |- section1.md
    |  |  `- section2.md
    |  |- chapter3.md
    |  |- chapter3
    |  |  |- toc.yml
    |  |  |- section1.md
    |  |  `- section2.md
    |  |- Appendix1.md
    |  |- Appendix2.md
    |  `- copyright.md
    `- data
       `- data.yml

    build
    |- cover.html
    |- preface.html
    |- toc.html
    |- chapter1.html
    |- chapter2
    |  |- index.html
    |  |- section1.html
    |  `- section2.html
    |- chapter3.html
    |- chapter3
    |  |- section1.html
    |  `- section2.html
    |- index.html
    `- copyright.html

## Blog

    content
    |- page
    |  |- 2015-10-24-blog1.md
    |  |- 2015-10-24-blog2.md
    |  |- 2015-10-18-blog3.md
    |  `- 2014-12-03-blog4.md
    `- data
       `- data.yml

    build
    |- index.html
    |- list.html
    |- tag.html
    `- blog
       |- 2015
       |  `- 10
       |     |- 24
       |     |  |- blog1.html
       |     |  `- blog2.html
       |     `- 18
       |        `- blog3.html
       `- 2014
          `- 12
             `- 03
                `- blog4.html
