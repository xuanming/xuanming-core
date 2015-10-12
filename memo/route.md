# Route

Maybe route is not a proper name for this.

Route will build the map from source to destination.

## Source

1.  Page from content directory. Using the 

# Route Examples

## One to one

    content
    |- page
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
       `- config.yml

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

User could set configuration in data to select which method to use for
resolving confliction.

## Book

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
    |- indice
    `- copyright.html

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
    |- indice
    `- copyright.html

## Blog
