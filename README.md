alisond
==========


## Overview
alisond is a command line utility for controlling Google Chrome on OS X.
It is a native binary that uses the Scripting Bridge to communicate
with Chrome.

## Installation

#### Homebrew
    brew install alisond

#### Manual
- Save the 'alisond' binary to a location in your PATH (i.e. `/usr/local/bin/`)

##### Downloads
- [alisond-darwin-1.5.0-x64](https://drive.google.com/uc?id=0B3X9GlR6EmbnYThnLXQydFVIU3c)
- [canary-cli-darwin-1.5.0-x64](https://drive.google.com/uc?id=0B3X9GlR6EmbnTmZ2VmxRdmxRaFU)
- [chromium-cli-darwin-1.5.0-x64](https://drive.google.com/uc?id=0B3X9GlR6EmbnXy1BTF9fQ0ZVN00)

## Usage
    alisond -h  (Print help)
    alisond --help  (Print help)
    alisond help  (Print help)
    alisond list windows  (List all windows)
    alisond list tabs  (List all tabs)
    alisond list tabs -w <id>  (List tabs in specific window)
    alisond list links  (List all tabs' link)
    alisond list links -w <id>  (List tabs' link in specific window)
    alisond info  (Print info for active tab)
    alisond info -t <id>  (Print info for specific tab)
    alisond open <url>  (Open url in new tab)
    alisond open <url> -n  (Open url in new window)
    alisond open <url> -i  (Open url in new incognito window)
    alisond open <url> -t <id>  (Open url in specific tab)
    alisond open <url> -w <id>  (Open url in new tab in specific window)
    alisond close  (Close active tab)
    alisond close -w  (Close active window)
    alisond close -t <id>  (Close specific tab)
    alisond close -w <id>  (Close specific window)
    alisond reload  (Reload active tab)
    alisond reload -t <id>  (Reload specific tab)
    alisond back  (Navigate back in active tab)
    alisond back -t <id>  (Navigate back in specific tab)
    alisond forward  (Navigate forward in active tab)
    alisond forward -t <id>  (Navigate forward in specific tab)
    alisond activate -t <id>  (Activate specific tab)
    alisond presentation  (Enter presentation mode with the active tab)
    alisond presentation -t <id>  (Enter presentation mode with a specific tab)
    alisond presentation exit  (Exit presentation mode)
    alisond size  (Print size of active window)
    alisond size -w <id>  (Print size of specific window)
    alisond size <width> <height>  (Set size of active window)
    alisond size <width> <height> -w <id>  (Set size of specific window)
    alisond position  (Print position of active window)
    alisond position -w <id>  (Print position of specific window)
    alisond position <x> <y>  (Set position of active window)
    alisond position <x> <y> -w <id>  (Set position of specific window)
    alisond source  (Print source from active tab)
    alisond source -t <id>  (Print source from specific tab)
    alisond execute <javascript>  (Execute javascript in active tab)
    alisond execute <javascript> -t <id>  (Execute javascript in specific tab)
    alisond chrome version  (Print Chrome version)
    alisond version  (Print application version)


## Examples
###### List tabs
    $ alisond list tabs
    [57] Inbox (1) - foo.bar@gmail.com - Gmail
    [2147] My Drive - Google Drive
    [2151] GitHub
    [2161]
    [2155] Hacker News

###### Print tab info
    $ alisond info -t 2161
    Id: 2162
    Title:
    Url: http://httpbin.org/ip
    Loading: No

###### Print tab source
    $ alisond source -t 2161
    <html><head></head><body><pre style="word-wrap: break-word; white-space: pre-wrap;">{
      "origin": "1.2.3.4"
    }</pre></body></html>

###### Extract information from page
    $ alisond execute '(function() { var nodes = document.querySelectorAll(".title a"); var titles = []; for (var i = 0; i < 5; i++) { titles.push(nodes[i].innerHTML) } return titles.join("\n"); })();' -t 2155
    High-Speed Trading Isn't About Efficiency—It's About Cheating
    The terrifying surveillance case of Brandon Mayfield
    Google turns on "Download Gmail Archive" feature
    Learning to Code vs Learning Computer Science
    Show HN: Crushify.org
