# Component

## `on_download_file_done(path, success, error_text)`
|Arguments|||
|---|---|---|
|path|`string`|The path that was originally supplied to [utils.DownloadFileAsync](../namespaces/utils.md#utilsdownloadfileasyncurl-path-verify_image).|
|success|`boolean`|If `true` it means the web request was succesful and the file was saved correctly.|
|error_text|`string`|Empty if success is `true`. If success is `false`, it should describe what went wrong.|

Called when thread created by [utils.DownloadFileAsync](../namespaces/utils.md#utilsdownloadfileasyncurl-path-verify_image) is done.

## `on_get_album_art_done(handle, art_id, image)`
|Arguments|||
|---|---|---|
|handle|[JsMetadbHandle](../interfaces/JsMetadbHandle.md)|
|art_id|`number`|
|image|[JsImage](../interfaces/JsImage.md)|Could be `null` on failure.|

Called when thread created by [JsMetadbHandle GetAlbumArtAsync](../interfaces/JsMetadbHandle.md#getalbumartasyncart_id) or [JsMetadbHandle GetAlbumArtThumbAsync](../interfaces/JsMetadbHandle.md#getalbumartthumbasyncart_id-max_size) is done.

## `on_http_request_done(task_id, success, response_text, status, response_headers)`
|Arguments|||
|---|---|---|
|task_id|`number`|The return value from the original [utils.HTTPRequestAsync](../namespaces/utils.md#utilshttprequestasynctype-url-user_agent_or_headers-body) call.|
|success|`boolean`|If `true`, it doesn't necessarily mean `HTTP` status `200` but it indicates the request was completed succesfully so the `response text` is from the server.|
|response_text|`string`|
|status|`number`|Will be `0` if the server was unreachable otherwise it should be the `HTTP` status code.|
|response_headers|`string`|This is a stringified `JSON` object so you need to use `JSON.parse` to access it. It's only valid if `success` was `true`.|

Called when thread created by [utils.HTTPRequestAsync](../namespaces/utils.md#utilshttprequestasynctype-url-user_agent_or_headers-body) is done.

See [Web Requests](../../guides/web-requests.md) for examples.

## `on_locations_added(task_id, handle_list)`
|Arguments|||
|---|---|---|
|task_id|`number`|The return value from the original [fb.AddLocationsAsync](../namespaces/fb.md#fbaddlocationsasyncpaths) call.|
|handle_list|[JsMetadbHandleList](../interfaces/JsMetadbHandleList.md)|

Called when thread created by [fb.AddLocationsAsync](../namespaces/fb.md#fbaddlocationsasyncpaths) is done.

## `on_main_menu(index)`
|Arguments|||
|---|---|---|
|index|`number`|

On the main menu `File>JavaScript Panel`, there are 10 menu items and
whichever number is selected is sent as the `index` to this callback.

Being main menu items now means you can bind them to global keyboard
shortcuts, standard toolbar buttons, etc.

Remember to think carefully about where you use this code as you
probably only want it to run once so don't include it in common files
and scripts where you might have multiple instances. Also, you should
avoid sharing scripts containing this code so as not to conflict with
what other users may already be using.

!!! example
	```js
	function on_main_menu(index) {
		switch (index) {
		case 1: // triggered when File>JavaScript Panel>1 is run
			do_something();
			break;
		case 2: // triggered when File>JavaScript Panel>2 is run
			do_something_else();
			break;
		}
	}
	```

## `on_notify_data(name, info)`
|Arguments|||
|---|---|---|
|name|`string`|
|info|`string`, `number`, `array`, `object`|

Called in other panels after [window.NotifyOthers](../namespaces/window.md#windownotifyothersname-info) is executed.

## `on_script_unload()`
Should always be called when:

 * scripts are reloaded from the context menu / `window.Reload`
 * the OK/Apply buttons are used in the [Configuration Window](../../configuration-window.md).
 * panels are removed/replaced in layout editing mode
 * [foobar2000](https://www.foobar2000.org) exits normally

It will not be called if a script throws an error or [foobar2000](https://www.foobar2000.org) terminates abnormally.

!!! note
	You do not need to clear timers or deactivate tooltips here. The component handles this automatically.

!!! note
	Do not try to use `window.SetProperty` here. When shutting down, the layout data which stores persistent
	properties has already been written to file and changes will not be saved.
