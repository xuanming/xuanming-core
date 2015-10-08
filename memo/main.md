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
