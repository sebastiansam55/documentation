# Keychron K8 Keyboard on Linux

## Intro and first Config

First thing make sure the `USB-C` plug is pushed all of the way in, I had to push relatively hard for the keyboard to be connected correctly to my computer.

This is a pretty reliable source and the solutions appear to be more or less completely applicable to the `K8` at the least.

[Keychron K2 config on github](https://github.com/Kurgol/keychron/blob/master/k2.md)

From the above link I used the alternative solution under `udev`;

Having the keyboard in the MacOS mode I executed:
`sudo touch /etc/modprobe.d/hid_apple.conf`
Open the file in your editor of choice (`sudo nano`) and add `options hid_apple fnmode=2` and write the changes.

Execute `sudo update-initramfs -u` and reboot the computer.

Make sure to switch the selector switch on the side of the keyboard to `Windows/Android` and everything works as expected for me. `F[1-12]` activate as expected and pressing `FN+F1` etc activate the functions related.

I would very much recommend that you upgrade to some thicker PBT key caps as the ones that ship with the `K8` are exceptionally grating to listen to. To my ear they make a really high pitch sort of ringing that borders on unbearable. I also have o-rings on my new key caps which help but I don't think are as necessary as PBT/thicker key caps.

## Keys
Being a TKL layout the `K8` has most if not all of the keys that I regularly use with some notable, annoyingly unnecessary exceptions.

### The Scroll Lock key
The scroll lock key does not send the scroll lock key. Instead it sends "`<LEFT_META>+j`" (KC:`125+36`) on the "`Windows`" layout or "`SPACE+FN`" (KC:`57+464`)  on the MacOS layout which are supposedly the key combinations used to activate Cortana and Siri. 

This seems like a complete waste of the key. Do I use scroll lock for scroll lock? Absolutely not. I use it as a toggle mute in voice chat application so I can look at my keyboard and see at a glance what the state of my microphone is (at least I could do this on keyboards that have a scroll lock indicator light). But now on my keyboard it is an unused and unloved key.

### The pause/break key
Right (on the left) next to it is where the "Pause\Break" key usually resides. Not so on the `K8` instead is the `K8` lighting control. This key does not send any signals to the computer at all from my examination of the device. 

Do I use the key as a pause/break key? Also no but it was a convenient key to bind as a shortcut for various other programs because it was essentially a "free" key. 

The use of this key as the light key is particularly annoying as there is not a way to disable it. Meaning any time that it is bumped you will have to cycle through all 16 different lighting modes to arrive back at your desired one.

### The `Fn` key. 
The `Fn` key operates very differently between the two layouts.

- Windows layout
    + On this layout the key does not send any events at all. In the [manual](https://www.keychron.com/pages/k8-keyboard-user-manual) there is an option to switch to a more `MacOS` type functionality where pressing the `F[1-12]` keys sends the signals like keyboard backlight before the `F[1-12]` signals.
    + No matter what the `Fn` key functionality is it does not send any signals to the computer on the Windows layout. The `F[1-12]` switching takes place entirely within the keyboard firmware.
- MacOS layout
    + On this layout the `Fn` key sends the `KEY_FN` or `464` scan code.
    + It will not send anything if you press `Fn+[1-3]` because this is bound to switching bluetooth devices. This is despite the keyboard being connected via a wired connection (making the `Fn+[1-3]` hotkeys useless)
    + Note that any other key combinations as described in the `K8` [quick start](https://cdn.shopify.com/s/files/1/0059/0630/1017/files/K8_QSD-1.jpg?v=1596771405) will also not send key strokes when combined with the `FN` key
        * This list includes; `S O X L 1 2 3`
        * I find this list of caveats to the function of the `FN` key to be so arbitrary to make it useless as other wise I would have to remember all of these when adding the `FN` to a hotkey.

## Devices added
Many keyboards add more than one device to `/dev/input`, the `K8` adds two devices when connected via wired and adds three devices when connected via bluetooth.

It is unclear what the 3rd device added when the keyboard is connected via bluetooth does. I have not been able to see any events sent by it during regular usage. I suspect that it is related to the bluetooth sleep functions as the listed capabilities as reported by `evtest` are as follows;
```
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 142 (KEY_SLEEP)
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
```

## Device Names

| Type | Name | Function | Physical Address |
| :--: | :--: | :------: | :--------------: |
| Wired | Keychron K8 Keychron K8 | Keyboard input | `usb-0000:00:14.0-1.3/input0` |
| Wired | Keychron K8 Keychron K8 | Function input | `usb-0000:00:14.0-1.3/input1` |
| Bluetooth | Keychron K8 Keyboard | Keyboard input | `b8:76:3f:ac:2c:05` |
| Bluetooth | Keychron K8 System Control | ? | `b8:76:3f:ac:2c:05` |
| Bluetooth | Keychron K8 Consumer Control | Function input | `b8:76:3f:ac:2c:05` |

The Keyboard input devices handle all of the regular key events, and the Function inputs handle the "Functions" like the screen brightness, media control, volume control etc.  


## Function Keys
On the Windows layout (pressing `FN+F[1-12]`):
<<<<<<< Updated upstream
=======

>>>>>>> Stashed changes
| Key | Key Signal | Scan Code | Device | Purpose |
| :-: | :--------: | :-------: | :----: | :-----: |
| `FN+F1` | `KEY_BRIGHTNESSDOWN` | `224` | Function input | Screen brightness |
| `FN+F2` | `KEY_BRIGHTNESSUP` | `225` | Function input | Screen brightness |
| `FN+F3` | `KEY_LEFTMETA+KEY_TAB` | `125+15` | Keyboard input | Switch windows |
| `FN+F4` | `KEY_LEFTMETA+KEY_DOT` | `125+52` | Keyboard input | ? |
| `FN+F5` | None | None | None | Decrease keyboard brightness |
| `FN+F6` | None | None | None | Increase keyboard brightness |
| `FN+F7` | `KEY_PREVIOUSSONG` | `165` | Function input | Media key |
| `FN+F8` | `KEY_PLAYPAUSE` | `164` | Function input | Media key |
| `FN+F9` | `KEY_NEXTSONG` | `163` | Function input | Media key |
| `FN+F10` | `KEY_MUTE` | `113` | Function input | Volume control |
| `FN+F11` | `KEY_VOLUMEDOWN` | `114` | Function input | Volume control |
| `FN+F12` | `KEY_VOLUMEUP` | `115` | Function input | Volume control |

On the MacOS layout (pressing `FN+F[1-12]`):
<<<<<<< Updated upstream
=======

>>>>>>> Stashed changes
| Key | Key Signal | Scan Code | Device | Purpose |
| :-: | :--------: | :-------: | :----: | :-----: |
| `FN+F1` | `KEY_BRIGHTNESSDOWN` | `224` | Keyboard input | Screen brightness |
| `FN+F2` | `KEY_BRIGHTNESSUP` | `225` | Keyboard input | Screen brightness |
| `FN+F3` | `KEY_SCALE` | `120` | Keyboard input | Switch windows |
| `FN+F4` | `KEY_DASHBOARD` | `204` | Keyboard input | ? |
| `FN+F5` | None | None | None | Decrease keyboard brightness |
| `FN+F6` | None | None | None | Increase keyboard brightness |
| `FN+F7` | `KEY_PREVIOUSSONG` | `165` | Keyboard input | Media key |
| `FN+F8` | `KEY_PLAYPAUSE` | `164` | Keyboard input | Media key |
| `FN+F9` | `KEY_NEXTSONG` | `163` | Keyboard input | Media key |
| `FN+F10` | `KEY_MUTE` | `113` | Keyboard input | Volume control |
| `FN+F11` | `KEY_VOLUMEDOWN` | `114` | Keyboard input | Volume control |
| `FN+F12` | `KEY_VOLUMEUP` | `115` | Keyboard input | Volume control |



## LEDS
On the keyboard, not counting the RGB backlight. There are three LEDS above the arrow cluster on the right hand size.
- Power LED
- Bluetooth LED
- CAPS_LOCK LED

When these LEDs are activated is self evident.

However, according to `evtest` the keyboard has the following LED events. 

```bash
  Event type 17 (EV_LED)
    Event code 0 (LED_NUML) state 0
    Event code 1 (LED_CAPSL) state 0
    Event code 2 (LED_SCROLLL) state 0
    Event code 3 (LED_COMPOSE) state 1
    Event code 4 (LED_KANA) state 0
```

<<<<<<< Updated upstream
Out of these only LED_CAPSL appears to effect the physical LEDs on the keyboard.
=======
Out of these only `LED_CAPSL` appears to effect the physical LEDs on the keyboard.
>>>>>>> Stashed changes

## Notes
All key/scan codes are those as reported by `evtest`, mostly on the wired connection unless otherwise specified.

Note that when a key is mentioned it is described by it's qwerty layout value. If you map your keyboard to a different layout the location of these hot keys does not move. IE: if you use dvorak which moves the location of many of the keys the shortcut for toggling Auto Sleep Mode `FN+S+O` will be `FN+O+R` on a dvorak keyboard, with the S->O and O->R. 