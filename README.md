# Arch-i3

```
Arch Linux (or Arch) is a Linux distribution for computers based on x86-64 architectures.
The design approach of the development team follows the KISS principle ("keep it simple,
stupid") as the general guideline, and focuses on elegance, code correctness, minimalism
and simplicity, and expects the user to be willing to make some effort to understand the
system's operation.
Arch Linux uses a rolling release model, such that a regular system update is all that 
is needed to obtain the latest Arch software; the installation images released by the 
Arch team are simply up-to-date snapshots of the main system components.
```
---
[for more info visit ArchWiki](https://wiki.archlinux.org/ "ArchWiki")


```
i3 is a tiling window manager designed for X11, inspired by wmii, and written in C.
It supports tiling, stacking, and tabbing layouts, which it handles dynamically.
Implement different modes, similar to the text editor vi and vim. That is, keys 
have different functions depending on the mode the window manager is in.
The configuration is done via a plain text file, i3 can be customized without 
programming.
```
---
[for more info visit i3](https://wiki.archlinux.org/ "i3")


## Contents
* [arch wallpaper](#archwallpaper)
* [i3 config file](#i3configfile)
* [.Xresources file](#.Xresourcesfile)
* [31 hold shift file](#31_hold_shift)
* [arch packages](#archpackages)
* [hdmi script](#hdmiscript)

<a name="archwallpaper"></a>
### arch wallpaper 

![arch wallpaper](https://github.com/AntenehDev/Arch-i3/blob/master/arch.png)

<a name="i3configfile"></a>
### i3 config file 

```bash
# i3 config file (v4)
# Please see http://i3wm.org/docs/userguide.html for a complete reference!

# Set mod key (Mod1=<Alt>, Mod4=<Super>)
set $mod Mod4

# set default desktop layout (default is tiling)
# workspace_layout tabbed <stacking|tabbed>

# Configure border style <normal|1pixel|pixel xx|none|pixel>
new_window pixel 1
new_float normal

# Hide borders
hide_edge_borders none

# change borders
bindsym $mod+u border none
bindsym $mod+y border pixel 1
bindsym $mod+n border normal

# Font for window titles. Will also be used by the bar unless a different font
# is used in the bar {} block below.
font xft:URWGothic-Book 11

# Use Mouse+$mod to drag floating windows
floating_modifier $mod

# start a terminal
bindsym $mod+Return exec terminal

# kill focused window
bindsym $mod+Shift+q kill

# start program launcher
#bindsym $mod+d exec --no-startup-id dmenu_recency

# launch categorized menu
bindsym $mod+z exec --no-startup-id morc_menu

################################################################################################
## sound-section - DO NOT EDIT if you wish to automatically upgrade Alsa -> Pulseaudio later! ##
################################################################################################

exec --no-startup-id volumeicon
bindsym $mod+Ctrl+m exec terminal -e 'alsamixer'
#exec --no-startup-id pulseaudio
#exec --no-startup-id pa-applet
#bindsym $mod+Ctrl+m exec pavucontrol

################################################################################################

# Screen brightness controls
# bindsym XF86MonBrightnessUp exec "xbacklight -inc 10; notify-send 'brightness up'"
# bindsym XF86MonBrightnessDown exec "xbacklight -dec 10; notify-send 'brightness down'"

# Start Applications
bindsym $mod+Ctrl+b exec terminal -e 'bmenu'
bindsym $mod+F2 exec palemoon
bindsym $mod+F3 exec pcmanfm
# bindsym $mod+F3 exec ranger
bindsym $mod+Shift+F3 exec gksu pcmanfm
bindsym $mod+F5 exec terminal -e 'mocp'
bindsym $mod+t exec --no-startup-id pkill compton
bindsym $mod+Ctrl+t exec --no-startup-id compton -b
bindsym $mod+Shift+d --release exec "killall dunst; exec notify-send 'restart dunst'"
bindsym Print exec --no-startup-id i3-scrot
bindsym $mod+Print --release exec --no-startup-id i3-scrot -w
bindsym $mod+Shift+Print --release exec --no-startup-id i3-scrot -s
bindsym $mod+Shift+h exec xdg-open /usr/share/doc/manjaro/i3_help.pdf
bindsym $mod+Ctrl+x --release exec --no-startup-id xkill

# focus_follows_mouse no

# change focus
bindsym $mod+j focus left
bindsym $mod+k focus down
bindsym $mod+l focus up
bindsym $mod+semicolon focus right

# alternatively, you can use the cursor keys:
bindsym $mod+Left focus left
bindsym $mod+Down focus down
bindsym $mod+Up focus up
bindsym $mod+Right focus right

# move focused window
bindsym $mod+Shift+j move left
bindsym $mod+Shift+k move down
bindsym $mod+Shift+l move up
bindsym $mod+Shift+semicolon move right

# alternatively, you can use the cursor keys:
bindsym $mod+Shift+Left move left
bindsym $mod+Shift+Down move down
bindsym $mod+Shift+Up move up
bindsym $mod+Shift+Right move right

# workspace back and forth (with/without active container)
workspace_auto_back_and_forth yes
bindsym $mod+b workspace back_and_forth
bindsym $mod+Shift+b move container to workspace back_and_forth; workspace back_and_forth

# split orientation
bindsym $mod+h split h;exec notify-send 'tile horizontally'
bindsym $mod+v split v;exec notify-send 'tile vertically'
bindsym $mod+q split toggle

# toggle fullscreen mode for the focused container
bindsym $mod+f fullscreen toggle

# change container layout (stacked, tabbed, toggle split)
bindsym $mod+s layout stacking
bindsym $mod+w layout tabbed
bindsym $mod+e layout toggle split

# toggle tiling / floating
bindsym $mod+Shift+space floating toggle

# change focus between tiling / floating windows
bindsym $mod+space focus mode_toggle

# toggle sticky
bindsym $mod+Shift+s sticky toggle

# focus the parent container
bindsym $mod+a focus parent

# move the currently focused window to the scratchpad
bindsym $mod+Shift+minus move scratchpad

# Show the next scratchpad window or hide the focused scratchpad window.
# If there are multiple scratchpad windows, this command cycles through them.
bindsym $mod+minus scratchpad show

#navigate workspaces next / previous
bindsym $mod+Ctrl+Right workspace next
bindsym $mod+Ctrl+Left workspace prev

# Workspace names
# to display names or symbols instead of plain workspace numbers you can use
# something like: set $ws1 1:mail
#                 set $ws2 2:

set $ws1 1
set $ws2 2
set $ws3 3
set $ws4 4
set $ws5 5
set $ws6 6
set $ws7 7
set $ws8 8
set $ws9 9

# switch to workspace
bindsym $mod+1 workspace $ws1
bindsym $mod+2 workspace $ws2
bindsym $mod+3 workspace $ws3
bindsym $mod+4 workspace $ws4
bindsym $mod+5 workspace $ws5
bindsym $mod+6 workspace $ws6
bindsym $mod+7 workspace $ws7
bindsym $mod+8 workspace $ws8
bindsym $mod+9 workspace $ws9

# Move focused container to workspace
bindsym $mod+Ctrl+1 move container to workspace $ws1
bindsym $mod+Ctrl+2 move container to workspace $ws2
bindsym $mod+Ctrl+3 move container to workspace $ws3
bindsym $mod+Ctrl+4 move container to workspace $ws4
bindsym $mod+Ctrl+5 move container to workspace $ws5
bindsym $mod+Ctrl+6 move container to workspace $ws6
bindsym $mod+Ctrl+7 move container to workspace $ws7
bindsym $mod+Ctrl+8 move container to workspace $ws8
bindsym $mod+Ctrl+9 move container to workspace $ws9

# Move to workspace with focused container
bindsym $mod+Shift+1 move container to workspace $ws1; workspace $ws1
bindsym $mod+Shift+2 move container to workspace $ws2; workspace $ws2
bindsym $mod+Shift+3 move container to workspace $ws3; workspace $ws3
bindsym $mod+Shift+4 move container to workspace $ws4; workspace $ws4
bindsym $mod+Shift+5 move container to workspace $ws5; workspace $ws5
bindsym $mod+Shift+6 move container to workspace $ws6; workspace $ws6
bindsym $mod+Shift+7 move container to workspace $ws7; workspace $ws7
bindsym $mod+Shift+8 move container to workspace $ws8; workspace $ws8
bindsym $mod+Shift+9 move container to workspace $ws9; workspace $ws9

# Open applications on specific workspaces
assign [class="URxvt"] $ws1
assign [class="Google-chrome"] $ws2
assign [class="Pale moon"] $ws2
assign [class="qutebrowser"] $ws2
assign [class="qBittorrent"] $ws9
assign [class="Code"] $ws3
assign [class="Pcmanfm"] $ws4
assign [class="dolphin"] $ws4
assign [class="Spotify"] $ws5
assign [class="Deadbeef"] $ws5
assign [class="TelegramDesktop"] $ws6
assign [class="vlc"] $ws7
assign [class="Gimp"] $ws8

# Open specific applications in floating mode
for_window [title="alsamixer"] floating enable border pixel 1
for_window [class="calamares"] floating enable border normal
for_window [class="Clipgrab"] floating enable
for_window [title="File Transfer*"] floating enable
for_window [class="Galculator"] floating enable border pixel 1
for_window [class="GParted"] floating enable border normal
for_window [title="i3_help"] floating enable sticky enable border normal
for_window [class="Lightdm-settings"] floating enable
for_window [class="Lxappearance"] floating enable sticky enable border normal
for_window [class="Manjaro-hello"] floating enable
for_window [class="Manjaro Settings Manager"] floating enable border normal
for_window [title="MuseScore: Play Panel"] floating enable
for_window [class="Nitrogen"] floating enable sticky enable border normal
for_window [class="Oblogout"] fullscreen enable
for_window [class="octopi"] floating enable
for_window [title="About Pale Moon"] floating enable
for_window [class="Pamac-manager"] floating enable
for_window [class="Pavucontrol"] floating enable
for_window [class="qt5ct"] floating enable sticky enable border normal
for_window [class="Qtconfig-qt4"] floating enable sticky enable border normal
for_window [class="Simple-scan"] floating enable border normal
for_window [class="(?i)System-config-printer.py"] floating enable border normal
for_window [class="Skype"] floating enable border normal
for_window [class="Timeset-gui"] floating enable border normal
for_window [class="(?i)virtualbox"] floating enable border normal
for_window [class="Xfburn"] floating enable

# switch to workspace with urgent window automatically
for_window [urgent=latest] focus

# reload the configuration file
bindsym $mod+Shift+c reload

# restart i3 inplace (preserves your layout/session, can be used to upgrade i3)
bindsym $mod+Shift+r restart

# exit i3 (logs you out of your X session)
bindsym $mod+Shift+e exec "i3-nagbar -t warning -m 'You pressed the exit shortcut. Do you really want to exit i3? This will end your X session.' -b 'Yes, exit i3' 'i3-msg exit'"

# Set shut down, restart and locking features
bindsym $mod+0 mode "$mode_system"
set $mode_system (l)ock, (e)xit, switch_(u)ser, (s)uspend, (h)ibernate, (r)eboot, (Shift+s)hutdown
mode "$mode_system" {
    bindsym l exec --no-startup-id i3exit lock, mode "default"
    bindsym s exec --no-startup-id i3exit suspend, mode "default"
    bindsym u exec --no-startup-id i3exit switch_user, mode "default"
    bindsym e exec --no-startup-id i3exit logout, mode "default"
    bindsym h exec --no-startup-id i3exit hibernate, mode "default"
    bindsym r exec --no-startup-id i3exit reboot, mode "default"
    bindsym Shift+s exec --no-startup-id i3exit shutdown, mode "default"

    # exit system mode: "Enter" or "Escape"
    bindsym Return mode "default"
    bindsym Escape mode "default"
}

# Resize window (you can also use the mouse for that)
bindsym $mod+r mode "resize"
mode "resize" {
        # These bindings trigger as soon as you enter the resize mode
        # Pressing left will shrink the window’s width.
        # Pressing right will grow the window’s width.
        # Pressing up will shrink the window’s height.
        # Pressing down will grow the window’s height.
        bindsym j resize shrink width 5 px or 5 ppt
        bindsym k resize grow height 5 px or 5 ppt
        bindsym l resize shrink height 5 px or 5 ppt
        bindsym semicolon resize grow width 5 px or 5 ppt

        # same bindings, but for the arrow keys
        bindsym Left resize shrink width 10 px or 10 ppt
        bindsym Down resize grow height 10 px or 10 ppt
        bindsym Up resize shrink height 10 px or 10 ppt
        bindsym Right resize grow width 10 px or 10 ppt

        # exit resize mode: Enter or Escape
        bindsym Return mode "default"
        bindsym Escape mode "default"
}


# Autostart applications
exec --no-startup-id /usr/lib/polkit-gnome/polkit-gnome-authentication-agent-1
exec --no-startup-id nitrogen --restore; sleep 1; compton -b
#exec --no-startup-id manjaro-hello
exec --no-startup-id nm-applet
exec --no-startup-id xfce4-power-manager
#exec --no-startup-id pamac-tray
#exec --no-startup-id clipit
exec --no-startup-id blueman-applet
# exec_always --no-startup-id sbxkb
#exec --no-startup-id start_conky_maia
# exec --no-startup-id start_conky_green
exec --no-startup-id xautolock -time 10 -locker blurlock
exec_always --no-startup-id ff-theme-util
exec_always --no-startup-id fix_xcursor

# Color palette used for the terminal ( ~/.Xresources file )
# Colors are gathered based on the documentation:
# https://i3wm.org/docs/userguide.html#xresources
# Change the variable name at the place you want to match the color
# of your terminal like this:
# [example]
# If you want your bar to have the same background color as your 
# terminal background change the line 362 from:
# background #14191D
# to:
# background $term_background
# Same logic applied to everything else.
set_from_resource $term_background background
set_from_resource $term_foreground foreground
set_from_resource $term_color0     color0
set_from_resource $term_color1     color1
set_from_resource $term_color2     color2
set_from_resource $term_color3     color3
set_from_resource $term_color4     color4
set_from_resource $term_color5     color5
set_from_resource $term_color6     color6
set_from_resource $term_color7     color7
set_from_resource $term_color8     color8
set_from_resource $term_color9     color9
set_from_resource $term_color10    color10
set_from_resource $term_color11    color11
set_from_resource $term_color12    color12
set_from_resource $term_color13    color13
set_from_resource $term_color14    color14
set_from_resource $term_color15    color15

# Start i3bar to display a workspace bar (plus the system information i3status if available)
bar {
	i3bar_command i3bar
	status_command i3status
	position bottom
	#position top

## please set your primary output first. Example: 'xrandr --output eDP1 --primary'
#	tray_output primary
#	tray_output eDP1

	bindsym button4 nop
	bindsym button5 nop
#   font xft:URWGothic-Book 11
	strip_workspace_numbers yes

    colors {
        background #222D31
        statusline #F9FAF9
        separator  #454947

#                      border  backgr. text
        focused_workspace  #F9FAF9 #16a085 #292F34
        active_workspace   #595B5B #353836 #FDF6E3
        inactive_workspace #595B5B #222D31 #EEE8D5
        binding_mode       #16a085 #2C2C2C #F9FAF9
        urgent_workspace   #16a085 #FDF6E3 #E5201D
    }
}

# hide/unhide i3status bar
bindsym $mod+m bar mode toggle

# Theme colors
# class                   border  backgr. text    indic.   child_border
  client.focused          #556064 #556064 #80FFF9 #FDF6E3
  client.focused_inactive #2F3D44 #2F3D44 #1ABC9C #454948
  client.unfocused        #2F3D44 #2F3D44 #1ABC9C #454948
  client.urgent           #CB4B16 #FDF6E3 #1ABC9C #268BD2
  client.placeholder      #000000 #0c0c0c #ffffff #000000 

  client.background       #2B2C2B

#############################
### settings for i3-gaps: ###
#############################

# Set inner/outer gaps
gaps inner 14
gaps outer -2

# Additionally, you can issue commands with the following syntax. This is useful to bind keys to changing the gap size.
# gaps inner|outer current|all set|plus|minus <px>
# gaps inner all set 10
# gaps outer all plus 5

# Smart gaps (gaps used if only more than one container on the workspace)
smart_gaps on

# Smart borders (draw borders around container only if it is not the only container on this workspace) 
# on|no_gaps (on=always activate and no_gaps=only activate if the gap size to the edge of the screen is 0)
smart_borders on

# Press $mod+Shift+g to enter the gap mode. Choose o or i for modifying outer/inner gaps. Press one of + / - (in-/decrement for current workspace) or 0 (remove gaps for current workspace). If you also press Shift with these keys, the change will be global for all workspaces.
set $mode_gaps Gaps: (o) outer, (i) inner
set $mode_gaps_outer Outer Gaps: +|-|0 (local), Shift + +|-|0 (global)
set $mode_gaps_inner Inner Gaps: +|-|0 (local), Shift + +|-|0 (global)
bindsym $mod+Shift+g mode "$mode_gaps"

mode "$mode_gaps" {
        bindsym o      mode "$mode_gaps_outer"
        bindsym i      mode "$mode_gaps_inner"
        bindsym Return mode "default"
        bindsym Escape mode "default"
}
mode "$mode_gaps_inner" {
        bindsym plus  gaps inner current plus 5
        bindsym minus gaps inner current minus 5
        bindsym 0     gaps inner current set 0

        bindsym Shift+plus  gaps inner all plus 5
        bindsym Shift+minus gaps inner all minus 5
        bindsym Shift+0     gaps inner all set 0

        bindsym Return mode "default"
        bindsym Escape mode "default"
}
mode "$mode_gaps_outer" {
        bindsym plus  gaps outer current plus 5
        bindsym minus gaps outer current minus 5
        bindsym 0     gaps outer current set 0

        bindsym Shift+plus  gaps outer all plus 5
        bindsym Shift+minus gaps outer all minus 5
        bindsym Shift+0     gaps outer all set 0

        bindsym Return mode "default"
        bindsym Escape mode "default"
}



# my changes
bindsym $mod+shift+x exec --no-startup-id blurlock
#bindsym $mod+p exec pcmanfm
bindsym $mod+p exec dolphin
bindsym $mod+g exec gimp
bindsym $mod+shift+v exec code
#bindsym $mod+c exec google-chrome
bindsym $mod+c exec qutebrowser 
bindsym $mod+shift+z exec urxvt -e vim
bindsym $mod+shift+f exec urxvt -e ranger
bindsym $mod+shift+t exec telegram-desktop
bindsym $mod+shift+i exec qbittorrent
bindsym $mod+shift+p exec urxvt -e poweroff
bindsym $mod+shift+o exec urxvt -e reboot
bindsym $mod+shift+n exec spotify
bindsym $mod+shift+m exec deadbeef
bindsym $mod+d exec rofi -show run -lines 4 -eh 2 -width 100 -padding 500

#exec urxvt
#exec urxvt -e vim 
#exec urxvt -e ranger
#exec urxvt -e xrandr --output DP1 --auto --output DP1 --auto --right-of eDP1
#exec code
#exec pcmanfm
#exec deadbeef

```

<a name=".Xresourcesfile"></a>
### .Xresources file

```bash
Xft.dpi:       96
Xft.antialias: true
Xft.hinting:   true
Xft.rgba:      rgb
Xft.autohint:  false
Xft.hintstyle: hintslight
Xft.lcdfilter: lcddefault

XTerm*background:        #222D31
XTerm*foreground:        #d8d8d8
XTerm*pointerColor:      #1ABB9B
XTerm*faceName:          Fixed
XTerm*faceSize:          11
XTerm*reverseVideo:      on
XTerm*selectToClipboard: true

*background:                      #222D31
*foreground:                      #d8d8d8
*fading:                          8
*fadeColor:                       black
*cursorColor:                     #1ABB9B
*pointerColorBackground:          #2B2C2B
*pointerColorForeground:          #16A085

!! black dark/light
*color0:                          #222D31
*color8:                          #585858

!! red dark/light
*color1:                          #ab4642
*color9:                          #ab4642

!! green dark/light
*color2:                          #7E807E
*color10:                         #8D8F8D

!! yellow dark/light
*color3:                          #f7ca88
*color11:                         #f7ca88

!! blue dark/light
*color4:                          #7cafc2
*color12:                         #7cafc2

!! magenta dark/light
*color5:                          #ba8baf
*color13:                         #ba8baf

!! cyan dark/light
*color6:                          #1ABB9B
*color14:                         #1ABB9B

!! white dark/light
*color7:                          #d8d8d8
*color15:                         #f8f8f8

Xcursor.theme: xcursor-breeze
Xcursor.size:                     0

URxvt.font:                       9x15,xft:TerminessTTFNerdFontMono

! alternative font settings with 'terminus':
! URxvt.font:      -xos4-terminus-medium-r-normal--16-160-72-72-c-80-iso10646-1
! URxvt.bold.font: -xos4-terminus-bold-r-normal--16-160-72-72-c-80-iso10646-1
!! terminus names see end of file!

URxvt.depth:                      32
URxvt.background:                 [100]#222D31
URxvt*scrollBar:                  false
URxvt*mouseWheelScrollPage:       false
URxvt*cursorBlink:                true
URxvt*background:                 black
URxvt*foreground:                 grey
URxvt*saveLines:                  5000
URxvt.background:                 [80]#000000

! for 'fake' transparency (without Compton) uncomment the following three lines
! URxvt*inheritPixmap:            true
! URxvt*transparent:              true
! URxvt*shading:                  138

! Normal copy-paste keybindings without perls
URxvt.iso14755:                   false
URxvt.keysym.Shift-Control-V:     eval:paste_clipboard
URxvt.keysym.Shift-Control-C:     eval:selection_to_clipboard
!Xterm escape codes, word by word movement
URxvt.keysym.Control-Left:        \033[1;5D
URxvt.keysym.Shift-Control-Left:  \033[1;6D
URxvt.keysym.Control-Right:       \033[1;5C
URxvt.keysym.Shift-Control-Right: \033[1;6C
URxvt.keysym.Control-Up:          \033[1;5A
URxvt.keysym.Shift-Control-Up:    \033[1;6A
URxvt.keysym.Control-Down:        \033[1;5B
URxvt.keysym.Shift-Control-Down:  \033[1;6B
! Rxvt.perl-ext-common:             ...,clipboard
! URxvt.keysym.M-C-c:               perl:clipboard:copy
! URxvt.keysym.M-v:                 perl:clipboard:paste
! URxvt.keysym.M-C-v:               perl:clipboard:paste_escaped
! URxvt*termName:                   string
! URxvt*geometry:                   geometry
! URxvt*chdir:                      string
! URxvt*loginShell:                 boolean
! URxvt*multiClickTime:             number
! URxvt*jumpScroll:                 boolean
! URxvt*skipScroll:                 boolean
! URxvt*pastableTabs:               boolean
! URxvt*scrollstyle:                plain
! URxvt*scrollBar_right:            boolean
! URxvt*scrollBar_floating:         true
! URxvt*scrollBar_align:            mode
! URxvt*thickness:                  number
! URxvt*scrollTtyOutput:            boolean
! URxvt*scrollTtyKeypress:          boolean
! URxvt*scrollWithBuffer:           boolean
! URxvt*tintColor:                  !7DA55
! URxvt*blurRadius:                 HxV
! URxvt*fading:                     number
! URxvt*fadeColor:                  color
! URxvt*utmpInhibit:                boolean
! URxvt*urgentOnBell:               boolean
! URxvt*visualBell:                 boolean
! URxvt*mapAlert:                   boolean
! URxvt*meta8:                      boolean
! URxvt*tripleclickwords:           boolean
! URxvt*insecure:                   boolean
! URxvt*cursorUnderline:            boolean
! URxvt*pointerBlank:               boolean
! URxvt*color0:                     color
! URxvt*color1:                     color
! URxvt*color2:                     color
! URxvt*color3:                     color
! URxvt*color4:                     color
! URxvt*color5:                     color
! URxvt*color6:                     color
! URxvt*color7:                     color
! URxvt*color8:                     color
! URxvt*color9:                     color
! URxvt*color10:                    color
! URxvt*color11:                    color
! URxvt*color12:                    color
! URxvt*color13:                    color
! URxvt*color14:                    color
! URxvt*color15:                    color
! URxvt*colorBD:                    color
! URxvt*colorIT:                    color
! URxvt*colorUL:                    color
! URxvt*colorRV:                    color
! URxvt*underlineColor:             color
! URxvt*scrollColor:                color
! URxvt*troughColor:                color
! URxvt*highlightColor:             color
! URxvt*highlightTextColor:         color
! URxvt*cursorColor:                color
! URxvt*cursorColor2:               color
! URxvt*pointerColor:               color
! URxvt*pointerColor2:              color
! URxvt*borderColor:                color
! URxvt*iconFile:                   file
! URxvt*font:                       fontname
! URxvt*boldFont:                   fontname
! URxvt*italicFont:                 fontname
! URxvt*boldItalicFont:             fontname
! URxvt*intensityStyles:            boolean
! URxvt*inputMethod:                name
! URxvt*preeditType:                style
! URxvt*imLocale:                   string
! URxvt*imFont:                     fontname
! URxvt*title:                      string
! URxvt*iconName:                   string
! URxvt*buffered:                   boolean
! URxvt*depth:                      number
! URxvt*visual:                     number
! URxvt*transient-for:              windowid
! URxvt*override-redirect:          boolean
! URxvt*hold:                       boolean
! URxvt*externalBorder:             number
! URxvt*internalBorder:             number
! URxvt*borderLess:                 true
! URxvt*lineSpace:                  number
! URxvt*letterSpace:                number
! URxvt*skipBuiltinGlyphs:          boolean
! URxvt*pointerBlankDelay:          number
! URxvt*backspacekey:               string
! URxvt*deletekey:                  string
! URxvt*print-pipe:                 string
! URxvt*modifier:                   modifier
! URxvt*cutchars:                   string
! URxvt*answerbackString:           string
! URxvt*secondaryScreen:            boolean
! URxvt*secondaryScroll:            boolean
! URxvt*perl-lib:                   string
! URxvt*perl-eval:                  perl-eval
! URxvt*perl-ext-common:            string
! URxvt*perl-ext:                   string
! URxvt*iso14755:                   boolean
! URxvt*iso14755_52:                boolean
! URxvt*xrm:                        string
! URxvt*keysym.sym:                 keysym
! URxvt*background.border:          boolean
! URxvt*background.expr:            string
! URxvt*background.interval:        seconds
! URxvt*bell-command:               string
! URxvt*kuake.hotkey:               string
! URxvt*matcher.button:             string
! URxvt*matcher.launcher:           string
! URxvt*matcher.launcher.*:         string
! URxvt*matcher.pattern.*:          string
! URxvt*matcher.rend.*:             string
! URxvt*remote-clipboard.fetch:     string
! URxvt*remote-clipboard.store:     string
! URxvt*searchable-scrollback:      string
! URxvt*selection-autotransform.*:  string
! URxvt*selection-pastebin.cmd:     string
! URxvt*selection-pastebin.url:     string
! URxvt*selection.pattern-0:        string
! URxvt*tab-bg:                     colour
! URxvt*tab-fg:                     colour
! URxvt*tabbar-bg:                  colour
! URxvt*tabbar-fg:                  colour
! URxvt*url-launcher:               string

! The Terminus font uses the following X-names:
! -xos4-terminus-medium-r-normal--12-120-72-72-c-60-iso10646-1
! -xos4-terminus-medium-r-normal--14-140-72-72-c-80-iso10646-1
! -xos4-terminus-medium-r-normal--16-160-72-72-c-80-iso10646-1
! -xos4-terminus-medium-r-normal--20-200-72-72-c-100-iso10646-1
! -xos4-terminus-medium-r-normal--22-220-72-72-c-110-iso10646-1
! -xos4-terminus-medium-r-normal--24-240-72-72-c-120-iso10646-1
! -xos4-terminus-medium-r-normal--28-280-72-72-c-140-iso10646-1
! -xos4-terminus-medium-r-normal--32-320-72-72-c-160-iso10646-1
! -xos4-terminus-bold-r-normal--12-120-72-72-c-60-iso10646-1
! -xos4-terminus-bold-r-normal--14-140-72-72-c-80-iso10646-1
! -xos4-terminus-bold-r-normal--16-160-72-72-c-80-iso10646-1
! -xos4-terminus-bold-r-normal--20-200-72-72-c-100-iso10646-1
! -xos4-terminus-bold-r-normal--24-240-72-72-c-120-iso10646-1
! -xos4-terminus-bold-r-normal--28-280-72-72-c-140-iso10646-1
! -xos4-terminus-bold-r-normal--32-320-72-72-c-160-iso10646-1

rofi.color-enabled: true
rofi.color-window: #A6222227
rofi.color-normal: #273238, #c1c1c1, #273238, #394249, #ffffff
rofi.color-active: #273238, #80cbc4, #273238, #394249, #80cbc4
rofi.color-urgent: #273238, #ff1844, #273238, #394249, #ff1844
```

<a name="31_hold_shift"></a>
### 31 hold shift

```bash
#! /bin/sh
set -e

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"
source "${datarootdir}/grub/grub-mkconfig_lib"

found_other_os=

make_timeout () {

  if [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then 
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
    verbose=
      else
    verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
    cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
    cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}

  adjust_timeout

    cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
```



<a name="archpackages"></a>
### arch packages

###### Try to install all <span style="color:Green"> *__pacman__*</span> packages as <span style="color:Green"> **_root_**</span> so you won't type sudo & your passcode every time you have to install package  

###### <span style="color:Red">**NEVER** </span> install <span style="color:Red"> **AUR**</span> packages as <span style="color:Red">*root*</span> or <span style="color:Red">*sudo* </span>

>update & upgrade packages
```bash
pacman -Suyy
```
---

> Replace dmenu with rofi
```bash
pacman -S rofi
#goto /home/anteneh/.i3/config & add 
bindsym $mod+d exec rofi -show run -lines 4 -eh 2 -width 100 -padding 300
#comment 
#bindsym $mod+d exec dmenu
#goto /home/anteneh/.Xresources & add
rofi.color-enabled: true
rofi.color-window: #A6222227
rofi.color-normal: #273238, #c1c1c1, #273238, #394249, #ffffff
rofi.color-active: #273238, #80cbc4, #273238, #394249, #80cbc4
rofi.color-urgent: #273238, #ff1844, #273238, #394249, #ff1844
```
---
>URXVT transparent 
```bash
#goto /home/anteneh/.Xresources & add
URxvt.background:                 [80]#000000
```
---

>Dolphin
```bash
pacman -S dolphin
#select no. 1
```
---

>pip
```bash
pacman -S python-pip
```
---

>sound driver
```bash
pacman -S pulseaudio pulseaudio-alsa pulseaudio-bluetooth pulseaudio-equalizer pulseaudio-jack pulseaudio-lirc pulseaudio-zeroconf
```
---

>Microcode
```bash
#for intel processors with grub bootloader
pacman -S intel-ucode
grub-mkconfig -o /boot/grub/grub.cfg
#for AMD processors install linux-firmware package
pacman -S linux-firmware
```
---

>Disable GRUB delay NOTE only if YOUDONT DUAL BOOT
```bash
#add the following lines to the file /etc/default/grub to achieve the fastest possible boot
sudo vim /etc/default/grub
#add this line & save & exit
GRUB_FORCE_HIDDEN_MENU="true"
#create a file called 31_hold_shift copy & past the text from the link into to 31_hold_shift & then move 31_hold_shift to /etc/grub.d/
vim 31_hold_shift
sudo mv 31_hold_shift /etc/grub.d/
#make it executable, and regenerate the grub configuration & reboot to see the changes
sudo chmod a+x /etc/grub.d/31_hold_shift
sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo reboot
#so to see grub menu you need to hold shift during the startup
```
---
[31_hold_shift.sh](https://raw.githubusercontent.com/AntenehDev/Arch-i3/master/31_hold_shift.sh "31_hold_shift.sh")


>QEMU/KVM
```bash
pacman -S qemu virt-manager
systemctl enable libvirtd.service
systemctl start libvirtd.service
```
---

>vscode
```bash
yaourt -S visual-studio-code-bin --noconfirm
```
---

>Qbittorrent
```bash
pacman -S qbittorrent
```
---

>Audacity
```bash
pacman -S audacity
```
---

>Deadbeef
```bash
pacman -S deadbeef
```
---

>SimpleScreenRecroder
```bash
pacman -S simplescreenrecorder
```
---

>OBS Studio
```bash
pacman -S obs-studio
```
---

>Cheese
```bash
pacman -S cheese
```
---

>Spotify & Blockify
```bash
yaourt -S spotify --noconfirm
yaourt -S blockify --noconfirm
```
---

>Java JDK
```bash
yaourt -S jdk --noconfirm
sudo archlinux-java set java-11-jdk
yaourt -S jre --noconfirm
sudo archlinux-java set java-10-jre/jre
sudo archlinux-java set java-11-jdk
archlinux-java status
java --version
```
---

>ADB
```bash
pacman -S android-tools android-udev
```
---

>Google chrome
```bash
yaourt -S google-chrome --noconfirm
```
---

>ungoogled-chromium
```bash
yaourt -S ungoogled-chromium --noconfirm
```
---
 
>YouTube-dl
```bash
pacman -S youtube-dl
```
---

>UMLET (like viso)
```bash
yaourt -S umlet --noconfirm
```
---

>Pycharm Community Edition
```bash
pacman -S pycharm-community-edition
```
---

>SublimeText
```bash
yaourt -S sublime-text-dev --noconfirm
```
---

>Slack
```bash
yaourt -S slack-desktop --noconfirm
```
---

>Android Studio
```bash
yaourt -S android-studio --noconfirm
```
---

>Virtualbox
```bash
uname -r 
#download virtualbox that matches your linux kernel
pacman -S virtualbox
modprobe -a vboxdrv
```
---

>Genymotion
```bash
yaourt -S genymotion --noconfirm
```
---

>Easytag
```bash
pacman -S easytag
```
---

>LMMS
```bash
pacman -S lmms
```
---


>Blender
```bash
pacman -S blender
```
---

>Inkscape
```bash
pacman -S inkscape
```
---

>Corebird
```bash
pacman -S corebird 
```
---

>FeedReader
```bash
pacman -S feedreader
```
---

>FileZilla
```bash
pacman -S filezilla
```
---

>Firefox Developer Edition
```bash
pacman -S firefox-developer-edition
```
---

>PuTTY
```bash
pacman -S putty
```
---

>Telegram Desktop
```bash
pacman -S telegram-desktop
```
---

>Zenmap
```bash
pacman -S nmap 
```
---

>Wireshark
```bash
pacman -S wireshark-qt
```
---

>Node
```bash
pacman -S nodejs
```
---

>check node version
```bash
node -v
node --version
```
---

>npm
```bash
pacman -S npm
```
---

>check npm version
```bash
npm --version
#OR
npm -v  #but most of the time it won't work
```
---

>Angular CLI
```bash
npm install -g @angular/cli
npm new app-name
#OR
ng new app-name --minimal	#if you don't want the test files
cd app-name
ng serve
#OR
ng serve --open   #the --open (or just -o) option automatically opens your browser to http://localhost:4200/
```
---

>Check angular version
```bash
ng --version
#OR 
ng -v	#but most of the time it won't work
```
---

>Ionic & Cordova
```bash
npm install -g ionic cordova
#config ionic
cd Documents/Dev
mkdir ionic
cd ionic
ionic start testapp blank
No
n
cd testapp && ionic serve
#OR
cd ./testapp
```
---

>WPS-office
```bash
cd Downloads
git clone https://aur.archlinux.org/wps-office.git
cd wps-office
yaourt -S libpng12 --noconfirm #only if it ask for dependency
makepkg
su
ls   #copy & paste the pkg file called wps-office_10.1.0.6757-1-x86_64.pkg.tar
pacman -U wps-office_10.1.0.6757-1-x86_64.pkg.tar
```
---

>Start bluetooth if not working
```bash
systemctl start bluetooth.service
systemctl enable bluetooth.service
```
---

>DB Browser for sqlite
```bash
pacman -S sqlitebrowser
```
---

>PostgreSQL
```bash
pacman -S postgresql
```
---

>Cisco packet tracer
```bash
yaourt -S packettracer61 --noconfirm
```
---

>Pavucontrol to control sound b/n laptop & TV(through HDMI) also other apps
```bash
pacman -S pavucontrol 
```
---

>Qutebrowser
```bash
pacman -S qutebrowser
```
---

>Remove orphans
```bash
pacman -Rns $(pacman -Qtdq)
```
---

>ffmpeg convert video
```bash
ffmpeg -i sample.mkv sampleConvert.mp4
```
---

>Dimension of your screen 
```bash
xdpyinfo | grep dimensions 
```
---

>Record screen
```bash
ffmpeg -y -f x11grab -s 1600x900 -i :0.0 recOut.mkv
```
---

>List webcam
```bash
ls /dev
#video0 is webcam 
```
---

>Record webcam
```bash
ffmpeg -y -i /dev/video0 recOut.mkv 
```
---

>Record audio & video
```bash
ffmpeg -y -f x11grab -s 1600x900 -i :0.0 -f alsa -i default recOut.mkv
```
---

>Record audio only
```bash
ffmpeg -y -f alsa -i default recOut.mkv 
```
---

>scrpy 
```bash
#install adb 
yaourt scrcpy --noconfirm
#OR
yaourt scrcpy-prebuiltserver --noconfirm 
#plug an Android device, and execute
scrcpy
#if it didn't work try using the lower resolution/bitrate with the parameters scrcpy -b2M -m800
scrcpy -b2M -m800
#if several devices are listed in adb devices, you must specify the serial
scrcpy -s 0123456789abcdef
#to show physical touches while scrcpy is running
scrcpy -t
#switch fullscreen mode
Ctrl+f
#Goto HOME screen
Ctrl+h | Middle-click
#Go BACK
Ctrl+b | Right-clickx2
#APP_SWITCH
Ctrl+s
#Goto MENU
Ctrl+m
#VOLUME_UP
Ctrl+↑ (up)
#VOLUME_DOWN 	
Ctrl+↓ (down)
#POWER 	
Ctrl+p
#turn screen on 	
Right-click²
#paste computer clipboard to device 	
Ctrl+v
#enable/disable FPS counter (on stdout) 	
Ctrl+i
#install APK from computer 	
#drag & drop APK file
```
<a name="hdmiscript"></a>
### hdmi script

```bash
#!/bin/sh
xrandr --output HDMI1 --mode 1920x1080 --pos 0x0 --rotate normal --output VIRTUAL1 --off --output eDP1 --primary --mode 1600x900 --pos 1920x0 --rotate normal
```
