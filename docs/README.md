# DilanScript 2
A super easy-to-use file formatting guide with parser.

## About DilanScript
Imagine including your first name in the name of a piece of software. Couldn't be me.

DilanScript is an easy-to-use file formatting system. It's basically a config file with formatting that's easy to edit along with an API to read it that's super easy to use. This documentation basically has everything you need. DilanScript 2 is severely limited in functionality *for now*. I literally made this in like less than an hour for personal use but I thought I might as well publish it for my friends or anyone on the internet to use. I definitely plan on adding more functionality as necessary. 

## The File
It's kinda a mix of YAML and JSON (it's worse, but probably a bit easier to get started with), but if you don't know what either of those are, it doesn't really matter. For now, it supports multiline blocks, sections that can contain other sections, with a basic key-and-value data storage system. For applications of mine like the [DMSLauncher](https://blockhead7360.com/dmslauncher), I have one of these DilanScript files on a web server so I can add users and enable and disable things in the app, which uses the DilanScript API to read it. Learn how to format one with the [File Formatting Guide Documentation](FileFormattingGuide.md).

TL;DR: It's an easy-to-use config file for your software :)

## The API
The API can read both local files and files on a URL. Currently only runs in Java but more language support will be added soon (probably). Learn how to use the basic API with the [API Documentation](API.md).

## Download API
Check out the [releases](https://github.com/Blockhead7360/dilanscript/releases) for the latest version.

## Credits
Dilan (https://blockhead7360.com).
