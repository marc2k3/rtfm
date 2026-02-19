# Overview

This component for [foobar2000](https://www.foobar2000.org) is based on `JScript Panel 3` and `Spider Monkey Panel`.

It allows the creation of customisable panels that can be written with
`JavaScript` rather than the `C++` required by the [foobar2000 SDK](https://www.foobar2000.org/SDK).

Under the hood, it uses the `Spider Monkey` engine (102.10esr) taken from `Spider Monkey Panel`
but all graphics rendering is `Direct2D` taken from `JScript Panel 3`. Also, all API
design choices are my own from `JScript Panel 3`. Everything I hated about `Spider Monkey Panel`
like the package manager and html dialog have been removed. Also, there is zero `ActiveX`
support. That nonsense needs to die.

Here are just some of the features provided by the component...

* Custom drawing of text, external images, lines, rectangles, etc.
* Use fonts/colours from the main preferences of whichever user interface you are using.
* Executing main/context menu commands.
* Ability to create custom buttons/menus.
* Capture keystrokes/mouse movement/clicks.
* [Callbacks](api/callbacks/index.md) can be used to trigger code based on various `foobar2000`, `Windows` and `Component` events.
* Read/[write](api/interfaces/IMetadbHandleList.md#updatefileinfofromjsonstr) file tags.
* Complete manipulation of playlists.
* Media Library display/sorting/filtering
* [Save settings](api/namespaces/window.md#windowgetpropertyname-default_value) on a per panel basis. These persist between restarts
and are stored inside the layout configuration file for whichever UI your are using. You can also write your own functions to
load/save settings from `JSON` or plain text files.
* [Built in support](api/namespaces/utils.md#utilshttprequestasynctype-url-user_agent_or_headers-body) for
making `GET / POST` requests which return plain text and there is also a method for downloading binary files.
* There are many built in methods for working with the local filesystem, launching external applications etc.
* And much more...
