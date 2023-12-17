# macOS

## Clean install

You can clean install by going to Recovery mode (restart with `cmd+r` pressed). Then Disk Utility > Select disk > Erase (Format it) > Close Disk Utility > Select option Reinstall MacOS (Choose macOS ver. to install).

## Notes

- In save dialogues I can press these keys:
  - `Return` or `⌘ + S` = Save
  - `ESC` = Cancel
- I can also press `/` or `~` to quickly go to some directory from a save dialogue. And I can press `⌘ + ↑` to go to `parent directory`.
- Recovery mode: Power off the machine, press the power button and immediately hold Cmd-R.
- [Both Windows and MacOS are at a point where clean installs are unnecessary.](https://www.reddit.com/r/MacOS/comments/90g4h9/is_it_worth_the_effort_to_do_a_clean_install_of/)
  - I can appreciate someone wanting to do a clean install if they've installed and removed many apps and just want to clear out everything spread around all the system and hidden folders, even if it doesn't really affect performance and won't save a ton of disk space. There is something cathartic about a clean install.
- `/usr/local/bin` is a good place to put raw binaries available in the path, that are not installed with Nix.
- [`defaults write NSGlobalDomain KeyRepeat -int 1` setup keyboard repeat.](https://twitter.com/jordwalke/status/1230582824224165888)
- [Can select text from middle of link's text by holding down alt while you drag and select with the mouse](https://twitter.com/MBoffin/status/1218668903586394112)
- [plutil tool support the generation of Swift or Objective-C code directly from plists. For example: plutil -convert swift.](https://twitter.com/dmartincy/status/1295029196503351298)
- [To code sign binaries ad hoc, run `codesign -s - <path_to_binary>`.](https://github.com/golang/go/issues/42684) This will give users a gatekeeper warning but they could still run the binary. To sign so users can run binary without warning, you need Apple developer account.
- [I basically install nothing except GUI apps on my Mac. I don’t even have a bashrc (or any shell rc for that matter). I never open the terminal on Mac. I live in the VM for dev work, and use GUI apps like calendar, email, messages, browser, etc. on Mac.](https://twitter.com/mitchellh/status/1449151623092060164)
- [`ls -lha /Library/Developer/CommandLineTools/usr/bin` to see what xcode command line developer tools installs.](https://twitter.com/nikitonsky/status/1453019511502909441)
- [Can right-click on a 2-factor authentication code to set it up with iCloud Keychain.](https://twitter.com/rafahari/status/1456013646144933893)
- [macOS has network quality command: networkQuality](https://twitter.com/justsitandgrin/status/1460286405578563595) ([Reddit](https://www.reddit.com/r/MacOS/comments/qxa933/builtin_network_bandwidth_test_tool_on_macos/))
- [Just because a root certificate is in the built-in iOS/macOS trust store doesn't mean that it is trusted. Apple applies additional constraints via configuration updates to maintain a high-level of security.](https://twitter.com/BasileBailey/status/1494801237694300161)
- [Things I immediately do when setting up a new Mac: 1. Turn off all system notifications. 2. Turn off autocorrect. 3. Set ⌘-V to "Paste and Match Style" to remove formatting.](https://twitter.com/davidhoang/status/1572591216470130694)
- [For MacOS, you need to disable AirPlay to make 5000 available. System Preference > Sharing > uncheck AirPlay Receiver.](https://github.com/thangchung/go-coffeeshop/issues/16)

## Code

### macOS Defaults

```bash
# Remove dock animation. https://www.reddit.com/r/apple/comments/6xg9xq/tip_of_the_day_one_thing_i_cant_live_without_in/
defaults write com.apple.dock autohide-delay -int 0
defaults write com.apple.dock autohide-time-modifier -float 0.4
killall Dock

# Revert
defaults delete com.apple.dock autohide-delay
defaults delete com.apple.dock autohide-time-modifier
killall Dock
```

```bash
# Turn internal keyboard off. https://discussions.apple.com/thread/5044946?answerId=26556362022#26556362022
sudo kextunload /System/Library/Extensions/AppleUSBTopCase.kext/Contents/PlugIns/AppleUSBTCKeyboard.kext/

# Turn internal keyboard on
sudo kextload /System/Library/Extensions/AppleUSBTopCase.kext/Contents/PlugIns/AppleUSBTCKeyboard.kext/
```

## Applications to Install

# Brew

[Homebrew](https://brew.sh/)

## Installation

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

## Links

- [macOS developer tutorials](https://www.raywenderlich.com/category/macos)
- [A Pro’s Guide to the Best Secret Mac Features](https://matthewpalmer.net/blog/2018/04/14/ultimate-pro-guide-best-secret-mac-features/index.html)
- [macOS open source](https://opensource.apple.com/)
- [macOS Security and Privacy Guide](https://github.com/drduh/macOS-Security-and-Privacy-Guide)
- [Quick Look plugins](https://github.com/sindresorhus/quick-look-plugins)
- [Objective-See](https://www.objective-see.com/) - Simple, yet effective macOS security tools.
- [Curated list of shell commands and tools specific to macOS](https://github.com/herrbischoff/awesome-macos-command-line)
- [The new Mac Pro is a design remix (2019)](https://www.arun.is/blog/mac-pro/)
- [BlockBlock](https://www.objective-see.com/products/blockblock.html) - Continually monitors common persistence locations and displays an alert whenever a persistent component is added to the OS.
- [Impact](https://github.com/ChimeHQ/Impact) - Crash detection and recording library for Apple platforms.
- [Designing LookUp for macOS (2019)](https://medium.com/lookup-design/designing-lookup-for-macos-bf5b8fea1a01)
- [macOS screenshot tips](https://twitter.com/CoreyGinnivan/status/1187209574303973376)
- [Open-source components of macOS](https://github.com/apple-open-source/macos)
- [AppMover](https://github.com/OskarGroth/AppMover) - Framework for moving your application bundle to Applications folder on launch.
- [Lilu](https://github.com/acidanthera/Lilu) - Arbitrary kext and process patching on macOS.
- [osx-hid-inspector](https://github.com/pqrs-org/osx-hid-inspector) - Command line tool for macOS for inspecting human input devices (HID).
- [macOS Kernel Extensions are officially deprecated](https://developer.apple.com/support/kernel-extensions/) ([HN](https://news.ycombinator.com/item?id=22251076))
- [mas-cli](https://github.com/mas-cli/mas) - Simple command line interface for the Mac App Store. Designed for scripting and automation.
- [apply-user-defaults](https://github.com/zero-sh/apply-user-defaults) - Small utility to set macOS user defaults declaratively from a YAML file.
- [Zero.sh](https://github.com/zero-sh/zero.sh) - Radically simple personal bootstrapping tool for macOS.
- [DefaultApp](https://tyler.io/default-app-for-mac-ios/) - Template for starting macOS projects. ([Code](https://github.com/tylerhall/DefaultApp)) ([HN](https://news.ycombinator.com/item?id=22582456))
- [Awesome macOS](https://github.com/iCHAIT/awesome-macOS)
- [macOS and iOS Security Related Tools](https://github.com/ashishb/osx-and-ios-security-awesome)
- [BlackHole](https://github.com/ExistentialAudio/BlackHole) - Modern MacOS virtual audio driver that allows applications to pass audio to other applications with zero additional latency.
- [xcnotary](https://github.com/akeru-inc/xcnotary) - Missing macOS app notarization helper, built with Rust. ([HN](https://news.ycombinator.com/item?id=22743659))
- [skhd](https://github.com/koekeishiya/skhd) - Simple hotkey daemon for macOS.
- [Proxy Audio Driver](https://github.com/briankendall/proxy-audio-device) - Virtual audio driver for macOS to sends all audio to another output.
- [Icons.app](https://github.com/SAP/macOS-icon-generator) - App for macOS which is designed to generate consistent sized icons of an existing application in various states, jiggling (shaking) etc.
- [OpenCore](https://dortania.github.io/OpenCore-Desktop-Guide/) - Open-source, unconventional, first-in-class piece of software designed to intercept kernel loading to insert a highly advanced rootkit, designed to be an alternative to Clover. ([Code](https://github.com/dortania/OpenCore-Desktop-Guide)) ([HN](https://news.ycombinator.com/item?id=22916281))
- [Creating a macOS App with SwiftUI](https://developer.apple.com/tutorials/swiftui/creating-a-macos-app)
- [Syphon](https://github.com/Syphon/Syphon-Framework) - macOS technology to allow applications to share video and still images with one another in realtime, instantly.
- [Mac Bare Metal](https://flow.swiss/mac-bare-metal) - Enterprise-class IaaS for macOS.
- [React Native for macOS](https://github.com/microsoft/react-native-macos) - Build native macOS apps with React. ([HN](https://news.ycombinator.com/item?id=23160075))
- [macOS defaults](https://macos-defaults.com/) - List of macOS defaults commands with demos. ([Code](https://github.com/yannbertrand/macos-defaults))
- [macOS Setup Guide](https://sourabhbajaj.com/mac-setup/) ([Code](https://github.com/sb2nov/mac-setup))
- [MacHack](https://github.com/kendfinger/MacHack) - List of built-in tools in macOS that you probably didn't know about.
- [SplitConfigurations](https://github.com/KevinGutowski/SplitConfigurations) - Up the basics of a Big Sur app layout. Includes splitview and toolbarItems.
- [Mathias Bynens' Sensible macOS Defaults](https://github.com/mathiasbynens/dotfiles/blob/master/.macos) ([HN](https://news.ycombinator.com/item?id=26513528))
- [xhyve](https://github.com/machyve/xhyve) - Lightweight macOS virtualization solution.
- [Declarative macOS configuration options (2021)](https://lobste.rs/s/q8qgr7/any_advice_on_declarative_macos)
- [macOS scripts](https://github.com/0xmachos/macos-scripts) - Various scripts for macOS tasks.
- [Pure Rust Implementation of Apple Code Signing (2021)](https://gregoryszorc.com/blog/2021/04/14/pure-rust-implementation-of-apple-code-signing/)
- [Apple’s Notarizing](https://www.cdfinder.de/guide/blog/apple_hell.html) ([HN](https://news.ycombinator.com/item?id=26993857))
- [macOS dev setup](https://github.com/donnemartin/dev-setup)
- [Lima](https://github.com/AkihiroSuda/lima) - Linux-on-Mac ("macOS subsystem for Linux", "containerd for Mac"). ([HN](https://news.ycombinator.com/item?id=27151993))
- [Inspect Apple macOS software updates](https://github.com/hjuutilainen/sus-inspector)
- [MacVM](https://github.com/KhaosT/MacVM) - MacOS VM for Apple Silicon using Virtualization API.
- [My 2021 New Mac Setup](https://www.swyx.io/new-mac-setup-2021/)
- [macOS extensions are moving away from the kernel (2021)](https://eclecticlight.co/2021/07/07/extensions-are-moving-away-from-the-kernel/) ([HN](https://news.ycombinator.com/item?id=27758181))
- [iOS and macOS Performance Tuning Book (2017)](https://www.oreilly.com/library/view/ios-and-macostm/9780133085501/)
- [node-mac-permissions](https://github.com/codebytere/node-mac-permissions) - Native node module to manage system permissions on macOS.
- [Swift Programming for macOS](https://gavinw.me/swift-macos/) ([Code](https://github.com/wigging/swift-macos))
- [Organize and Index Your Screenshots (OCR) on macOS (2021)](https://alexn.org/blog/2020/11/11/organize-index-screenshots-ocr-macos.html)
- [The journey to controlling external monitors on M1 Macs (2021)](https://alinpanaitiu.com/blog/journey-to-ddc-on-m1-macs/) ([HN](https://news.ycombinator.com/item?id=28011861))
- [dyld-shared-cache-extractor](https://github.com/keith/dyld-shared-cache-extractor) - CLI for extracting libraries from Apple's dyld shared cache file.
- [ArchTest](https://github.com/below/ArchTest) - Why does this not compile on Apple Silicon?
- [The macOS Sandbox File Limit (2021)](https://buckleyisms.com/blog/anecdotes-about-the-macos-sandbox-file-limit/) ([HN](https://news.ycombinator.com/item?id=28105814))
- [Asahi Linux for Apple M1 progress report, August 2021](https://asahilinux.org/2021/08/progress-report-august-2021/) ([HN](https://news.ycombinator.com/item?id=28180135))
- [macOS 11's hidden security improvements (2021)](https://blog.malwarebytes.com/mac/2021/08/macos-11s-hidden-security-improvements/) ([HN](https://news.ycombinator.com/item?id=28250340))
- [Santa](https://github.com/google/santa) - Binary authorization system for macOS. ([Docs](https://santa.dev/))
- [Rudolph](https://github.com/airbnb/rudolph) - Control server counterpart of Santa, and is used to rapidly deploy configurations to Santa agents.
- [macOS persistence – Beyond the good ol' LaunchAgents](https://theevilbit.github.io/beyond/) ([HN](https://news.ycombinator.com/item?id=28498058))
- [macOS Security Compliance](https://github.com/usnistgov/macos_security) - Open source effort to provide a programmatic approach to generating security guidance.
- [Apple M1 Exploration](https://drive.google.com/file/d/1WrMYCZMnhsGP4o3H33ioAUKL_bjuJSPt/view)
- [WhatsNewViewController](https://github.com/Jonathan-Gander/WhatsNewViewController) - Nice way to present your new app features.
- [diskspace](https://github.com/scriptingosx/diskspace) - macOS command line tool to return the available disk space on APFS volumes.
- [PlayCover](https://github.com/iVoider/PlayCover) - Run iOS apps & games on M1 Mac with mouse, keyboard and controller support.
- [Sideload iOS apps regardless of security settings](https://github.com/EricRabil/m1-ios-sideloader)
- [node-mac-userdefaults](https://github.com/codebytere/node-mac-userdefaults) - Native Node.js module that provides an interface to the user’s defaults database on macOS.
- [Resources about macOS/iOS system security](https://github.com/houjingyi233/macOS-iOS-system-security)
- [asitop](https://github.com/tlkh/asitop) - Performance monitoring CLI tool for Apple Silicon. ([Web](https://tlkh.github.io/asitop/))
- [macOS Optimizer](https://github.com/sickcodes/osx-optimizer) - Shell scripts to speed up your mac boot time, accelerate loading, and prevent unnecessary throttling.
- [Setup a New Developer Computer](https://github.com/vendasta/setup-new-computer-script) ([HN](https://news.ycombinator.com/item?id=29535432))
- [macFUSE](https://github.com/osxfuse/osxfuse) - Allows you to extend macOS via third party file systems.
- [Tuning Your Code’s Performance for Apple Silicon](https://developer.apple.com/documentation/apple-silicon/tuning-your-code-s-performance-for-apple-silicon) ([HN](https://news.ycombinator.com/item?id=29719544))
- [macOS Setup after 15 Years of Linux (2021)](https://hookrace.net/blog/macos-setup/) ([HN](https://news.ycombinator.com/item?id=29742551))
- [Infinite Mac](https://system7.app/)
- [apple-tools](https://github.com/meme/apple-tools) - Collection of tools for working with Apple software/hardware.
- [macOS tips and tricks](https://saurabhs.org/macos-tips)
- [Hardening macOS (2022)](https://www.bejarano.io/hardening-macos/) ([HN](https://news.ycombinator.com/item?id=31864974))
- [PlayCover](https://github.com/PlayCover/PlayCover) - Run iOS apps and games on Apple Silicon Macs with mouse, keyboard and controller support.
- [Completely Open-Source Implementation of Apple Code Signing and Notarization (2022)](https://gregoryszorc.com/blog/2022/08/08/achieving-a-completely-open-source-implementation-of-apple-code-signing-and-notarization/) ([HN](https://news.ycombinator.com/item?id=32386762))
- [macOS Hardening](https://github.com/beerisgood/macOS_Hardening)
- [macOS notes](https://github.com/slavaim/mac-notes)
- [All of the sounds in macOS Big Sur](https://github.com/ThisIsNoahEvans/BigSurSounds)
- [Lightweight Alpine VMs on macOS](https://beringresearch.github.io/macpine/) ([HN](https://news.ycombinator.com/item?id=33769274)) ([Code](https://github.com/beringresearch/macpine))
- [The Impossible Port: MacOS (2022)](https://blog.ryujinx.org/the-impossible-port-macos/) ([Lobsters](https://lobste.rs/s/acbp3c/impossible_port_macos))
- [Cilicon](https://github.com/traderepublic/Cilicon) - Self-Hosted macOS CI on Apple Silicon.
- [Awesome macOS Command Line](https://git.herrbischoff.com/awesome-macos-command-line/about/) ([HN](https://news.ycombinator.com/item?id=33896513))
- [Hacking with macOS](https://www.hackingwithswift.com/store/hacking-with-macos) ([Code](https://github.com/twostraws/macOS))
- [Prefsniff](https://github.com/zcutlip/prefsniff) - Utility to sniff preferences changes to macOS plist files.
- [Remove animation on unhiding macOS dock](https://twitter.com/Gavmn/status/1633953059071234048)
- [macOS Cursors](https://mac-cursors.netlify.app/) ([Code](https://github.com/daviddarnes/mac-cursors)) ([HN](https://news.ycombinator.com/item?id=35238906))
- [Keyboard tricks from a macOS app dev (2023)](https://notes.alinpanaitiu.com/Keyboard%20tricks%20from%20a%20macOS%20app%20dev) ([HN](https://news.ycombinator.com/item?id=35678269))
- [macOS Internals](https://gist.github.com/kconner/cff08fe3e0bb857ea33b47d965b3e19f) ([HN](https://news.ycombinator.com/item?id=35847715))
- [Diving into a secret macOS tool - networkQuality (2023)](https://cyberhost.uk/the-hidden-macos-speedtest-tool-networkquality/) ([HN](https://news.ycombinator.com/item?id=35936999))
- [Eighty Shades of Option Key](https://getenet.notion.site/Eighty-Shades-of-Option-Key-3c6e58feb5c848ee9d4c027f0b9d52e0)
