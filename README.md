# Ripon AI Photo Studio  (rust.riponaistudio)

A fast, **offline** passport / ID photo studio for Windows, written in Rust.
Remove the background, crop the head, enhance, retouch and print — for **one customer or ten at once** —
plus AI upscaling, face restore and an ID-card (NID) scanner-style tool.

No Python, no GPU, no extra DLLs. One `.exe`. Your photos never leave your computer.

![Edit photo](docs/screenshots/01-edit-photo.png)

## Download and install

**[Download the latest installer (Windows 10 / 11)](../../releases/latest)** — get
`rust.riponaistudio-Setup-<version>.exe` from the *Assets* list and run it.

AI models are *not* inside the installer. After the first start press **AI Models** (top right) and
**Download** the ones you want (see [AI Models](#ai-models)). The app works without them too —
you can still crop, enhance, print, and erase the background by hand.

---

## Quick start (30 seconds)

1. **Open photo** (or drag and drop a picture into the window).
2. The background is removed and the head is placed in the orange frame automatically.
3. Choose the photo size on the left (Passport 35 x 45 mm, visa, custom ...).
4. On the right choose paper and copies, then press **Print sheet** — or save **PDF / JPG / PNG**.

---

## The five tabs

### 1. Edit photo
The main page. Everything for one photo is on one screen: left = tools, middle = original with the crop frame,
right = the finished result.

| Card | What it does |
|---|---|
| **1 Size & crop** | Choose the photo size. **Auto head crop** places the head. Move the frame with the mouse (drag to move, drag a corner to resize, wheel = zoom) or with the **Left / Right / Up / Down** buttons. **Rotate** left/right 90°, **Free rotate** in 1° steps (buttons, slider, drag the number, mouse wheel or arrow keys), **Flip**. Quality 200 / 300 / 600 dpi. |
| **2 Background** | **Remove background** with an AI model, or **Keep original**. Pick the background colour. **Edge smooth** and **Edge cut** clean the edge. The brush and Pen tools fix mistakes (below). |
| **3 Enhance** | Auto colour & light, brightness, contrast, colour, lift shadows, sharpen, reduce noise, black & white. |
| **AI Enhance** | **Upscale x4** and **Restore face** for small, blurry or old photos (needs the optional models). Has **Undo AI enhance**. |
| **4 Retouch** | Skin smooth and **Spot heal** (click a pimple / dust spot). |
| **Dress / name** | Put a suit / dress overlay (your own transparent PNGs in the `dress` folder) and a name / date line under the photo. |

**Duet (2 photos in one frame)** — press **Duet** in card 1 for bank-size 1.9 x 1.5 in style frames.
Photo **A** and **B** are completely independent (own crop, colours, clean-up). Use **Pin as Photo A / B**, drag and
resize each photo with the mouse, set the gap and alignment. **Undo / Redo** = Ctrl+Z / Ctrl+Y.

![Duet](docs/screenshots/07-duet.png)

#### Fixing the background by hand
Press a tool, then paint / click **on the RESULT picture**. Scroll = zoom, right mouse drag = move, **Esc** = stop.

- **Restore (red)** brings the person back. **Erase (blue)** removes background.
- **Softness** — left = hard sharp edge, right = soft feathered edge (the thin inner ring shows the full-strength part).
- **Strength** — low = a gentle touch, go over the same place again for more.
- Presets: **Hard edge**, **Soft edge**, **Gentle**. Undo stroke / Clear brush.
- **Pen tool** — click point after point around an area. Click the first (orange) point, double-click or press
  **Enter** to close the shape. **Backspace** removes the last point.
- **Lasso** — hold the mouse button and draw around the area, release to close.
- For a Pen / Lasso shape choose: **Remove inside**, **Restore inside** or **Keep only inside**
  (everything outside is removed), and an **Edge feather** (0 = sharp cut, higher = soft blend).
  Undo shape / Clear shapes.

![Pen tool](docs/screenshots/06-pen-tool.png)

### 2. Print sheet
Shows the real print sheet: A4, 4R, 5R, A3, Letter or a custom paper. Choose **Copies** (or **Fill the page**),
**Gap**, **Margin**, border or **cut marks**, **Rotate to fit more**, and an optional studio name line.
The line under the preview tells you how many photos fit.

- **Print sheet** opens the normal Windows print window (choose the printer, number of copies, Preferences)
  and prints at real size. Set paper to A4 / correct size in the printer's Preferences.
- **PDF / JPG / PNG** save the whole sheet. **Photo JPG / PNG** save a single photo.
- **For online forms (KB limit)** — set pixel size and the maximum KB, then **Save JPG under limit**.

![Print sheet](docs/screenshots/02-print-sheet.png)

### 3. Document / NID
For ID cards, NID, certificates and whole A4 / Legal pages that a customer sends as a phone picture.

1. Open the **Front** and **Back** pictures (drag and drop or **Replace**). Front and back are **fully independent** —
   crop, turn and clean-up of one never changes the other.
2. The card is found and straightened. If it is wrong, press **Auto detect** / **AI detect**, or drag the **4 round handles**
   onto the corners (a loupe helps). Use **90° / 180° / Flip** to turn it.
3. Choose the size of the picture on the page (ID card 85.6 x 54 mm, A4, Legal, custom).
4. Clean-up: even out the light, remove shadows, contrast, sharpen, grey / scan B&W, **Old document restore**,
   remove **red / blue ink, seals, pen writing**, and the hand **Eraser**.
5. **Page layout** tab: drag cards to move them, drag the handles to resize, add **Front copy / Back copy**, type exact
   X / Y / W / H in mm, **Auto arrange all**, **Fit page (keep shape)**. Zoom with the `-` / `+` / **Fit** buttons and the wheel.
6. **Print page** or save the page as PDF / JPG / PNG at real size.

![Document tool](docs/screenshots/04-document-nid.png)

### 4. Batch print (many customers)
Ten customers, two copies each? Put them all on **one** A4 sheet.

1. Press **Add photos...** and select many pictures at once — or drag and drop them into the window.
2. Every customer gets a card with a small preview, an editable **name**, and **- / +** for the **copies**.
   **Set for all** gives every customer the same copy count. The total number of photos is counted for you.
3. Choose the **photo size**, **background colour**, **paper** (A4, A3, 4R, 5R, Letter, custom, portrait or landscape),
   **gap**, **margin**, border or cut marks, and quality (200 / 300 / 600 dpi).
4. The preview shows exactly what will be printed. If everything does not fit, more sheets are added
   (use the `<` `>` buttons above the preview). **Smart packing** places the photos so the least paper is used.
   Photos are never stretched.
5. Select a customer for more options: **Edit photo** (opens the full editor — crop, brush, upscale ... — then
   **Done - back to batch**), **Replace**, **Up / Down**, **Remove**, and **Own size for this customer** if one person needs
   a different size.
6. **Print all sheets** or save **PDF / JPG / PNG**.

Background removal for the batch runs one photo at a time in the background — you can keep working, and one photo
that fails does not stop the others.

![Batch print](docs/screenshots/03-batch-print.png)

### 5. AI Models
Press **AI Models** (top right). Models are kept in `%LOCALAPPDATA%\RiponComputer\models\`
(the same folder as the Ripon Computer Python app, so models you already have are found).

| Model | Used for | Size |
|---|---|---|
| **U2Net human** | Background removal, best for people | ~168 MB |
| **IS-Net general** | Background removal with sharp hair & edges; also used by *Document → AI detect* | ~170 MB |
| **SPAN x4** | Fast upscaling (recommended) | ~2 MB |
| ClearReality, UltraSharp, **Real-ESRGAN** | Other upscalers — Real-ESRGAN is the best quality but slow on a CPU | varies |
| **GFPGAN 1.4 / 1.2, CodeFormer** | Face restore | varies |

Per model: **Download**, **Import file...** (if you downloaded it yourself), **Delete**, status.
**Download links are editable** (several per model, tried in order) — release links expire, so you can paste a new one.
**Backup all models (.zip)** and **Restore from backup (.zip)** move everything to another computer.

![AI Models](docs/screenshots/05-ai-models.png)

---

## Tips for a photo studio

- Set your studio printer as the Windows **default printer** — it is pre-selected in the print window.
- For passport sheets, choose **A4**, **Copies = Fill the page** and **Cut marks**.
- If the AI cuts a little too much hair, use **Restore** with a soft brush; for a stray background piece use **Pen → Remove inside**.
- The batch tab keeps each customer's own edits. Use **Edit photo** for the one difficult photo and leave the rest automatic.
- If something goes wrong, error details are written to `ripon-studio.log` in `%APPDATA%\RiponAIPhotoStudio`.

## Keyboard and mouse

| Action | How |
|---|---|
| Zoom a picture | mouse wheel |
| Move a zoomed picture | right mouse drag |
| Undo / Redo | Ctrl+Z / Ctrl+Y |
| Stop a brush / pen tool | Esc |
| Close a Pen shape | click the orange first point, double-click, or Enter |
| Remove last Pen point | Backspace |
| Nudge a card on the A4 page | arrow keys: 0.5 mm, Shift = 5 mm |
| Open photo | Ctrl+O |

## Build from source

Requirements: Rust (MSVC toolchain) on Windows 10 / 11.

```
cargo build --release
```
Result: `target\release\ripon-ai-photo-studio.exe`.
`build_installer.bat` also builds the Setup file (needs Inno Setup 6). A GitHub Action
(`.github/workflows/build-windows.yml`) builds the exe and installer for you.

Command line: `ripon-ai-photo-studio photo.jpg` opens a photo, `--doc front.jpg back.jpg` opens the Document tab,
`--batch a.jpg b.jpg ...` opens Batch print.

## Notes

- Tested with unit tests, a headless self-test and the GUI under Linux. The Windows exe, real printers and
  antivirus / proxy environments depend on your machine — if something does not work, please open an issue with a screenshot.
- Face restore expects a roughly frontal face (passport style).
- The screenshots use the Ripon AI Photo Studio logo as the sample picture.

## Model credits and licences

Models are downloaded from their original release pages and are **not** part of this repository.
Check each licence before commercial use — for example CodeFormer is released for non-commercial use.
- U2-Net, IS-Net: via [rembg](https://github.com/danielgatis/rembg)
- GFPGAN, CodeFormer, Real-ESRGAN, SPAN and other upscalers: ONNX conversions from
  [facefusion-assets](https://github.com/facefusion/facefusion-assets)
- Inference: [tract](https://github.com/sonos/tract) (pure Rust ONNX). GUI: [egui / eframe](https://github.com/emilk/egui).
- Font: Poppins (SIL Open Font License).

---

© Ripon Computer
