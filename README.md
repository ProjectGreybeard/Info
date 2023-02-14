# What is Project Greybeard?

Greybeard is an **EXPERIMENTAL** Project based on [openSUSE MicroOS Desktop](https://en.opensuse.org/Portal:MicroOS/Desktop)

The Project's headline goal is to provide an immutable, automatically updating, graphical linux workstation that targets commandline/window-manager centric users aka those old-school "Greybeard" Linux users who dislike modern GNOME, KDE, etc and would prefer something akin to i3.

If MicroOS is the perfect OS for servers, and MicroOS Desktop is the perfect OS for non-technical/lazy developer users, then Greybeard should appeal those who want all the benefits of an immutable base OS, but still a fully customisable, if incredibly geeky, window-manager environment

# Which window manager will Project Greybeard use?

The goal is to provide a clean but customised [Sway](https://swaywm.org/) environment. It will be more customised than vanilla upstream Sway, but also provide less out of the box than [openSUSEway](https://en.opensuse.org/Portal:OpenSUSEway) which, in our opinion, goes further than we'd like to for Greybeard.

# Will Greybeard require Flatpaks for graphical applications?

Like MicroOS Desktop, flatpaks will be the recommended way of installing additional graphical applications on Greybeard, with [flathub](https://flathub.org) configured out of the box.

Also like MicroOS Desktop, the recommended way of installing non-flatpak graphical apps and/or non-graphical applications will be via [distrobox](https://github.com/89luca89/distrobox), which will be integrated out of the box.

However, unlike the MicroOS Desktop where customising the base OS is discoraged, Greybeard recognises that users of window managers like Sway need to be able to add additional tooling into the base OS to customise their sway environment. This will be supported, hopefully with tooling to help track deviations from the baseline Greybeard installation.

# Will Greybeard require reboots to install packages/system updates?

Applications installed via flatpaks or distrobox will not require the system to reboot before they can be used, and should immediately show in Sways application launcher.

Any packages (such as additional window-manager components) will need to be installed via [transactional-update](https://manpages.opensuse.org/Tumbleweed/transactional-update/transactional-update.8.en.html) which will require a reboot to take effect. This is to ensure that if anything goes wrong, your system+wm environment can easily return to how it last worked.

System Updates will be entirely automated, with transactional-update automatically running in the background, notifying in your graphical environment when there is an update ready to apply with a reboot. Just like MicroOS Desktop there will be no scheduled reboots configured out of the box.

# How 'minimal' will Project Greybeard installations be?

Like MicroOS Desktop, Greybeard aims to be 'small' while still 'usable' out of the box. Greybeard should be able to do everything the MicroOS Desktop can, but maybe not as easily.

Like all MicroOS varients, Greybeard will not install OS packages using zyppers *recommends* feature, so the basic installation should be trim and stay that way.

Unlike MicroOS Desktop, Greybeard users are expected to be somewhat technical, so some 'nice to have but not necessary' features may be intentionally avoided to keep the system as trim as possible. For example Greybeard is not expected to use a graphical login manager, with users expecting to login via a regular plain text TTY and Sway starting (automatically?) once they've logged in. 

# What additional goals does Project Greybeard have?

As an experimental effort, Greybeard also hopes to stand as a reproducible example as how to build custom derivatives of openSUSE MicroOS or MicroOS Desktop. Therefore all the steps taken to build Greybeard will be recorded in our [journal](https://github.com/ProjectGreybeard/Info/blob/main/journal.md) for others to follow along and copy/adapt for their own use.

Once we've built working images/installers for the very developer-centric window-manager use case, we may also experiment on a varient of Greybeard for more 'kiosk' like use, loading up an immutable base and running a single graphical application automatically.

# Is Project Greybeard an openSUSE Project?

No, at this time this project is entirely seperate and unassociated with openSUSE, openSUSE MicroOS and other openSUSE Projects. This may change if these experiments prove popular.

# Who can contribute to Project Greybeard?

Anyone, as long as you agree with the general premise of the Project as described above.

This is an intentionally opinionated project and we do not wish to waste our time with endless debates adjusting the scope of what we set out to do. We do not wish to dramatically increase the scope of this Project just to draw in more contributors.

That said, we recognise we don't know everything, so if you have opinions as to how you think we can best fufill our goals, please follow along our [journal](https://github.com/ProjectGreybeard/Info/blob/main/journal.md) and start contributing!
