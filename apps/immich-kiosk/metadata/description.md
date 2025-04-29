# Immich Kiosk
Immich Kiosk is a lightweight slideshow for running on kiosk devices and browsers that uses Immich as a data source.

## Key features
- Lightweight, responsive frontend for smooth performance.
- Display random images from your Immich collection, or curate specific albums and people.
- Fully customizable appearance with flexible transitions.
- Add a live clock with adjustable formats.
- Define default settings for all devices through environment variables or YAML config files.
- Configure device-specific settings using URL parameters.

## Requirements
- A reachable Immich server that is running version v1.127.0 or above.
- A browser from [this supported list](https://browserslist.dev/?q=PiAwLjIl) or higher.

## Changing settings via URL
You can configure settings for individual devices through the URL. This feature is particularly useful when you need different settings for different devices, especially if the only input option available is a URL, such as with kiosk devices.

Example:

`https://{URL}?refresh=120&background_blur=false&transition=none`

The above would set refresh to 120 seconds (2 minutes), turn off the background blurred image and remove all transitions for this device/browser.

------

## Configuration
Edit `config.yaml` in app-data directory.

| **yaml**                          | **ENV**                 | **Value**                  | **Default** | **Description**                                                                            |
|-----------------------------------|-------------------------|----------------------------|-------------|--------------------------------------------------------------------------------------------|
| show_time                         | KIOSK_SHOW_TIME         | bool                       | false       | Display clock.                                                                             |
| time_format                       | KIOSK_TIME_FORMAT       | 24 \| 12                   | 24          | Display clock time in either 12 hour or 24 hour format. Can either be 12 or 24.            |
| show_date                         | KIOSK_SHOW_DATE         | bool                       | false       | Display the date.                                                                          |
| date_format                       | KIOSK_DATE_FORMAT       | string                     | DD/MM/YYYY  | The format of the date. default is day/month/year |
| clock_source                      | KIOSK_CLOCK_SOURCE      | client \| server           | client      | The source of the clock. Either client or server.                                          |
| refresh                           | KIOSK_REFRESH           | int                        | 60          | The amount in seconds a image will be displayed for.                                       |
| disable_screensaver             | KIOSK_DISABLE_SCREENSAVER | bool                       | false       | Ask browser to request a lock that prevents device screens from dimming or locking. NOTE: I haven't been able to get this to work constantly on IOS. |
| optimize_images                   | KIOSK_OPTIMIZE_IMAGES   | bool                       | false       | Whether Kiosk should resize images to match your browser screen dimensions for better performance. NOTE: In most cases this is not necessary, but if you are accessing Kiosk on a low-powered device, this may help. |
| use_gpu                           | KIOSK_USE_GPU           | bool                       | true        | Enable GPU acceleration for improved performance (e.g., CSS transforms) |
| show_archived                     | KIOSK_SHOW_ARCHIVED     | bool                       | false       | Allow assets marked as archived to be displayed.                                           |
| album                  | KIOSK_ALBUM             | string                   |           | The ID(s) of a specific album or albums you want to display.|
| album_order       | KIOSK_ALBUM_ORDER       | random \| newest \| oldest | random  | The order an album's assets will be displayed.|
| excluded_albums | KIOSK_EXCLUDED_ALBUMS  | string                   |          | The ID(s) of a specific album or albums you want to exclude. |
| experimental_album_video | KIOSK_EXPERIMENTAL_ALBUM_VIDEO  | bool | false | Enable experimental video playback for albums. |
| person                 | KIOSK_PERSON            | string                   |          | The ID(s) of a specific person or people you want to display. |
| excluded_people | KIOSK_EXCLUDED_PEOPLE   | string                  |        | The ID(s) of a specific person or people you want to exclude. |
| date               | KIOSK_DATE              | []string                   | []          | A date range or ranges. |
| tag                      | KIOSK_TAG               | string                   |          | Tag or tags you want to display. |
| memories                          | KIOSK_MEMORIES          | bool                       | false       | Display memories. |
| blacklist                         | KIOSK_BLACKLIST         | []string                   | []          | The ID(s) of any specific assets you want Kiosk to skip/exclude from displaying. You can also tag assets in Immich with "kiosk-skip" to achieve the same. |
| date_filter          | KIOSK_DATE_FILTER       | string                     | ""          | Filter person and random assets by date. |
| disable_navigation               | KIOSK_DISABLE_NAVIGATION | bool                       | false       | Disable all Kiosk's navigation (touch/click, keyboard and menu).    |
| disable_ui                        | KIOSK_DISABLE_UI        | bool                       | false       | A shortcut to set show_time, show_date, show_image_time and image_date_format to false.    |
| frameless                         | KIOSK_FRAMELESS         | bool                       | false       | Remove borders and rounded corners on images.                                              |
| hide_cursor                       | KIOSK_HIDE_CURSOR       | bool                       | false       | Hide cursor/mouse via CSS.                                                                 |
| font_size                         | KIOSK_FONT_SIZE         | int                        | 100         | The base font size for Kiosk. Default is 100% (16px). DO NOT include the % character.      |
| background_blur                   | KIOSK_BACKGROUND_BLUR   | bool                       | true        | Display a blurred version of the image as a background.                                    |
| background_blur_amount            | KIOSK_BACKGROUND_BLUR_AMOUNT | int                   | 10          | The amount of blur to apply to the background image (sigma).                               |
| theme                  | KIOSK_THEME             | fade \| solid              | fade        | Which theme to use. |
| layout                | KIOSK_LAYOUT            | single \| portrait \| landscape \| splitview \| splitview-landscape | Which layout to use. |
| sleep_start      | KIOSK_SLEEP_START       | string                     | ""          | Time (in 24hr format) to start sleep mode. |
| sleep_end        | KIOSK_SLEEP_END         | string                     | ""          | Time (in 24hr format) to end sleep mode. |
| disable_sleep      | N/A                     | bool                       | false       | Bypass sleep mode by adding `disable_sleep=true` to the URL. |
| custom_css        | N/A                     | bool                       | true        | Allow custom CSS to be used.         |
| transition                        | KIOSK_TRANSITION        | none \| fade \| cross-fade | none        | Which transition to use when changing images.                                              |
| fade_transition_duration          | KIOSK_FADE_TRANSITION_DURATION | float               | 1           | The duration of the fade (in seconds) transition.                                          |
| cross_fade_transition_duration    | KIOSK_CROSS_FADE_TRANSITION_DURATION | float         | 1           | The duration of the cross-fade (in seconds) transition.                                    |
| show_progress                     | KIOSK_SHOW_PROGRESS     | bool                       | false       | Display a progress bar for when image will refresh.                                        |
| image_fit         | KIOSK_IMAGE_FIT         | contain \| cover \| none   | contain     | How your image will fit on the screen. Default is contain. |
| image_effect   | KIOSK_IMAGE_EFFECT      | none \| zoom \| smart-zoom | none        | Add an effect to images.                                                                   |
| image_effect_amount | KIOSK_IMAGE_EFFECT_AMOUNT | int                  | 120         | Set the intensity of the image effect. Use a number between 100 (minimum) and higher, without the % symbol. |
| use_original_image                | KIOSK_USE_ORIGINAL_IMAGE | bool                      | false       | Use the original image. NOTE: If the original is not a png, gif, jpeg or webp Kiosk will fallback to using the preview. |
| show_album_name                   | KIOSK_SHOW_ALBUM_NAME   | bool                       | false       | Display album name(s) that the asset appears in.                                           |
| show_person_name                  | KIOSK_SHOW_PERSON_NAME  | bool                       | false       | Display person name(s).                                                                    |
| show_image_time                   | KIOSK_SHOW_IMAGE_TIME   | bool                       | false       | Display image time from METADATA (if available).                                           |
| image_time_format                 | KIOSK_IMAGE_TIME_FORMAT | 12 \| 24                   | 24          | Display image time in either 12 hour or 24 hour format. Can either be 12 or 24.            |
| show_image_date                   | KIOSK_SHOW_IMAGE_DATE   | bool                       | false       | Display the image date from METADATA (if available).                                       |
| image_date_format | KIOSK_IMAGE_DATE_FORMAT | string                     | DD/MM/YYYY  | The format of the image date. default is day/month/year. | show_image_description            | KIOSK_SHOW_IMAGE_DESCRIPTION    | bool               | false       | Display image description from METADATA (if available). |
| show_image_exif                   | KIOSK_SHOW_IMAGE_EXIF           | bool               | false       | Display image Fnumber, Shutter speed, focal length, ISO from METADATA (if available).      |
| show_image_location               | KIOSK_SHOW_IMAGE_LOCATION       | bool               | false       | Display the image location from METADATA (if available).                                   |
| hide_countries                    | KIOSK_HIDE_COUNTRIES            | string           |           | List of countries to hide from image_location                                              |
| show_more_info                    | KIOSK_SHOW_MORE_INFO            | bool               | true        | Enables the display of additional information about the current image(s)                   |
| show_more_info_image_link         | KIOSK_SHOW_MORE_INFO_IMAGE_LINK | bool               | true        | Shows a link to the original image (in Immich) in the additional information overlay       |
| show_more_info_qr_code            | KIOSK_SHOW_MORE_INFO_QR_CODE    | bool               | true        | Displays a QR code linking to the original image (in Immich) in the additional information overlay |
| like_button_action            | KIOSK_LIKE_BUTTON_ACTION    | string           | [favorite]  | Action(s) to perform when the like button is clicked. Supported actions are [favorite, album]. |
| hide_button_action                | KIOSK_HIDE_BUTTON_ACTION        | string           | [tag]       | Action(s) to perform when the hide button is clicked. Supported actions are [tag, archive]. |
| immich_users_api_keys             | N/A                     | map[string]string          |          | key:value mappings of Immich usernames to their corresponding API keys. |
| show_user                         | KIOSK_SHOW_USER         | bool                       | false       | Display the user used to fetch the image. |
| weather             | N/A                     | WeatherLocation          |           | Display the current weather. |

> This project is not affiliated with Immich