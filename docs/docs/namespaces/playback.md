**Properties**

|||||
|---|---|---|---|
|playback.CursorFollowPlayback|`boolean`|read, write|
|playback.CustomVolume|`number`|read|See note below.
|playback.IsPaused|`boolean`|read|
|playback.IsPlaying|`boolean`|read|
|playback.Length|`number`|read|
|playback.Order|[PlaybackOrder](../flags.md#playbackorder)|read,write|
|playback.PlaybackFollowCursor|`boolean`|read, write|
|playback.ReplaygainMode|[ReplaygainMode](../flags.md#replaygainmode)|read, write|
|playback.StopAfterCurrent|`boolean`|read, write|
|playback.Time|`number`|read, write|
|playback.Volume|`number`|read, write|See note below.

!!! note "Custom Volume"
	`playback.CustomVolume` can be used for displaying the volume from `UPnP` devices. It will return
	a value of `-1` when using a normal device and that also indicates that `playback.Volume` is writable.
	When a custom volume control is active, you can not use `playback.Volume` and must use `playback.VolumeUp()` / `playback.VolumeDown()` / `playback.VolumeMute()`.

**Methods**
## `playback.GetActiveDSPs()`
Returns a `VBArray` so you need to use `.toArray()` on the result.

## `playback.GetDSPPresets()`
Returns a `JSON` array in string form so you need to use `JSON.parse` on the result.

!!! example
	```js
	var str = playback.GetDSPPresets();
	console.log(str);
	```

	``` markdown title="Example output"
	[
		{
			"Active": true,
			"Name": "two"
		},
		{
			"Active": false,
			"Name": "three"
		}
	]
	```

	```js
	var arr = JSON.parse(str);
	console.log(arr.length); // number of presets

	for (var i = 0; i < arr.length; i++) {
		if (arr[i].Active) {
			// this is the active preset, do something with the Name??
		}
	}
	```

## `playback.GetNowPlaying()`
Returns an [IMetadbHandle](../interfaces/IMetadbHandle.md) instance.
Now playing item or `null` if [foobar2000](https://www.foobar2000.org) isn't playing.

## `playback.GetOrderNames()`
Returns a `VBArray` so you need to use `.toArray()` on the result.

This is an array of playback order names which can be iterated
or used with `playback.Order`.

!!! example
	=== "Current"
		```js
		console.log(playback.GetOrderNames().toArray()[playback.Order]);
		```

	=== "Loop"
		```js
		var arr = playback.GetOrderNames().toArray();
		for (var i = 0; i < arr.length; i++) {
			console.log(arr[i]);
		}
		```

## `playback.GetOutputDevices()`
Returns a `JSON` array in string form so you need to use `JSON.parse` on the result.

!!! example
	```js
	var str = playback.GetOutputDevices();
	console.log(str);
	```

	``` markdown title="Example output"
	[
		{
			"Active": false,
			"DeviceID": "{5243F9AD-C84F-4723-8194-0788FC021BCC}",
			"Name": "Null Output",
			"OutputID": "{EEEB07DE-C2C8-44C2-985C-C85856D96DA1}"
		},
		{
			"Active": true,
			"DeviceID": "{00000000-0000-0000-0000-000000000000}",
			"Name": "Primary Sound Driver",
			"OutputID": "{D41D2423-FBB0-4635-B233-7054F79814AB}"
		},
		{
			"Active": false,
			"DeviceID": "{1C4EC038-97DB-48E7-9C9A-05FDED46847B}",
			"Name": "Speakers (Sound Blaster Z)",
			"OutputID": "{D41D2423-FBB0-4635-B233-7054F79814AB}"
		},
		{
			"Active": false,
			"DeviceID": "{41B86272-3D6C-4A5A-8907-4FE7EBE39E7E}",
			"Name": "SPDIF-Out (Sound Blaster Z)",
			"OutputID": "{D41D2423-FBB0-4635-B233-7054F79814AB}"
		},
		{
			"Active": false,
			"DeviceID": "{9CDC0FAE-2870-4AFA-8287-E86099D69076}",
			"Name": "3 - BenQ BL3200 (AMD High Definition Audio Device)",
			"OutputID": "{D41D2423-FBB0-4635-B233-7054F79814AB}"
		}
	]
	```

	```js
	var arr = JSON.parse(str);
	console.log(arr.length); // number of devices
	```

As you can see, only one of the items in the array has `Active`
set to `true` so that is the device you'd want to display the name of
or mark as selected in a menu.

To change device you can use [fb.RunMainMenuCommand](fb.md#fbrunmainmenucommandcommand) with the
device name or use [playback.SetOutputDevice](#playbacksetoutputdeviceoutputid-deviceid) with the
`DeviceID`/`OutputID`.

!!! example
	=== "RunMainMenuCommand"
		```js
		var str = playback.GetOutputDevices();
		var arr = JSON.parse(str);
		// Assuming same list from above, switch output to the last device.
		fb.RunMainMenuCommand("Playback/Device/" + arr[4].Name);
		```

	=== "SetOutputDevice"
		```js
		var str = playback.GetOutputDevices();
		var arr = JSON.parse(str);
		// Assuming same list from above, switch output to the last device.
		playback.SetOutputDevice(arr[4].OutputID, arr[4].DeviceID);
		```

## `playback.Next()`
Shortcut to main menu command.

No return value.

## `playback.Pause()`
Shortcut to main menu command.

No return value.

## `playback.Play()`
Shortcut to main menu command.

No return value.

## `playback.PlayOrPause()`
Shortcut to main menu command.

No return value.

## `playback.Previous()`
Shortcut to main menu command.

No return value.

## `playback.Random()`
Shortcut to main menu command.

No return value.

## `playback.SetDSPPreset(idx)`
|Arguments|||
|---|---|---|
|idx|`number`|

No return value. See [playback.GetDSPPresets](#playbackgetdsppresets).

## `playback.SetOutputDevice(OutputID, DeviceID)`
|Arguments|||
|---|---|---|
|OutputID|`string`|
|DeviceID|`string`|

No return value. See [playback.GetOutputDevices](#playbackgetoutputdevices).

## `playback.Stop()`
Shortcut to main menu command.

No return value.

## `playback.VolumeDown()`
Shortcut to main menu command.

No return value.

## `playback.VolumeMute()`
Shortcut to main menu command.

No return value.

## `playback.VolumeUp()`
Shortcut to main menu command.

No return value.
