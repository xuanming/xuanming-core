# Components

1.  Content
2.  Appearance
    1.  Theme. Could be directly from github, or a gem. Theme could have
        parameters and set in configuration.
3.  Plugin
    1.  Functionality
    2.  Appearance
    3.  Command


# General

*   There will be `/_config` and `/_sitemap` pages. The use of js and
    css for these pages should be similar with ordinary pages. These
    pages are ignored in the building by default.
*   How to know a page must be rebuilt? Compare the timestamp of all
    the related files (content source, layout, data, ...)
    *   middleman rebuild everything. It just compare the files between
        two builds. All actual building operations are executed.
*   Helper for getting the relative link of a specified page.
*   Data could have sub directories:

        data
        |- theme
        |  |- blog.yml
        |  |- book.yml
        |  `- bootstrap.yml
        |- disqus
        |  |- token.yml
        |  `- url.yml
        |- content.yml
        `- page.yml

    The data could be retrieved by data.theme.blog, data.disqus.url.
*   Theme only contains js and css, not layout. The frame will
    include the layout and some helpers. A frame may come with
    some predefined themes in it. Then a theme should depend on certain
    frame. 
*   Helpers should have scope. Some helpers could only be available in
    their own extension or some specific frames.
*   Extension types:
    1. Frame. Layout. Depend on helper.
    2. Theme. Js and css. Depend on frame.
    3. Helper.
    4. Command.
    5. Converter.
    6. Generator. Could be an interactive generator for a specific page.
