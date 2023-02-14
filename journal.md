## 14 Feb 2023 - 18:17 - rbrown

Realised that, given we don't plan on making YaST installation media we probably dont need all the 000* stuff..removed all mention of it from previous journal entries to keep this readable

Created a greybeard-release package in OBS WebUI
 * https://build.opensuse.org/package/new/home:RBrownSUSE:Greybeard
 * Checked it out on my machine - `osc co home:RBrownSUSE:Greybeard:greybeard-release`
 * `cd home:RBrownSUSE:Greybeard/greybeard-release`
 * Created greybeard-release.spec using https://build.opensuse.org/package/view_file/home:RBrownSUSE:microos-desktop/000package-groups/MicroOS-release.spec.in?expand=1 for inspiration, but removing anything which I suspect in YaST/SUSE Product specific
 * Package is doing the bare minimum, providing the 'Provides' that should everything should need, setting the welcome on the terminal, defining the os-release, and of course putting the distros LICENSE in full on the system
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
