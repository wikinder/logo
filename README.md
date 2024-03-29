# logo

![logo.png](logo.png)

OS: MacOS with Homebrew installed

```
brew install imagemagick librsvg
```

1. Download [`1f9f8.svg`][1f9f8.svg] from Twemoji:
    ```
    curl -O https://raw.githubusercontent.com/twitter/twemoji/v14.0.2/assets/svg/1f9f8.svg
    ```
2. Convert it to an 816x816 transparent PNG (which will have a 16px margin at the bottom):
    ```
    rsvg-convert -h 816 -o 1f9f8-816px.png 1f9f8.svg
    ```
4. Crop to create an 800x800 PNG (which is live as [`icon.png`](https://wikinder.org/w/resources/assets/icon.png) for `og:image`; [favicon](https://wikinder.org/favicon.ico) was created based on this):
    ```
    convert -crop +8+0 -crop -8-16 1f9f8-816px.png 1f9f8-800px.png
    ```
5. Resize it to 200px and trim (resulting in 136x200):
    ```
    convert -geometry x200 1f9f8-800px.png 1f9f8-200px.png
    ```
    ```
    convert -trim 1f9f8-200px.png 1f9f8-200px-trimmed.png
    ```
6. Convert [`WikindeR.svg`](#wikindersvg) to a PNG of 200px height (resulting in 965x200):
    ```
    rsvg-convert -h 200 -o WikindeR-200px.png WikindeR.svg
    ```
7. Merge the two images side by side with a 59px space in between (resulting in 1160x200):
    ```
    convert 1f9f8-200px-trimmed.png WikindeR-200px.png -background transparent -splice 59x0+0+0 +append -chop 59x0+0+0 logo.png
    ```

## [`WikindeR.svg`](WikindeR.svg)

This was created as follows:

1. Download [`toys_r_us.ttf`][toys_r_us.ttf] from CDNFonts:
    ```
    curl -O https://fonts.cdnfonts.com/s/95273/toys_r_us.ttf
    ```
2. Upload it to [google-font-to-svg-path](https://danmarshall.github.io/google-font-to-svg-path/) and generate `WikindeR.svg` with the following settings:
    * Text: WikindeR
    * Size: 100
    * Separate Characters: Yes
    * Stroke Width: 0
    * Non-Scaling Stroke: No
    * (leave all other settings as default)
4. Manually edit the SVG in a text editor.  In particular, change the color of each letter with reference to [Encycolorpedia](https://encycolorpedia.com/companies/us/toys-r-us).

## License

[`1f9f8.svg`][1f9f8.svg] (c) 2019 Twitter, Inc and other contributors. [CC BY 4.0][CC-BY-4.0]

[`toys_r_us.ttf`][toys_r_us.ttf] (c) Unknown

Any modifications we made are licensed under [CC0][CC0-1.0].

[1f9f8.svg]: https://github.com/twitter/twemoji/blob/v14.0.2/assets/svg/1f9f8.svg
[toys_r_us.ttf]: https://www.cdnfonts.com/toys-r-us-2.font
[CC0-1.0]: https://creativecommons.org/publicdomain/zero/1.0/
[CC-BY-4.0]: https://creativecommons.org/licenses/by/4.0/
