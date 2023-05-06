### Based on 0.4.0-1 from Debian 11, i just clean-up right-click menu, no more patches

# LXTerminal

LXTerminal is a VTE-based terminal emulator with support for multiple tabs.  It
is completely desktop-independent and does not have any unnecessary
dependencies. In order to reduce memory usage and increase the performance all
instances of the terminal are sharing a single process.

### How to repeat:

```
sudo apt install devscripts --no-install-recommends
apt source lxterminal
apt build-dep lxterminal
cd lxterminal

your-favorite-text-editor ./src/lxterminal.c
```
found 

/* Descriptors for popup menu items, accessed via right click on the terminal. */
static GtkActionEntry vte_menu_items[] =
{
    { "VTEMenu", NULL, "VTEMenu" },
    { "NewWindow", "list-add", N_("New _Window"), NULL, "New Window", G_CALLBACK(terminal_new_window_activate_event) },
    { "NewTab", "list-add", N_("New _Tab"), NULL, "New Tab", G_CALLBACK(terminal_new_tab_activate_event) },
    { "Sep1", NULL, "Sep" },
    { "OpenURL", NULL, N_("Open _URL"), NULL, "Open URL", G_CALLBACK(terminal_open_url_activate_event) },
    { "CopyURL", NULL, N_("Copy _URL"), NULL, "Copy URL", G_CALLBACK(terminal_copy_url_activate_event) },
    { "Copy", "edit-copy", N_("Cop_y"), NULL, "Copy", G_CALLBACK(terminal_copy_activate_event) },
    { "Paste", "edit-paste", N_("_Paste"), NULL, "Paste", G_CALLBACK(terminal_paste_activate_event) },
    { "Clear", NULL, N_("Cl_ear scrollback"), NULL, "Clear scrollback", G_CALLBACK(terminal_clear_activate_event) },
    { "Sep2", NULL, "Sep" },
    { "Preferences", "system-run", N_("Preference_s"), NULL, "Preferences", G_CALLBACK(terminal_preferences_dialog) },
    { "Sep3", NULL, "Sep" },
    { "NameTab", "dialog-information", N_("Na_me Tab"), NULL, "Name Tab", G_CALLBACK(terminal_name_tab_activate_event) },
    { "PreviousTab", "go-previous", N_("Pre_vious Tab"), NULL, "Previous Tab", G_CALLBACK(terminal_previous_tab_activate_event) },
    { "NextTab", "go-next", N_("Ne_xt Tab"), NULL, "Next Tab", G_CALLBACK(terminal_next_tab_activate_event) },
    { "Tabs_MoveTabLeft", NULL, N_("Move Tab _Left"), NULL, "Move Tab Left", G_CALLBACK(terminal_move_tab_left_activate_event) },
    { "Tabs_MoveTabRight", NULL, N_("Move Tab _Right"), NULL, "Move Tab Right", G_CALLBACK(terminal_move_tab_right_activate_event) },
    { "CloseTab", "window-close", N_("_Close Tab"), NULL, "Close Tab", G_CALLBACK(terminal_close_tab_activate_event) }
};

and remove any string that you want

and build:
```
dch -l local '99.build6'
dpkg-source --commit
debuild -us -uc

sudo dpkg -i ../lxterminal_*local*.deb
```

Yes, you shuldn't trust random guy from the internet
