# Immich Kiosk
Immich Kiosk is a lightweight slideshow for running on kiosk devices and browsers that uses Immich as a data source.


[Demo](http://demo.immichkiosk.app) - [Documentation](http://docs.immichkiosk.app)

## Key features
- Lightweight, responsive frontend for smooth performance.
- Display random images from your Immich collection, or curate specific albums and people.
- Fully customizable appearance with flexible transitions.
- Add a live clock with adjustable formats.
- Define default settings for all devices through environment variables or YAML config files.
- Configure device-specific settings using URL parameters.

> This project is not affiliated with Immich

## Requirements
- A reachable Immich server that is running version **v3.2.0** or above.
- A browser from [this supported list](https://browserslist.dev/?q=PiAwLjIl) or higher.

## Changing settings via URL
If you want a more personalized configuration, you can configure settings for individual devices through the URL.
Use the integrated URL Builder: 
`http://your-immich-kiosk-app-url/url-builder`

> You need to enable it in the app config form, when needed. *(URLs provided stays valid anyway)*

## Configuration
If you want to change your default configuration, you can edit the `config.yaml` in the app-data directory.
Check the [docs](https://docs.immichkiosk.app/configuration/) for details

### Problem after Update ?
Sometimes Immich Kiosk updates bring changes to the syntax of its config file.
To fix this, two situations:
 1. You have edited your Immich Kiosk `config.yaml`in the app-data:
    - Check the [release notes](https://github.com/damongolding/immich-kiosk/releases) and adapt your config file
 
 2. You didn't edit anything outside Runtipi WebUI for this app:
    - From this app page: Click on the **three dots** -> **Reset app** *(your config file will be replaced by the newest one)*
