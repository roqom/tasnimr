---
layout: post
title: "Why you should still install Ruby on macOS, even though it comes pre-installed (for development)"
date: 2025-07-28
permalink: /macOSruby/
---

f you are using macOS, then Ruby is pre-installed in your system.

However, if you want to develop a web app using the Ruby language, you still need to install Ruby via Homebrew. 

"Ok, but why? Why do I need to install Ruby again?"

Because the pre-installed Ruby in macOS is for system-level tasks, it is not meant for personal development use. In other words, there are some tools that your MacBook is running under the hood, using Ruby scripts, such as Xcode, Command Line Tools, and System Configuration, among others. 

This pre-installed Ruby is: 

- Outdated – to ensure macOS system compatibility 

- Read-only – you will face a permission issue when installing Ruby gems like Rails. 

- Can mess with system files – If you insist on installing gems globally with macOS system Ruby, you might cause problems with macOS tools that rely on Ruby. 

If you want to use Ruby, it is best to install it separately from the pre-installed Ruby. 

How do you install? Via a package manager called Homebrew. 

Think of a package manager like the Apple App Store, but for code and tools. 

Instead of downloading and installing software manually, a package manager, like installing an app in the App Store, (1) knows where to get software (called “packages”), (2) handles dependencies (what that software needs to work), and (3) makes updating/uninstalling clean and simple.

Here's a side-by-side breakdown between App Store and Homebrew:

| Feature | App Store | Homebrew |
| ----------- | ----------- | ----------- |
| Purpose | Install graphical apps (with icons, windows, UIs) like Pages, Zoom, GarageBand | Install command-line tools, developer libraries, and servers (like Git, Ruby, PostgreSQL) |
| Interface | GUI (point-and-click) | Terminal (you type commands) |
| Audience | Regular users | Developers, power users |
| Examples | Slack, Final Cut Pro, Xcode, Evernote | git, node, ruby, wget, mysql, ffmpeg  |
| Where apps go | /Applications | /opt/homebrew or /usr/local |
| How to install | Open App Store → Search → Click Install | brew install <tool-name> |
| Auto updates | Managed by macOS | You run brew update && brew upgrade |
| App type | GUI/desktop apps | CLI (command-line interface) tools |
