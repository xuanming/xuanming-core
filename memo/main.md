# Packages

1.  freeze
2.  freeze-cli
    1.  freeze new
    2.  freeze install, install required components
    3.  freeze server
    4.  freeze console
    5.  freeze generate, generate source files
    6.  freeze build
    6.  freeze show config/sitemap
    7.  freeze plugin, operation about available plugins
    8.  freeze subcmd
    9.  freeze help, this should be built-in feature for freeze command
3.  freeze-converter-tilt
4.  freeze-route-direct
5.  freeze-datasource-data
6.  freeze-datasource-direct
7.  freeze-datasource-helper
8.  freeze-theme-bootstrap
9.  freeze-book, include converter of toc, datasource of toc, some themes

# Components

1.  Content.
    1.  Pages.
    2.  Site data. Do not put configuration here, only data.
2.  Appearance
    1.  Frame. Layout and js. How to assemble the contents.
    2.  Theme. How to show the contents. Could be directly from github,
        or a gem. Theme could have parameters and set in configuration.
3.  Plugin
    1.  Functionality. Helper
    2.  Appearance
    3.  Command

# Components2

1.  Data source (page, data, REST)
    *   Common data. Global data
    *   Page specific data
2.  Data type
3.  Route
4.  Converter

# Components3

Data should be devided into:

1.  Source. Where to get the data, file system or internet
2.  Type. Markdown, yaml, erb
3.  Converter. Determined by type and source (file from cdn do not
    need to be converted)

Data sources:

1.  File system
2.  Internet. CDN, REST, external link

Data types:

1.  Page
    *   Markdown, slim, haml, erb
2.  Data
    *   Yaml, json
3.  Javascript
4.  CSS
5.  Image
6.  Layout
    *   erb, haml, slim
7.  Header
    *   erb, haml, slim
8.  Footer
    *   erb, haml, slim

Data source


# General

*   Integrate Ember.js. Ember is actually static pages. Try to make an
    ember.js frame. But the page route is different from traditional
    static pages. Some kind of pages should not be converted in the
    building process.
*   Provide the ability to generate a single page. This will be useful
    for a book, which could be directly converted to pdf.
*   Convert to html/json/xml/... Could provide static API.
*   There will be `/_config` and `/_sitemap` pages. The use of js and
    css for these pages should be similar with ordinary pages. These
    pages are ignored in the building by default.
*   How to know a page must be rebuilt? Compare the timestamp of all
    the related files (content source, layout, data, ...)
    *   middleman rebuild everything. It just compare the files between
        two builds. All actual building operations are executed.
*   Try to know whether the building of pages in middleman uses rack.
*   Deploy incrementally. Use something like git to do this. Check the
    built files between local and remote, and only transfer the
    difference. This should be an deployment extension. Capistrano may
    be able to do this.
*   Data could be dynamic. It could be from database or some web
    service. Then an incremental deployment will be very useful. The
    site can periodically be deployed in order to get a dynamic site.
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
*   For the book extension, make reader view in firefox available.
*   Theme only contains js and css, not layout. The frame will
    include the layout and some helpers. A frame may come with
    some predefined themes in it. So a theme should depend on certain
    frame. 
*   Helpers should have scope. Some helpers could only be available in
    their own extension or some specific frames.
*   Modules in extensions should have their own configuraion, which
    could be listed in the command.
*   Plugin types:
    1.  Frame. Route, converter, layout and js. Optional depends on
        helper. Ember.js is an example of frame.
    2.  Theme. Css and js. Depends on frame.
    3.  Helper.
    4.  Command.
    5.  Converter.
    6.  Generator. Could be an interactive generator for a specific
        page.
*   Commands should have default subcommand. Each action should be a
    command. Options should be description for the action.

        freeze server start
        freeze server             # default to freeze server start
        freeze                    # default to freeze server, and then default to freeze server start
        freeze plugin list-all
        freeze plugin list        # list all imported plugins

*   Command plugins.
    1.  freeze generate

*   The plugin for host all the available plugins. Provide the
    `freeze plugin list-all` command.
    Create a static site for keeping all the plugins' metadata.
    Could get all available plugins with API from this static site.
    Developers could send pull request to github and new plugin
    will be automatically added. This plugin will also decide the
    source of plugin, so only the plugin name is needed in the
    configuration.
*   Configuration comes from default, config file and command options,
    with the priority from low to high.
