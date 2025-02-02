## Output modes

Here, you can browse the range of ways that Raycast lets you view your data, whether you need to display a range of items such as open pull requests, or whether you just need confirmation that your script has run successfully.

In `fullOutput` the entire output is presented on a separate view, similar to a terminal window. This is handy when your script generates output to consume.

![fullOutput mode](/images/screenshots/fulloutput-mode.png)

In `compact` mode the last line of the standard output is shown in the toast

![compact mode](/images/screenshots/compact-mode.png)

In `silent` mode the last line (if exists) will be shown in overlaying HUD toast after Raycast window is closed.

![silent mode](/images/screenshots/silent-mode.png)

In `inline` mode, the first line of output will be directly shown in the command item and automatically refresh according to the specified `refreshTime`. Tip: Set your dashboard items as favourites via the action menu in Raycast

![inline mode](/images/screenshots/inline-mode.png)

**🚨 Hint:** use `cmd k` to access extra functionality such as adding to favourites or reordering the root search preferences.

# ANSII Supported Colors 🎨

We support colors for `inline` and `fullOutput` mode scripts for you to customise generated output by changing its background and foreground color.

![colors inline mode](/images/screenshots/inline-colours.png)

Escape code is in linux format: `0x1B`

## 3-bit colors (8-color mode)

Colors are adapted to current users apperance settings (light and dark themes)
| Color | # Foreground | # Background | Light | Dark |
| ------ | ------------ | ------------ | ----- | ---- |
| Black | 30 | 40 | #000000 | #000000 |
| Red | 31 | 41 | #B12424 | #FF6363 |
| Green | 32 | 42 | #006B4F | #59D499 |
| Yellow | 33 | 43 | #F8A300 | #FFC531 |
| Blue | 34 | 44 | #138AF2 | #56C2FF |
| Magenta | 35 | 45 | #9A1B6E | #CF2F98 |
| Cyan | 36 | 46 | #3EB8BF | #52EEE5 |
| White | 97 | 107 | #FFFFFF | #FFFFFF |

## 8-bit colors (256-color mode)
https://en.wikipedia.org/wiki/ANSI_escape_code#8-bit

`38;5;⟨n⟩m` - Select 8-bit foreground color

`48;5;⟨n⟩m` - Select 8-bit background color

![image](https://user-images.githubusercontent.com/1301068/114558204-bc076600-9c6a-11eb-806a-ab07ddf0d290.png)

## 24-bit colors (TrueColor mode)
https://en.wikipedia.org/wiki/ANSI_escape_code#24-bit

`38;2;⟨r⟩;⟨g⟩;⟨b⟩m` - Select RGB foreground color

`48;2;⟨r⟩;⟨g⟩;⟨b⟩m` - Select RGB background color


## Other supported codes

| Code | Name |
| ---- | ---- |
| 0 | Reset (normal) |
| 4 | Underline |
| 9 | Crossed out |
| 24 | Not underlined |
| 29 | Not crossed out |

**💡Hint:** Unsupported terminal codes will be stripped out from output and ignored.

**Example:**

![colors inline mode](/images/screenshots/colour-example.png)
| Script | Code |
| ------ | ---- |
| bash (3-bit) | `echo -e '\033[31;42mred text on green background\033[0m'` |
| bash (8-bit) | `echo -e '\033[38;5;196m\033[48;5;70mred text on green background\033[0m'` |
| bash (24-bit) | `echo -e '\033[38;2;255;0;0m\033[48;2;0;255;0mred text on green background\033[0m'` |
| bash tput | `export TERM=linux; echo "$(tput setaf 1)$(tput setab 2)red text on green background$(tput sgr0)";` |
| swift (8-bit) | `print("\\u{001B}[31;42mred text on green background\\u{001B}[0m")` |
| osascript (8-bit) | `do shell script "echo '\\033[31;42mred text on green background\\033[0m'"`|
