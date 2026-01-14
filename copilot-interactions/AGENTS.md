# Vaadin DevTools prototype
This is a quick interaction prototype for Vaadin DevTools.

It is importnat that this is kept as a stand-alone single index.html with inline javascript and CSS; potentially loading icons and such from external CDNs.

## Base
The base view is an address form with a few text fields and buttons. This is just there to give an impressoion if an unelying Vaadin application. Styling is not important.

There is a top bar, not part of the form, that is for configuring the prototype; choose with interaction variant we're trying out.

## The Activation Button
There is a floating button in the lower right. This is the main item indicating that the application is running in DevMode and where we activate all other DevMode things.

We'll explore mutiple options for interactions.

First:
a) Only click to activate, last mode (see below) is activated.
b) Click to activate last mode, but additionally hover shows the mode selector and global/config menu.

## The Toolbar
The toolbar expands from the activation button, exposing a set of tools that can be used when activated from the DevMode button. Mainly the tools are icons opening panels with fuctionality, but for now that can be stubbed out as icons only.

The set of tools shown in the toolbar depends on the Mode activated.

## Modes
Modes adjust the tools available depending on the task at hand, to start with "Edit", "Inspect" and "Test".

Modes are chosen with a mode selector in the toolbar close to the activation button, indicated by icon, and affect 1) the tools shown in the toolbar, 2) wether or not the application is in "selection" or "interaction" mode, and 3) whether or not all features are read-only or read/write.

Configuratoin of modes should be stored in a "json" (inline) to easily be configured.

Example tools:
- Edit (selection mode, read/write): Outline, Palette, Properties, Log
- Inspect (selection mode, read-only): Outline, Properties, Log, Info, Feature flags
- Test: (interaction mode): Test recorder, Info, Feature flags, Log

## Selection vs Interaction mode
When DevTools is in a "selection" mode, interaction with the underlying app is blocked, and instead the clicked component is selected, so that properties can be shown etc.

In "interaction" mode the app functions normally, but has the DevMode tools shown, which can include panels sugh as log and test recorder etc, that just observe (potentially writing test scripts etc, but generally not modifying the app code),

## Global / config tools
There are also a number of features globally available, such as user impersonation, feedback, and DevMode settings. Theses show up in a menu (behind an icon), at least for now.