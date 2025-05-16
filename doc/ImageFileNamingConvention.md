## Paperdoll Image File Naming Convention

### Root Directory
```text
├── res
│   ├── body (stores body-related assets)
│   ├── face (stores face-related assets, default features and distinguishing features)
│   ├── hair (stores hair-related assets)
│   ├── clothes (stores clothing-related assets)
```

### Body-Related
```text
├── body
│   ├── breasts (breast size variations, naming format: breasts[1-6].png)
│   ├── penis (penis size variations, naming format: penis[0-6].png and penis_virgin[0-6].png)
│   ├── basehead.png (base head)
│   ├── basenoarms.png (base body without arms)
│   ├── basetorso.png (base torso)
│   ├── leftarm.png (left arm)
│   ├── rightarm.png (right arm)
```

### Face-Related
```text
├── face
│   ├── dmark (stores distinguishing features)
│   │   ├── [feature position] (feature name, spaces replaced with underscores, e.g., 'chin', 'eyes')
│   │   │   ├── [feature ID] (feature ID, spaces replaced with underscores, e.g., 'pointed_chin')
│   ├── baseeyes.png (base eyes)
│   ├── basemouth.png (base mouth)
│   ├── basenose.png (base nose)
│   ├── baseeyebrows.png (base eyebrows)
│   ├── baseface.png (base face)
│   ├── basechin.png (base chin)
```

### Hair-Related
```text
├── hair
│   ├── back (back hair)
│   │   ├── [hairstyle ID] (hairstyle ID, spaces replaced with underscores, e.g., 'in a bun' -> in_a_bun)
│   │   │   ├── [length].png (possible length variations, spaces replaced with underscores, e.g., 'mid-back length' -> mid-back_length.png)
│   ├── front (front hair)
│   │   ├── same as back hair
```

### Clothing-Related
```text
├── clothes
│   ├── [category in English] ("outerwear", "dresses", "bodysuits", "tops", "bottoms", "footwear", "underwear", "swimwear", "accessories", "masks", "bags")
│   │   ├── [clothing ID] (clothing ID, spaces replaced with underscores, e.g., 'Button-up Shirt' -> Button-up_Shirt)
```

- Clothing is divided into base items and variations (or wear configurations). All layers of base items and variations are divided into three sub-layers and one additional layer: full, left, right, acc.
    - full: clothing without left and right arms
    - left: left arm
    - right: right arm
    - acc: additional layer, all other content that is not colorable.

- If the clothing needs to be colorable, add _gray to the filename, e.g., full_gray, left_gray, right_gray. Note that acc cannot be colorable.
- For hat-type clothing: use mask.png to mask and constrain the hair layer; white is visible, transparent is hidden.

- Variations storage:
    - For clothing with color variations (e.g., color2), the directory remains the same as the base item.
    - Other variations are stored in subfolders named [variation name], e.g., Button-up_Shirt/design/xxx.png
    - Clothing ID naming rules:
        - Color variations are placed before full/left/right, e.g., color2_full_gray.png
        - Other variations are placed in their own folders before full/left/right, e.g., a_band_logo_full.png
        - All spaces in variation content or variation names should be replaced with underscores, e.g., a band logo -> a_band_logo
    - Breast variations:
        - Breast variations are divided into default and specific numbers. Specific number variations are named: breast[1-6]_full...; default breast variations are named: breast_full...
        - Breast variations are displayed when the current outermost clothing is the innermost clothing, e.g., wearing only a bra, not wearing a bra + bodysuit, etc.
- Theoretically, all layers have six images: full, left, right, acc_full, acc_left, acc_right. However, if an image is empty, it does not need to be stored.

### Example:
```text
├── clothes
│   ├── tops
│   │   ├── Fake_Sleeves_Graphic_T-shirt
│   │   │   ├── design
│   │   │   │   ├── a_bucking_bull_full.png
│   │   │   │   ├── ...
│   │   │   ├── sleeves
│   │   │   │   ├── down_sleeve_color2_right_gray.png (wear configuration: sleeves down, sleeve_color2 colorable)
│   │   │   │   ├── ...
│   │   │   ├── full_gray.png
│   │   │   ├── left_gray.png
│   │   │   ├── right_gray.png
│   │   ├── University_Esports_Jersey
│   │   │   ├── full_gray.png
│   │   │   ├── left_gray.png
│   │   │   ├── right_gray.png
│   │   │   ├── acc_full.png (additional layer: university logo, not colorable)
│   │   │   ├── color2_full_gray.png (color variation: colorable)
```

A complete sample image package will be released later. You can prepare materials according to this naming convention in advance.
Other Notes

- Complete clothing and hairstyle data acquisition:
    - ModLoader exports all data, database_xxx.js:
    - Or check in the browser console: setup.clothes, setup.hairstyles, setup.hairlengths (hair lengths)
- Canvas size: any size; you can choose any size from 64 to 1024 or more. The canvas size depends on the size of basenoarms.png (base body without arms).
- Background, foreground, close-up, or other layers: This system allows for easy addition of layers for further development.
