## [The Japanese version of the README is here.](README.md)
# (improved) Beat Saber Overlay

This is an improved version of Reselim's [Beat Saber Overlay](https://github.com/Reselim/beat-saber-overlay) with various display options.

Overlay the score information when distributing or recording Beat Saber via OBS.

![preview](https://rynan4818.github.io/beatsaber-overlay-bsr-image.png)

- The image shows a sample of the full option using HttpStatusExtention.

## Installation (OBS)

1. Please install the following mods to send the beat saver data to the overlay.

   If you are a beginner, we recommend you to install the original version of HTTP Status from ModAssistant, which will automatically install the dependent mods for you.

   - [Beat Saber HTTP Status](https://github.com/opl-/beatsaber-http-status) *Original version of ModAssistant registration

      ![image](https://rynan4818.github.io/beatsaber-overlay-httpstatus.png)

   There is also a performance-improved version produced by denpadokei.
   - [HttpSiraStatus](https://github.com/denpadokei/beatsaber-http-status)

      ![image](https://rynan4818.github.io/beatsaber-overlay-denpadokei_en.png)

   To use the optional `pp` feature and the custom difficulty display, you will also need to install denpadokei's version of HttpSiraStatus and the HttpStatusExtention.
	 - [HttpStatusExtention](https://github.com/denpadokei/HttpStatusExtention)

   *Both versions of HTTP Status require you to install `websocket-sharp` in ModAssistant. Please note that it is often forgotten to install.

   ![image](https://rynan4818.github.io/beatsaber-overlay-websocket-sharp.png)

2. Download the latest release from the [release page](https://github.com/rynan4818/beat-saber-overlay/releases).

3. Extract the zip to an appropriate folder. (Example: C:\TOOL\beat-saber-overlay)

4. Create a Browser source

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting1_en.png)

5. In Create new, enter an appropriate name and press OK.

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting2_en.png)

6. Double-click index.html in the unzipped zip file or open it with Chrome or Edge browser.

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting3_en.png)

7. Copy the address(URL) field of your browser.

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting4_en.png)

8. Paste the copied address into the OBS URL field.

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting5_en.png)

   If it is a `Local file`, you cannot set options, so you need to enter it in URL notation like this.

   Set the size equal to your canvas size (1280x720, etc.)

   (Optional) For 1080p canvases, add the `scale` modifier to scale the overlay by 1.5x.

	    file:///C:/TOOL/beat-saber-overlay/index.html?modifiers=scale

9. If necessary, add `?modifiers=` after index.html in the URL to set the options. Separate multiple options with a comma (,).

   ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting6_en.png)

10. The width of the property can be deliberately shrunk to narrow the display width of the overlay.

    If you reduce the width to less than the canvas size, the overflow text(Title, Subtitle, Artist[Mapper], Custom difficulty) will scroll.

    ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting7_en.png)

    ![image](https://rynan4818.github.io/beatsaber-overlay-scllol.gif)

11. Raise the order of the overlay sources to a higher priority than the game sources so that the overlay is superimposed on the game screen.

    ![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting8_en.png)

## Options

Options are added to the URL query as such:

```
file:///C:/TOOL/beat-saber-overlay/index.html?modifiers=top,all
```

### `modifiers`

Multiple modifiers can be seperated with commas.

- `top`
	* Moves the overlay to the top and reverses the layout vertically
- `rtl`
	* Moves the overlay to the right and uses right-to-left text
- `scale`
	* Scales the overlay by 1.5x, for use on 1080p canvases
- `test`
	* Makes the background black, for testing purposes
- `bsr`
	* Show beatsaver's map key
- `miss`
	* Show the number of misses
- `mod`
	* Show Modifier (ex. DA,FS,NA,etc...)
- `energy`
	* Show energy bar
- `pp`
	* Shows pp points with 100% accuracy, Star Difficulty, and real-time pp points for ranked map.（*1）
- `label`
   * Displays the custom difficulty level, if any, along with the default difficulty level.(*1)
- `all`
	* `bsr`, `miss`, `mod`, `energy`, `pp`, `label` Show all options.（*1）
- `no-performance`
	* Hide score display
- `no-hidden`
	* Don't hide the overlay when the map ends

*1：To use the `pp` and `label` option, you need to install [HttpStatusExtention](https://github.com/denpadokei/HttpStatusExtention).

### `ip` and `port`

Listen to events from another IP and/or port.
```
file:///C:/TOOL/beat-saber-overlay/index.html?ip=192.168.1.10&port=6557&modifiers=top,bsr
```

### Other
The [Japanese README](https://github.com/rynan4818/beat-saber-overlay/blob/master/README.md#%E6%A9%9F%E8%83%BD%E8%BF%BD%E5%8A%A0%E8%A1%A8%E7%A4%BA%E5%A4%89%E6%9B%B4%E3%82%B9%E3%82%AD%E3%83%B3) has other explanations, such as additional overlay features and skin changes.

We do not provide this overlay via GitHub Pages, etc., which is common for other overlays, for the following reasons.

- There were many troubles with the original (Unnamed) Beat Saber Overlay due to URL changes.

- It is not possible to use it in case of network problems, such as not being able to connect to GitHub.

- It's a bit of a hassle, but there's no problem with downloading and displaying it as a local file.

---

This README has been translated by www.DeepL.com/Translator (free version).
