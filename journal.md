## 23 Feb 2023 - rebrown

Merged Maurizio's port of mod-firstboot - want to improve it but it's good enough meanwhile
Also merged Maurizio's theme for SwayNC - no improvements needed

Next steps
* Tweak firstboot
* Tweak window theme to have less blue (Greys/monochrome with transparency to show wallpaper is tempting)

## 21 Feb 2023 - rbrown

Getting annoyed with testing in a VM (hardware acceleration needed for sway testing), so trying real hardware
* Realised nmtui isn't installed but is needed by jeos-firstboot, added to patterns-greybeard
* added distrobox + podman to patterns-greybeard
* added distrobox to default greybeard sway config with keybinding Mod+Shift+Enter (akin to terminal being Mod+Enter)
* added transactional-update-notifier

Next steps - not much left now
* Firstboot wizard - install flatpaks as --user by default, not system wide, find a nice way of introducing beginners to sway (keyboard shortcuts and such)

## 20 Feb 2023 - rbrown

Lots of work on https://github.com/ProjectGreybeard/branding by m4u9
Nicely packaged using a git \_service file in OBS https://build.opensuse.org/package/view_file/home:RBrownSUSE:Greybeard/branding-greybeard/\_service?expand=1

Testing the latest image and making tweaks
* Latest bug https://github.com/ProjectGreybeard/bugs/issues/6

## 17 Feb 2023 - rbrown

Tested first image with sway, but pattern is obvious incomplete, added more required packages

## 16 Feb 2023 - rbrown

Testing first image (Basic non-GUI MicroOS rebranded as Greybeard). Mostly perfect, but still installs grub2-branding-openSUSE and doesn't include the gpg key for the greybeard repo by default
 * Addressed key with https://build.opensuse.org/package/rdiff/home:RBrownSUSE:Greybeard/greybeard?linkrev=base&rev=10
 * Address grub2-branding with https://build.opensuse.org/package/rdiff/home:RBrownSUSE:Greybeard/branding-greybeard?linkrev=base&rev=9

Created jeos-firstboot module for creating the user on firstboot
 * https://build.opensuse.org/package/show/home:RBrownSUSE:Greybeard/jeos-firstboot-module-user

Next Steps
 * Add sway and config into skel so it works

## 15 Feb 2023 - rbrown

Created branding-greybeard in OBS WebUI
 * https://build.opensuse.org/package/new/home:RBrownSUSE:Greybeard
 * Checked it out on my machine - `osc co home:RBrownSUSE:Greybeard:branding-greybeard`
 * `cd home:RBrownSUSE:Greybeard/branding-greybeard`
 * Created .spec using https://build.opensuse.org/package/view_file/Base:System/branding-openSUSE/branding-openSUSE.spec?expand=1 as inspiration, but dramatically smaller as we have far less to worry about
 * Threw together a quick wallpaper in GIMP
 * `osc add` everything so far and checked in, it builds, though at this point it's useless - that's fine, will add to it as the pattern comes together and it becomes obvious what needs 'branding'

Created patterns-greybeard in OBS WebUI
 * https://build.opensuse.org/package/new/home:RBrownSUSE:Greybeard
 * Checked it out on my machine - `osc co home:RBrownSUSE:Greybeard:patterns-greybeard`
 * `cd home:RBrownSUSE:Greybeard/patterns-greybeard`
 * Created .spec using https://build.opensuse.org/package/view_file/devel:microos/patterns-microos/patterns-microos.spec?expand=1 as inspiration, but dramatically smaller as we have far less to worry about
 * `osc add` everything so far and checked in, it builds, though at this point it's useless - that's fine, will add to i
t as the pattern comes together

Created greybeard in OBS WebUI
 * https://build.opensuse.org/package/new/home:RBrownSUSE:Greybeard
 * Checked it out on my machine - `osc co home:RBrownSUSE:Greybeard:greybeard`
 * `cd home:RBrownSUSE:Greybeard/greybeard`
 * Created .kiwi using https://build.opensuse.org/package/view_file/devel:microos:images/openSUSE-MicroOS/openSUSE-MicroOS.kiwi?expand=1 as inspiration, but dramatically smaller as we have far less to worry about
 * `osc add` everything so far and checked in, it builds, though at this point it's useless beyond basic boot testing

Opened first bugs
 * https://github.com/ProjectGreybeard/bugs/issues/1 - Might not fix
 * https://github.com/ProjectGreybeard/bugs/issues/2 - fixed with https://build.opensuse.org/package/rdiff/home:RBrownSUSE:Greybeard/greybeard-release?linkrev=base&rev=7

Next Steps
 * Test the image and fix the obvious issues that are bound to be found
 * Add contents to the pattern to start actually making it a graphical desktop system

## 14 Feb 2023 - 18:17 - rbrown

Realised that, given we don't plan on making YaST installation media we probably dont need all the 000* stuff..removed all mention of it from previous journal entries to keep this readable

Created a greybeard-release package in OBS WebUI
 * https://build.opensuse.org/package/new/home:RBrownSUSE:Greybeard
 * Checked it out on my machine - `osc co home:RBrownSUSE:Greybeard:greybeard-release`
 * `cd home:RBrownSUSE:Greybeard/greybeard-release`
 * Created greybeard-release.spec using https://build.opensuse.org/package/view_file/home:RBrownSUSE:microos-desktop/000package-groups/MicroOS-release.spec.in?expand=1 for inspiration, but removing anything which I suspect in YaST/SUSE Product specific
 * Package is doing the bare minimum, providing the 'Provides' that should everything should need, setting the welcome on the terminal, defining the os-release, and of course putting the distros LICENSE in full on the system
 * Checked it in `osc ci`
 * Watched the build and made a few minor tweaks till it worked
 * https://build.opensuse.org/package/view_file/home:RBrownSUSE:Greybeard/greybeard-release/greybeard-release.spec

so the -release package is made..next steps are now
 * creating a branding-greybeard package
 * creating a patterns-greybeard package to be where most of the magic will happen
 * creating our first greybeard image, most likely based on the "SelfInstall" image from [openSUSE-MicroOS](https://build.opensuse.org/package/view_file/openSUSE:Factory/openSUSE-MicroOS/openSUSE-MicroOS.kiwi?expand=1) - I want to avoid YaST and the associated skelcd-\*, installation-images work, especially as that would require forking installation-images to support this not-openSUSE distro we're building

## 14 Feb 2023 - 14:55 - rbrown

Created initial OBS Project [home:RBrownSUSE:Greybeard](https://build.opensuse.org/project/show/home:RBrownSUSE:Greybeard)
 * Used OBS WebUI - https://build.opensuse.org/project/new

Configured [Project Meta](https://build.opensuse.org/projects/home:RBrownSUSE:Greybeard/meta) using OBS WebUI
 * *standard* build target duplicating the role of openSUSE:Factory standard where all RPMs are built
 * *images* build target for building installation images from home:RBrownSUSE:Greybeard
 * The above names could be anything, just used the above to copy openSUSE:Factory
 * x86_64 only for starters, aarch64 maybe someday

Configured [Project Config](https://build.opensuse.org/projects/home:RBrownSUSE:Greybeard/prjconf) using OBS WebUI
 * *images* repo needs to be defined as a kiwi repo, to build kiwi images

Next steps
 * creating a greybeard-release package
 * creating a branding-greybeard package
 * creating a patterns-greybeard package to be where most of the magic will happen
 * creating our first greybeard image, most likely based on the "SelfInstall" image from [openSUSE-MicroOS](https://build.opensuse.org/package/view_file/openSUSE:Factory/openSUSE-MicroOS/openSUSE-MicroOS.kiwi?expand=1) - I want to avoid YaST and the associated skelcd-\*, installation-images work, especially as that would require forking installation-images to support this not-openSUSE distro we're building

## 14 Feb 2023 - 14:12 - rbrown

Created https://github.com/ProjectGreybeard/, wrote initial [README](https://github.com/ProjectGreybeard/Info/blob/main/README.md)
