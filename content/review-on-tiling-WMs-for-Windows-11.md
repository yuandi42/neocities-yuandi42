---
title: "Review on Tiling WMs for Windows 11"
date: 2022-09-03T00:34:29+08:00
<!-- draft: true -->
tags: [ 'software' ]
---

Not long ago, I played a little with Windows 11 mainly to give
[WSLg](https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps) a try.
Though now decorated with eyecandies such as blur effect and rounded corners,
Windows is still awful and hard to use. Anyway, during the time fighting with
M$, I've struggled to living in a [tiling
WM](https://en.wikipedia.org/wiki/Tiling_window_manager) environment since I am
a long time [dwm](https://dwm.suckless.org/) user. I have tried most of tiling
WMs I could find for Win11 before I finaaly got tried of it. And now let me
share my experiece with you. **Spoiler Warning**: they all suck!

## Windows-built-in

As is known to all, you can manage windows' size and position by
<kbd>Super</kbd> + <kbd>↑↓←→</kbd>; switch between virtual desktops (workspace
/ group / tag for this OS) by <kbd>Super</kbd> + <kbd>Ctrl</kbd> +
<kbd>←→</kbd>; cycle around windows with <kbd>Alt</kbd> + <kbd>Tab</kbd> /
<kbd>Esc</kbd>. Now in Win11, you can also hover cursor on normalized /
maximized button for a while, then a subframe will pop up, and you can choose a
layout displayed in that frame and put windows in position you want by
clicking. Pretty Windows-style, right?

However, Windows still has no bulit-in ways to automaticly tile window, so
below comes our tiling window manager candidates:

## [bug.n](https://github.com/fuhsjr00/bug.n)

bug.n is a dwm-copy so famous that even suckless guys metion it on their
website. You can get the latest version from gituhb, which released on 2019, so
it may not be fully compatible with Win11. And actually, it is extremely buggy.

1. It has no support for Windows virtual desktop (which was introduced into
   Windows when 10 came out). And it deals with windows from multiple desktops
   as if they are in the same desktop.
1. I am not quite sure, but it seems to recognize something as a invisible
   window. So there is always a blank to my screen, what a waste of space.

I guess bug.n may be a good WM for a Win7 user, but don't consider about it
when comes to Win11.

## [Workspacer](https://workspacer.org/)

Another dwm-copy on Windows, and it's much better, yet still buggy. This
project is quite active, and you can get the latest realease from github or
install it using choco/winget.

It has a better default keybindings (by better I mean closer to dwm), but still
no support for virtual desktop (they consider adding the feature). At least no
strange blank on my screen now. And there things really werid.

1. All keybinding involving <kbd>Shift</kbd> only work with the left one. lol.
1. Morever, everytime I start it, a strange powershell window launched then
   quit.
1. And I cannot stop the WM by quit the systray. The only way to get rid of it
   is to kill the process in task manager.

Well, Workspacer is more usable than bug.n on Win11, however, it is still far
from a handy WM. Will rest of them be better?

## [Amethyst Windows v2](https://amethystwindows.com/)

It seems to be ported from a WM designed for Mac OS X. And it's even worse than
WMs ahead. How? 

1. It crashes from time to time.
1. It has no hint at all when you change window focus.
1. It doesn't totally run in background. And there always a tiny window living
   on desktop, very annoying when you press <kbd>Alt</kbd> + <kbd>Tab</kbd>.
1. Although it support Windows virtual desktop, its performance is buggy when
   you manually move window between desktops.

At least we can move between virtual desktops now. But this tiling WM is still,
unuseable.

## [Win3wm](https://github.com/McYoloSwagHam/win3wm)

It didn't work at all, at least on my machine. I did a breif research (refused
to waste too much time on it) but still couldn't work it out --- so, sayonara,
Win3wm.

## [komorebi](https://github.com/LGUG2Z/komorebi)

As the author claimed in the github repo, it's a bspwm-inspired project. And I
have to admit that the demo video on their README did impressed me. Would it be
the chosen WM? The answer is nope.

Just like bspwm, it has no built-in way to manage windows through keybindings,
so you need an additional hotkey daemon.
[AutoHotKey](https://www.autohotkey.com/) seems to be the only decent choice,
and the documentation also recommends you to use that. It also offer a example
`.ahk` file for configuration. Nervertheless, the exmaple config is fxxking
broken, or out of date, who cares. So I try to run `komorebic` commands in
powershell. Then I found:

1. It's fxxking slow. I need to wait until Hell freezes over from `komorebic
   start` to windows finally get tiled.
1. It doesn't support virtual desktop (again!), and handles windows from
   multiple desktops just like bug.n.
1. `komorebic focus left/right/up/down` doesn't change window focus as I
   expect. It just moves cursor to the window I want to focus on and then
   this window just gets urgent. Nice joke, haha.

Only taking it's snail-like speed into accout, komorebi is not a useable WM.
It's just a lame bspwm imitator, not bspwm on Win11.

## [FacnyWM](https://apps.microsoft.com/store/detail/9P1741LKHQS9)

You can install it from M$ $tore for free (free as in... free beer), and it's
the only way to get it, I guess.

It's a proprietary software based on an open source porject called winman
(cucked MIT licnese, lol). You can download it for free, however, a license
must be purchased for continued use. And as you can imagine, windows pop up
sometime, begging you to pay for it, just like an annoying fly.

Don't consider above awful factors, this WM is, well, close to a okay level. It
is stable and fast enough for daily use. FancyWM uses key chords to manage
windows and virtual desktops (and it has the most distinguished support for
virtual desktops, which is almost flawless compared with WM above).

Its keybindings may be difficult to get started for a dynamic window manager
user. Nevertheless, here is a thing: it is impossible to live in Windows
without a mouse , hence those hotkeys become somehow senseless when you hold
the mouse in your right hand most of the time. Then what really matters is the
speed of windows getting tiled by WM. In that aspect, FancyWM is passable,
especially compared to other window managers I've tried. 

## When they encounter WSLg window...

Oh, seems that we come to the end and FancyWM is worth keeping? Absolutely no.
As I mentioned above, all those WMs I tried suck, they share the same cons: 

1. None, I mean, no one of them, even Windows-built-in keybindings, can handle
   WSLg correctly. Yeah, I know it's caused by some API problems. And the fact
   that Linux GUI programs can run on Windows 11 is kind of mircale. So I can
   accept if those WM deal with my emacs on Debian WSL as if it doesn't exist.
   But you, Workspacer? Can you tell me why you got totally crashed? Come on,
   the main reason I come to Windows 11 is the WSLg. But those WSLg windows
   cannot work with any of WM, which destories my workflow.
1. If you launch WMs as a normal user, then those WMs can't handle windows with
   admin privilege correctly. And if you launch them as admin, while, it's
   okay, unless you worry about security porblem, or get annoyed since it
   always asks you for an admin rights(while, I did got annoyed). But why
   should we do that? Every tiling window manager on Linux (and BSD) works fine
   without root privilege. I can `exec dwm` as a normal user, run `sudo st`,
   and this terminal window still get tiled, just like any other windows.
1. Their keybindings, although that doesn't really matter, are sucked. And they
   have to be sucked because Windows-built-in keybindings (totally useless!)
   occupy some commmon combination suck as <kbd>Super</kbd> + <kbd>k</kbd>,
   <kbd>Super</kbd> + <kbd>l</kbd> and etc. And I guess there is no way to
   change those keybindings (maybe Powertoy can do that in a tricky way).

## Conclusion

As you see, I've tried so many tiling WMs on Windows 11, yet none of them
satisfied me. I know there are fxxking much more WMs that I haven't tried, but
I need a break from those cucked programs. Don't bother me with any other
tiling window managers for Windows 11. If you did need one, I would recommend
FancyWM, even though it's a proprietary garbage and you need to pay for an
advanced edition. Now it's time to go back to my cozy GNU/Linux cabin and take
a nice nap.
