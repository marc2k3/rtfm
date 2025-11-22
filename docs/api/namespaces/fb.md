# fb

**Properties**

|||||
|---|---|---|---|
|fb.AlwaysOnTop|`boolean`|read, write|
|fb.ComponentPath|`string`|read|
|fb.FoobarPath|`string`|read|
|fb.ProfilePath|`string`|read|
|fb.VersionString|`string`|read|

!!! example
	```js
	fb.AlwaysOnTop = !fb.AlwaysOnTop; // toggles the current value
	console.log(fb.FoobarPath); // Z:\foobar2000\
	```

**Methods**
## `fb.AddDirectory()`
Shortcut to main menu command.

No return value.

## `fb.AddFiles()`
Shortcut to main menu command.

No return value.

## `fb.AddLocationsAsync(window_id, paths)`
|Arguments|||
|---|---|---|
|window_id|[window.ID](window.md)|
|paths|`array`|An array of strings which could be files, urls, playlists.|

Returns a unique `task_id`.

Similar to [plman.AddLocations](plman.md#plmanaddlocationsplaylistindex-paths-select) except rather than specifiying a target playlist, you get a handle list generated
from the supplied paths/urls which are sent to a new [on_locations_added](../callbacks/component.md#on_locations_addedtask_id-handle_list) callback.

!!! example
	```js
	var files = ["z:\\1.mp3", "z:\\2.flac"];

	function on_mouse_lbtn_dblclk() {
		var task_id = fb.AddLocationsAsync(window.ID, files);
		console.log("got task_id", task_id);
	}

	function on_locations_added(task_id, handle_list) {
		console.log("callback task_id", task_id);
		console.log(handle_list.Count);
	}
	```

## `fb.CheckClipboardContents()`
Returns a `boolean` value.

Checks clipboard contents are handles or a file selection
from `Windows Explorer`. Use in conjunction	with
[fb.GetClipboardContents](#fbgetclipboardcontents).

## `fb.CheckComponent(name)`
|Arguments|||
|---|---|---|
|name|`string`|

Returns a `boolean` value.

Use this if your script depends on other components.

!!! example
	```js
	if (!fb.CheckComponent("foo_playcount")) {
		utils.ShowPopupMessage("This script requires foo_playcount.", "Rating");
	}
	```

## `fb.ClearPlaylist()`
No return value.

Clears active playlist. If you wish to clear a specific playlist, use [plman.ClearPlaylist](plman.md#plmanclearplaylistplaylistindex).

## `fb.CreateContextMenuManager()`
Returns an [IContextMenuManager](../interfaces/IContextMenuManager.md) instance.

## `fb.CreateHandleList([handle])`
|Arguments|||
|---|---|---|
|handle|[IMetadbHandle](../interfaces/IMetadbHandle.md), optional|

Returns an [IMetadbHandleList](../interfaces/IMetadbHandleList.md) instance.

!!! example
	```js
	var handle = fb.GetFocusItem();
	var handle_list = fb.CreateHandleList(handle);
	var image_path = ...
	handle_list.AttachImage(image_path, 0);
	handle_list.Dispose();
	```

## `fb.CreateMainMenuManager(root_name)`
|Arguments|||
|---|---|---|
|root_name|`string`|Must be one of `File`, `Edit`, `View`, `Playback`, `Library`, `Help`.

Returns an [IMainMenuManager](../interfaces/IMainMenuManager.md) instance.

## `fb.EnableAdvancedLogging()`
No return value.

Only enable this if you're having problems diagnosing your own script errors. The setting persists
until `foobar2000` is closed. To disable this advanced logging, remove this method and restart
`foobar2000`.

Console messages will point directly at the `C++` source code and this is something that you can
ask about in the [main support thread](https://hydrogenaud.io/index.php/topic,110499.0.html).

## `fb.EnumerateMainMenuCommands()`
Returns a `JSON` array in string form so you need to use `JSON.parse` on the result.

Every item of the array has the following properties:
```
Checked // boolean
Disabled // boolean
FullPath // string, the same full path you'd supply to fb.RunMainMenuCommand
HiddenByDefault // boolean
Radio // boolean
Type // string "Fixed" or "Dynamic"
Visible // boolean
```

!!! example

	```js
	var menu_commands = JSON.parse(fb.EnumerateMainMenuCommands());

	// list all checked commands in the Console
	menu_commands.filter(function (command) {
		return command.Checked;
	}).forEach(function (command) {
		console.log(command.FullPath);
	});
	```

## `fb.Exit()`
Shortcut to main menu command.

No return value.

## `fb.GetAlbumArtStub([art_id])`
|Arguments|||
|---|---|---|
|art_id|[AlbumArtId](../flags.md#albumartid)|Default `0`.|

Returns an [IJSImage](../interfaces/IJSImage.md) instance or `null` on failure.

## `fb.GetAudioChunk(requested_length[, offset])`
|Arguments|||
|---|---|---|
|requested_length|`number`|seconds|
|offset|`number`|Default `0`|

Returns an [IAudioChunk](../interfaces/IAudioChunk.md) instance or `null` on failure.

`get_absolute_time` and `get_chunk_absolute` and their arguments are described here:

[https://github.com/marc2k3/foobar2000-sdk/blob/main/foobar2000/SDK/vis.h](https://github.com/marc2k3/foobar2000-sdk/blob/main/foobar2000/SDK/vis.h)


## `fb.GetClipboardContents()`
Returns an [IMetadbHandleList](../interfaces/IMetadbHandleList.md) instance.

Clipboard contents can be handles copied to the clipboard in
other components, a file selection from Explorer, etc.

!!! example
	```js
	// ==PREPROCESSOR==
	// @import "%fb2k_component_path%helpers.txt"
	// ==/PREPROCESSOR==

	function on_mouse_rbtn_up(x, y) {
		var ap = plman.ActivePlaylist;

		// playlist_can_add_items is defined in helpers.txt, it uses
		// plman.GetPlaylistLockFilterMask to determine if the active playlist
		// permits adding items
		// MF_STRING and MF_GRAYED are also defined there.

		var can_paste_flag = playlist_can_add_items(ap) && fb.CheckClipboardContents() ? MF_STRING : MF_GRAYED;

		var menu = window.CreatePopupMenu();
		menu.AppendMenuItem(can_paste_flag, 1, "Paste");

		var idx = menu.TrackPopupMenu(x, y);
		menu.Dispose();

		if (idx == 1) {
			var handle_list = fb.GetClipboardContents();
			plman.InsertPlaylistItems(ap, plman.GetPlaylistItemCount(ap), handle_list);
			handle_list.Dispose();
		}

		return true;
	}
	```

## `fb.GetFocusItem()`
Returns an [IMetadbHandle](../interfaces/IMetadbHandle.md) instance.

Handle of the currently selected active playlist item or `null` on failure.

## `fb.GetLibraryItems([query])`
|Arguments|||
|---|---|---|
|query|`string`|Optional. If omitted or invalid, all items will be returned.|

Returns an [IMetadbHandleList](../interfaces/IMetadbHandleList.md) instance.

## `fb.GetSelection([flags])`
|Arguments|||
|---|---|---|
|flags|`number`|Default `0`, `1` no now playing|

Returns an [IMetadbHandleList](../interfaces/IMetadbHandleList.md) instance.

## `fb.GetSelectionType()`
Returns a [SelectionType](../flags.md#selectiontype)

## `fb.IsLibraryEnabled()`
Returns a `boolean` value.

## `fb.IsLibraryInitialised()`
Returns a `boolean` value.

## `fb.LoadPlaylist()`
Shortcut to main menu command.

No return value.

## `fb.RunContextCommand(command)`
|Arguments|||
|---|---|---|
|command|`string`|The full path to the command must be supplied. Case is not important.|

Returns `true` if a matching command was found, `false` otherwise.

!!! note
	This method is for the currently playing file only. See also: [IMetadbHandleList RunContextCommand](../interfaces/IMetadbHandleList.md#runcontextcommandcommand).

## `fb.RunMainMenuCommand(command)`
|Arguments|||
|---|---|---|
|command|`string`|The full path to the command must be supplied. Case is not important.|

Returns `true` if a matching command was found, `false` otherwise.

## `fb.SavePlaylist()`
Shortcut to main menu command.

No return value.

## `fb.ShowConsole()`
Shortcut to main menu command.

No return value.

## `fb.ShowLibrarySearchUI(query)`
|Arguments|||
|---|---|---|
|query|`string`|

No return value.

Opens the `Library>Search` window populated with the query you set.

## `fb.ShowPictureViewer(path)`
|Arguments|||
|---|---|---|
|path|`string`|

No return value.

## `fb.ShowPreferences()`
Shortcut to main menu command.

No return value.

## `fb.TitleFormat(pattern)`
|Arguments|||
|---|---|---|
|pattern|`string`|

Returns an [ITitleFormat](../interfaces/ITitleFormat.md) instance.
