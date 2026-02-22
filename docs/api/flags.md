All of these are provided in `helpers.txt` bundled with the component. You
can include it for use in any script like this.

```
include(fb.ComponentPath + 'helpers.txt');
```

## DWRITE_FONT_WEIGHT
```js
const DWRITE_FONT_WEIGHT_THIN = 100;
const DWRITE_FONT_WEIGHT_EXTRA_LIGHT = 200;
const DWRITE_FONT_WEIGHT_ULTRA_LIGHT = 200;
const DWRITE_FONT_WEIGHT_LIGHT = 300;
const DWRITE_FONT_WEIGHT_SEMI_LIGHT = 350;
const DWRITE_FONT_WEIGHT_NORMAL = 400;
const DWRITE_FONT_WEIGHT_REGULAR = 400;
const DWRITE_FONT_WEIGHT_MEDIUM = 500;
const DWRITE_FONT_WEIGHT_DEMI_BOLD = 600;
const DWRITE_FONT_WEIGHT_SEMI_BOLD = 600;
const DWRITE_FONT_WEIGHT_BOLD = 700;
const DWRITE_FONT_WEIGHT_EXTRA_BOLD = 800;
const DWRITE_FONT_WEIGHT_ULTRA_BOLD = 800;
const DWRITE_FONT_WEIGHT_BLACK = 900;
const DWRITE_FONT_WEIGHT_HEAVY = 900;
const DWRITE_FONT_WEIGHT_EXTRA_BLACK = 950;
const DWRITE_FONT_WEIGHT_ULTRA_BLACK = 950;
```

## DWRITE_FONT_STYLE
```js
const DWRITE_FONT_STYLE_NORMAL = 0;
const DWRITE_FONT_STYLE_OBLIQUE = 1;
const DWRITE_FONT_STYLE_ITALIC = 2;
```

## DWRITE_FONT_STRETCH
```js
const DWRITE_FONT_STRETCH_ULTRA_CONDENSED = 1;
const DWRITE_FONT_STRETCH_EXTRA_CONDENSED = 2;
const DWRITE_FONT_STRETCH_CONDENSED = 3;
const DWRITE_FONT_STRETCH_SEMI_CONDENSED = 4;
const DWRITE_FONT_STRETCH_NORMAL = 5;
const DWRITE_FONT_STRETCH_MEDIUM = 5;
const DWRITE_FONT_STRETCH_SEMI_EXPANDED = 6;
const DWRITE_FONT_STRETCH_EXPANDED = 7;
const DWRITE_FONT_STRETCH_EXTRA_EXPANDED = 8;
const DWRITE_FONT_STRETCH_ULTRA_EXPANDED = 9;
```

## DWRITE_TEXT_ALIGNMENT
```js
const DWRITE_TEXT_ALIGNMENT_LEADING = 0;
const DWRITE_TEXT_ALIGNMENT_TRAILING = 1;
const DWRITE_TEXT_ALIGNMENT_CENTER = 2;
const DWRITE_TEXT_ALIGNMENT_JUSTIFIED = 3;
```

## DWRITE_PARAGRAPH_ALIGNMENT
```js
const DWRITE_PARAGRAPH_ALIGNMENT_NEAR = 0;
const DWRITE_PARAGRAPH_ALIGNMENT_FAR = 1;
const DWRITE_PARAGRAPH_ALIGNMENT_CENTER = 2;
```

## DWRITE_WORD_WRAPPING
```js
const DWRITE_WORD_WRAPPING_WRAP = 0;
const DWRITE_WORD_WRAPPING_NO_WRAP = 1;
const DWRITE_WORD_WRAPPING_EMERGENCY_BREAK = 2;
const DWRITE_WORD_WRAPPING_WHOLE_WORD = 3;
const DWRITE_WORD_WRAPPING_CHARACTER = 4;
```

## DWRITE_TRIMMING_GRANULARITY
```js
const DWRITE_TRIMMING_GRANULARITY_NONE = 0;
const DWRITE_TRIMMING_GRANULARITY_CHARACTER = 1;
const DWRITE_TRIMMING_GRANULARITY_WORD = 2;
```

## WICBitmapTransform
```js
const WICBitmapTransformRotate0 = 0;
const WICBitmapTransformRotate90 = 1;
const WICBitmapTransformRotate180 = 2;
const WICBitmapTransformRotate270 = 3;
const WICBitmapTransformFlipHorizontal = 8;
const WICBitmapTransformFlipVertical = 16;
```

## MessageBox Buttons
```js
const MB_OK = 0;
const MB_OKCANCEL = 1;
const MB_ABORTRETRYIGNORE = 2;
const MB_YESNOCANCEL = 3;
const MB_YESNO = 4;
```

## MessageBox Icons
```js
const MB_ICONHAND = 16;
const MB_ICONQUESTION = 32;
const MB_ICONEXCLAMATION = 48;
const MB_ICONASTERISK = 64;
```

## MessageBox Return Values
```js
const IDOK = 1;
const IDCANCEL = 2;
const IDABORT = 3;
const IDRETRY = 4;
const IDIGNORE = 5;
const IDYES = 6;
const IDNO = 7;
```

## AppendMenuItem Flags
```js
const MF_SEPARATOR = 0x00000800;
const MF_ENABLED = 0x00000000;
const MF_GRAYED = 0x00000001;
const MF_DISABLED = 0x00000002;
const MF_UNCHECKED = 0x00000000;
const MF_CHECKED = 0x00000008;
const MF_STRING = 0x00000000;
const MF_MENUBARBREAK = 0x00000020;
const MF_MENUBREAK = 0x00000040;
// const MF_BITMAP; // do not use
// const MF_OWNERDRAW // do not use
// const MF_POPUP // do not use
```

[https://docs.microsoft.com/en-gb/windows/win32/api/winuser/nf-winuser-appendmenua](https://docs.microsoft.com/en-gb/windows/win32/api/winuser/nf-winuser-appendmenua)

## TrackPopupMenu Flags
```js
const TPM_LEFTALIGN = 0x0000;
const TPM_CENTERALIGN = 0x0004;
const TPM_RIGHTALIGN = 0x0008;
const TPM_TOPALIGN = 0x0000;
const TPM_VCENTERALIGN = 0x0010;
const TPM_BOTTOMALIGN = 0x0020;
const TPM_HORIZONTAL = 0x0000;
const TPM_VERTICAL = 0x0040;
const TPM_HORPOSANIMATION = 0x0400;
const TPM_HORNEGANIMATION = 0x0800;
const TPM_VERPOSANIMATION = 0x1000;
const TPM_VERNEGANIMATION = 0x2000;
const TPM_NOANIMATION = 0x4000;
```

[https://docs.microsoft.com/en-gb/windows/win32/api/winuser/nf-winuser-trackpopupmenu](https://docs.microsoft.com/en-gb/windows/win32/api/winuser/nf-winuser-trackpopupmenu)

## Mouse Mask Values
```js
const MK_LBUTTON = 0x0001;
const MK_RBUTTON = 0x0002;
const MK_SHIFT = 0x0004;
const MK_CONTROL = 0x0008;
const MK_MBUTTON = 0x0010;
const MK_XBUTTON1 = 0x0020;
const MK_XBUTTON2 = 0x0040;
```

## SetCursor Values
```js
const IDC_ARROW = 32512;
const IDC_IBEAM = 32513;
const IDC_WAIT = 32514;
const IDC_CROSS = 32515;
const IDC_UPARROW = 32516;
const IDC_SIZE = 32640;
const IDC_ICON = 32641;
const IDC_SIZENWSE = 32642;
const IDC_SIZENESW = 32643;
const IDC_SIZEWE = 32644;
const IDC_SIZENS = 32645;
const IDC_SIZEALL = 32646;
const IDC_NO = 32648;
const IDC_APPSTARTING = 32650;
const IDC_HAND = 32649;
const IDC_HELP = 32651;
```

## FILE_ATTRIBUTE
```js
const FILE_ATTRIBUTE_READONLY = 0x00000001;
const FILE_ATTRIBUTE_HIDDEN = 0x00000002;
const FILE_ATTRIBUTE_SYSTEM = 0x00000004;
const FILE_ATTRIBUTE_DIRECTORY = 0x00000010;
const FILE_ATTRIBUTE_ARCHIVE = 0x00000020;
const FILE_ATTRIBUTE_NORMAL = 0x00000080;
const FILE_ATTRIBUTE_TEMPORARY = 0x00000100;
const FILE_ATTRIBUTE_SPARSE_FILE = 0x00000200;
const FILE_ATTRIBUTE_REPARSE_POINT = 0x00000400;
const FILE_ATTRIBUTE_COMPRESSED = 0x00000800;
const FILE_ATTRIBUTE_OFFLINE = 0x00001000;
const FILE_ATTRIBUTE_NOT_CONTENT_INDEXED = 0x00002000;
const FILE_ATTRIBUTE_ENCRYPTED = 0x00004000;
// const FILE_ATTRIBUTE_DEVICE // do not use
// const FILE_ATTRIBUTE_VIRTUAL // do not use
```

[http://msdn.microsoft.com/en-us/library/ee332330%28VS.85%29.aspx](http://msdn.microsoft.com/en-us/library/ee332330%28VS.85%29.aspx)

## Keyboard Mask Values
```js
const VK_BACK = 0x08;
const VK_TAB = 0x09;
const VK_RETURN = 0x0D;
const VK_SHIFT = 0x10;
const VK_CONTROL = 0x11;
const VK_ALT = 0x12;
const VK_ESCAPE = 0x1B;
const VK_PGUP = 0x21;
const VK_PGDN = 0x22;
const VK_END = 0x23;
const VK_HOME = 0x24;
const VK_LEFT = 0x25;
const VK_UP = 0x26;
const VK_RIGHT = 0x27;
const VK_DOWN = 0x28;
const VK_INSERT = 0x2D;
const VK_DELETE = 0x2E;
const VK_SPACEBAR = 0x20;
```

## AlbumArtId
```js
const AlbumArtId = {
	front : 0,
	back : 1,
	disc : 2,
	icon : 3,
	artist : 4,
};
```

## AlbumArtType
```js
const AlbumArtType = {
	embedded : 0,
	default : 1,
	stub : 2,
};
```

## ColourType
```js
const ColourType = {
	text : 0,
	background : 1,
	highlight : 2,
	selection : 3,
};
```

## FontType
```js
const FontType = {
	defaults : 0,
	tabs : 1,
	lists : 2,
	playlists : 3,
	statusbar : 4,
	console : 5,
};
```

## PlaylistLockFilterMask
```js
const PlaylistLockFilterMask = {
	filter_add : 1,
	filter_remove : 2,
	filter_reorder : 4,
	filter_replace : 8,
	filter_rename : 16,
	filter_remove_playlist : 32,
};
```

## ReplaygainMode
```js
const ReplaygainMode = {
	None : 0,
	Track : 1,
	Album : 2,
	Track_Album_By_Playback_Order : 3,
};
```

## PlaybackOrder
```js
const PlaybackOrder = {
	Default : 0,
	Repeat_Playlist : 1,
	Repeat_Track : 2,
	Random : 3,
	Shuffle_tracks : 4,
	Shuffle_albums : 5,
	Shuffle_folders : 6,
};
```

## PlaybackQueueOrigin
```js
const PlaybackQueueOrigin = {
	user_added : 0,
	user_removed : 1,
	playback_advance : 2,
};
```

## PlaybackStartingCMD
```js
const PlaybackStartingCMD = {
	default : 0,
	play : 1,
	next : 2,
	prev : 3,
	settrack : 4,
	rand : 5,
	resume : 6,
};
```

## PlaybackStopReason
```js
const PlaybackStopReason = {
	user : 0,
	eof : 1,
	starting_another : 2,
};
```

## SelectionType
```js
const SelectionType = {
	undefined : 0,
	active_playlist_selection : 1,
	caller_active_playlist : 2,
	playlist_manager : 3,
	now_playing : 4,
	keyboard_shortcut_list : 5,
	media_library_viewer : 6,
};
```
