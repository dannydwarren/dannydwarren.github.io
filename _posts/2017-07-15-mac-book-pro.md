---
layout: post
title: Mac Book Pro
comments: true
categories: [software]
tags:       [apple, productivity]
---
## My First Mac
I recently started at Pluralsight and as my daily machine I now have a MacBook Pro (15-inch, 2016). I really like it, except for all the things I don't like... See I'm a Microsoft fan boy. So I'm used to having a lot of the OS provided up front, but on Mac I find myself craving functionality that is not available by default. Luckily all the Mac folks before me have realized these short comings already and have made add-on products that I can use to fill in those gaps. So without further ado here is my list (updated over time) of products, utilities, tools, and other learnings that I wish I was told before I joined all the iSheeple.

## Touch Bar
I don't hate the touch bar, but I certainly do not like it. It lacks feedback and it absorbed the much needed `ESC` key that I use heavily as a developer.

### How to make the Function Keys the Default Keys for the Touch Bar
The touch bar also abstracts away the critical function keys needed for debugging. Luckily there is a way to [make function keys the default for individual apps](https://www.igeeksblog.com/how-to-use-function-keys-on-macbook-pro-with-touch-bar/) which is actually a really great way to do it.

## Trackpad (UPDATE: 2017-12-21)
I LOVE THE TRACKPAD!!! Haptic feedback is amazing! Not having a physical rotation point for clicking is a game changer. I can use the entire trackpad without worrying about losing my click or needing to click harder.

### Single Touch to Look-up: Thumbs Down!
The only bad part about the trackpad in MacOS so far is the single touch to look-up, but there is a fix for that! Go to (CNet's post)[http://ccm.net/faq/40112-mac-os-x-yosemite-turn-off-the-trackpad-look-up-feature] to learn how to turn it off. No more annoying dictionary look-ups while clicing around in websites etc.

## Terminal Woes
Okay, 'woes' may be too strong a word. Let's face it, terminal and cmd both suck as is. PowerShell is awesome and is now cross-platform, but if you want to understand all the help docs and tutorials for Mac out there you need to understand bash. So I've been introduced to [zsh](http://ohmyz.sh/) which makes the terminal x1000 better! Actually, I really like it. Strange coming from this GUI lover.

### A Better Terminal
There is even another option on Mac to take the terminal to the next level and that is [iTerm2](https://iterm2.com/). It's pretty awesome, but you'll have to do your own research to see what all it's capable of as I'm still just getting into it.

### Window Management
In Windows we can do `WIN + SHIFT + ARROW` to dock a window to a certain location. This feature is one of my favorites and does not exist in MacOS and has been my #1 complaint. Recently I was introduced to [Divvy](http://mizage.com/divvy/) and it is awesome! It is a paid product, but at ~$15 it's worth every penny! They also provide a Windows version which I have not tried yet, but I intend to try it because it is that awesome!

## Back to Windows
You knew this was coming! I love Windows, it's my native land. I use a [Boot Camp](https://support.apple.com/boot-camp) partition to boot Windows native. Then I use [Parallels](https://www.parallels.com/) to load that native partition as a VM from within MacOS. Most of my use cases haven't needed native Windows as yet so I've been primarily in MacOS and using Parallels for Windows.

### Lesson Learned Running Windows in Parallels:

#### Back Button in Chrome
Left-click back in Chrome with multiple pages to go back though. While holding left-click then right-click multiple times. The interrupt causes left-click to be detected again and goes back. This is annoying when a second finger touches the trackpad while clicking the back button. So keep those fingers up mates!

### Lessons Learned Running Windows Native via Boot Camp:

#### Trackpad
Even I have to admit that trackpad in Mac is the best in class. I'm totally blown away that I almost never have erroneous clicks when typing in MacOS even with my sweaty palms all over this trackpad. It's a breath of fresh air! However, the awesome trackpad is only awesome by combining Apple hardware with MacOS. Once inside Windows native on Apple hardware the trackpad is no better and sometimes worse, because of size, than other hardware. The solution for this poor experience is [Trackpad++](http://trackpad.forbootcamp.org/) which helps replicate some awesome MacOS gestures in Windows and also allows you to turn the trackpad off all together! If you don't purchase it, you are required to update to the latest version. Not a bad deal if you always want the latest for free!

##### Trackpad++ Configuration (UPDATE: 2017-12-21)
- 2-Finger Gestures
  - Disable: Pinch-to-Zoom, Accelerate Scroll, Edge Gestures (use the settings icon by it)
  - Enable: Invert Swipe Dir., Invert Scroll Dir.
- Trackpad as Mouse
  - Disable: Tap-to-Click
- Elimination of Accidental Input
  - Enable: On Lifting Fingers Release 3-Finger Drag Immediately (No Delay), When Typing, Ignore All 'Trackpad Input', Lower Pinch-to-Zoom Sensitivity
- 3-Finger Gestures
  - Swipe Left: Next Desktop
  - Swipe Right: Previous Desktop
- 4-Finger Gestures
  - Swipe Left: Forward
  - Swipe Right: Back
- Update Windows Settings for Mouse
  - Open: Change your mouse settings
    - Choose how many lines to scroll each time: Lower to 1 (min). NOTE: This will make the mouse scroll feel slow, but you can use mouse wheel specific settings to overcome this if you have a Logitech mouse or potentially other brands with dedicated mouse software.

## Other Thoughts
If you have any awesome tools to make MacOS or Windows on Apple hardware better leave a comment! I'm all about making our OS as comfortable as possible and would love to have a similar experience on both Windows and MacOS. That may be blasphemous to some, but really a computer is a computer and an OS is just that an OS, not a religion! 
