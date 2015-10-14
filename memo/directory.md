# Directory structure

    |- config.yml
    |- content
    |  |- page
    |  |  |- index.html.erb
    |  |  `- pages
    |  |     |- page1.html.slim
    |  |     `- page2.html.haml
    |  |- image
    |  |  |- logo.png
    |  |  `- page1.jpg
    |  `- data
    |     |- content.yml
    |     `- page.yml
    |- frame
    |  |- layout
    |  |  `- layout.html.erb
    |  |- route
    |  |- converter
    |  `- js
    |     `- frame.js.coffeescript
    |- theme
    |  |- image
    |  |- font
    |  |- css
    |  |  `- all.css.scss
    |  `- js
    |     `- all.js.coffeescript
    |- lib
    |  `- some.rb                   # helpers
    |- plugin
    |  |- plugin1                   # helpers, theme
    |  `- plugin2
    `- build
