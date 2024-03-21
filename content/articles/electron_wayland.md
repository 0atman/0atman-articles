---
{}
---

As I mentioned, this env var:

ELECTRON_OZONE_PLATFORM_HINT = "auto";


Makes electron apps scale properly under Wayland.

What it does is tells electron to render them in Wayland natively, not using xwayland as a wrapper. This allows highdpi to work without blurring.

HOWEVER, there is a subtle bug in obsidian's version of electron (and Discord's, and some others maybe) that causes the "drop" js event to misfire. In obsidian, this only effects reordering of tabs and splits with mouse, as far as I can see, I didn't notice it for weeks.

Test your apps using it set to auto, if they work, great, they'll use less battery and render clearer text.
If some don't work, you can selectively change it for just those apps, of course.

But specifically for obsidian, I've got it rendering natively normally, and for the rare times I need to re-order tabs (I have multiple layouts preset) I launch it with this alias, make my tweaks, then go back to native:

alias fixobsidian='ELECTRON_OZONE_PLATFORM_HINT=""  OBSIDIAN_USE_WAYLAND=1 obsidian -enable-features=UseOzonePlatform'


If you don't use high-dpi scaling, like I don't on my desktop, it's probably a good idea to NOT set this, and let all electron apps run inside xwayland for now. But I set it on my laptop, where I *do* run resolution scaling.

However, I may decide to throw all this away and just not use global resolution scaling on my laptop, tbh.

Electron has fixed it in the latest release, but apps lag *years* behind those, as upgrading electron breaks many things, which is annoying for app creators.

I bet https://tauri.app (the rust electron replacement) doesn't have this problem XD
