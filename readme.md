**A Paperdoll System Implementation for Course of Temptation**

This is a fork of the original mod by HCPTangHY, translated to English.

---

## 🛠️ Usage Instructions

* **Download**: Get the latest version from the [Releases](https://github.com/vatavian/CoT-Paperdoll-Mod/releases) section.
* **Installation**: Use a mod loader to load the mod into the game.
* **Pixel Character Pack**: Each release includes a pixel character pack mod for beautification purposes. Regular players don't need to download this.
* **Customization**: Beautification authors can create their own packs based on the sample. Leave unwanted original images transparent.

---

## 📚 Data Guide

* **Naming Conventions**: [Folder structure for images.](https://github.com/vatavian/CoT-Paperdoll-Mod/blob/custom/doc/ImageFileNamingConvention.md)
* **Hairstyles**: [List of hairstyle names.](https://github.com/vatavian/CoT-Paperdoll-Mod/blob/custom/doc/hairstyle.md)
* **Distinctive Features**: [Names of unique character features](https://github.com/vatavian/CoT-Paperdoll-Mod/blob/custom/doc/dmarks.md)
* **Clothing Data**: Due to the large volume, specific data isn't provided here. Use the Modloader interface's "Export All Current Data" feature to find `js/database_clothes.js`, which contains all clothing data.

---

## 🧩 APIs

### `Paperdoll` Class

* `loadBaseModel(src)`: Loads the base model of the paperdoll. The canvas size is determined by the image size.
* `loadLayer(src, color='', type='')`: Loads a layer. If no color is specified, no coloring is applied. `type` can be `skin`, `hair`, etc.
* `desaturateImage(src)`: Converts the image to grayscale.
* `colorLayer(src, color, mode)`: Applies color to a layer.
* `draw()`: Renders the final image.

### `setup.Paperdoll.paperdollPC`

* Methods related to the sidebar paperdoll.
* Use the `ReplacePatcherAddon` to insert code into this method.
* `PCLayers` format: `{layer: xxx, load: async function() { ... }}`

---

## 🧪 Release Notes

### Version 1.4.5

* Added a refresh button for the sidebar paperdoll.
* Introduced a mirror passage in the wardrobe to view large images without scaling.
* Fixed chest variations and made minor adjustments to the scaling function.
* Enabled clicking the sidebar to view large images.
* Added custom scaling options.
