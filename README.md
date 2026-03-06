# Password Field Widget

**ID:** `org.openxtalk.widget.passwordfield`  
**Author:** Emily-Elizabeth Howard  
**Version:** 1.0.0  
**Platform:** macOS only

---

## Overview

A native macOS password field widget for LiveCode, wrapping `NSSecureTextField` via the LiveCode Builder Objective-C bridge. Characters are masked as the user types, making it suitable for secure password entry.

---

## Requirements

- LiveCode 9.6 or later
- macOS (the widget uses a native AppKit view and will not render on other platforms)

---

## Installation

Place `org.openxtalk.widget.passwordfield.lcb` in your LiveCode extension folder and compile it using the Extension Builder, or distribute the compiled `.lce` bundle.

---

## Usage

Drag the **Password Field** widget onto a card from the widget palette. At runtime a native `NSSecureTextField` is displayed. In the IDE editor the widget appears blank — this is expected behaviour, identical to LiveCode's own built-in native Mac field widgets.

### Getting the entered password

```livescript
put the passwordText of widget "myPasswordField" into tPassword
```

### Setting a value programmatically

```livescript
set the passwordText of widget "myPasswordField" to ""
```

### Setting placeholder text

```livescript
set the placeholder of widget "myPasswordField" to "Enter your password"
```

### Enabling and disabling

```livescript
set the enabled of widget "myPasswordField" to false
```

### Handling the return key

```livescript
on returnKey
    put the passwordText of the target into tPassword
    -- validate or submit tPassword
end returnKey
```

---

## Properties

| Property | Type | Default | Description |
|---|---|---|---|
| `passwordText` | String | `""` | The current (plaintext) contents of the field. |
| `placeholder` | String | `"Password"` | Hint text shown when the field is empty. |
| `enabled` | Boolean | `true` | Whether the field is editable. Inherited from the host widget. |

---

## Messages

| Message | Description |
|---|---|
| `returnKey` | Sent to the widget's script object when the user presses the Return key. |

---

## Notes

- The widget appearance (font, bezel style, focus ring) follows the macOS system style automatically.
- The `passwordText` property returns the live value from the native field whenever it is available, so there is no need to observe a change message to read the current input.
- This widget does not support Windows, Linux, iOS, or Android. On non-Mac platforms a placeholder image is displayed instead.
