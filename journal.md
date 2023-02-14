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
 * bootstrapping a basic product definition, akin to 000product, 000release-packages and 000package-groups in openSUSE:Factory
 * configuring/running [pkglistgen](http://osrt.opensuse.org/docs/pkglistgen.html) against 000package-groups once it's made. This is especially important as we're based on Tumbleweed/MicroOS so the package lists will change outside of our control. pkglistgen expected to run from a container on my server at home for now, easier from a secrets/security aspect
 * creating a patterns-greybeard package to be where most of the magic will happen
 * creating our first greybeard image, most likely based on the "SelfInstall" image from [openSUSE-MicroOS](https://build.opensuse.org/package/view_file/openSUSE:Factory/openSUSE-MicroOS/openSUSE-MicroOS.kiwi?expand=1) - I want to avoid YaST and the associated skelcd-\*, installation-images work, especially as that would require forking installation-images to support this not-openSUSE distro we're building

## 14 Feb 2023 - 14:12 - rbrown

Created https://github.com/ProjectGreybeard/, wrote initial [README](https://github.com/ProjectGreybeard/Info/blob/main/README.md)
