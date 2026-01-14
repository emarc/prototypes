# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a UI prototype for Vaadin DevTools - a developer tools interface for the Vaadin web framework. The project is intentionally minimal: a single `index.html` file with inline JavaScript and CSS.

## Development Approach

**Critical constraint**: Keep everything in a single `index.html` file with inline JS/CSS. External resources (icons, etc.) should be loaded from CDNs only.

## Architecture

The prototype has these components:

1. **Base View** - A mock address form simulating a Vaadin application (styling not important)
2. **Configuration Bar** - Top bar for selecting interaction variants (not part of the form)
3. **Activation Button** - Floating button in lower-right indicating DevMode is active
4. **Toolbar** - Expands from activation button, shows mode-dependent tools
5. **Mode System** - Three modes: Edit, Inspect, Test

### Modes and Their Tools

Store mode configuration in inline JSON. Each mode has:
- A set of available tools
- Selection or interaction mode
- Read-only or read/write access

| Mode | Selection/Interaction | Access | Tools |
|------|----------------------|--------|-------|
| Edit | Selection | Read/Write | Outline, Palette, Properties, Log |
| Inspect | Selection | Read-only | Outline, Properties, Log, Info, Feature flags |
| Test | Interaction | Read-only | Test recorder, Info, Feature flags, Log |

### Selection vs Interaction Mode

- **Selection mode**: Blocks app interaction; clicks select components for inspection/editing
- **Interaction mode**: App functions normally; DevTools observe without blocking

### Global Tools

Available via menu icon: user impersonation, feedback, DevMode settings.

## Key Design Decisions

- Activation button interactions: (a) click activates last mode, (b) hover shows mode selector and config menu
- Tools are primarily icons that open panels (stub as icons initially)
- Mode selector appears in toolbar near activation button

## Reference

See `AGENTS.md` for the complete prototype specification.
