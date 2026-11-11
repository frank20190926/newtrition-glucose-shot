# NewTrition Glucose Shot — pouch artwork

Front panel artwork for the NewTrition Glucose Shot 1.7 fl oz (50ml) pouch in four flavors: Wild Berry, Grape, Blue Raspberry, Mystic Melon. Freelancer contest #2801092.

Live inspector: https://frank20190926.github.io/newtrition-glucose-shot/

Master package: https://frank20190926.github.io/newtrition-glucose-shot/downloads/NewTrition_Glucose_Shot_Master_Package.zip

## What is kept from the client file

The pouch shape, the colored header (silver hexagonal N emblem, NEWTRITION® wordmark, "Perform • Recover • Thrive"), the tear tab with its flavor arc and chevron row, the silver collar, and the film shading all come from the supplied `3D_Shot_Pouch.jpeg`. Only the body print below the collar is new. There is no fruit imagery and there are no icons anywhere in the artwork.

## Copy on the front panel

| Level | Text |
|---|---|
| Product title | GLUCOSE SHOT |
| Dose | 15g Fast-Acting Glucose |
| Function | Raises Low Blood Sugar • Boosts Energy |
| Attributes | Naturally Flavored • Ready to Drink • Caffeine Free |
| Bottom | DIETARY SUPPLEMENT / 1.7 fl oz (50ml) |

Cap heights on the flat master: GLUCOSE 8.1 mm, SHOT 13.9 mm, 15g 6.6 mm (0.60 of the mean title cap height).

## Master package contents

| Folder / file | Contents | Files |
|---|---|---:|
| `01_3D_Pouch_Renders/` | 4 single pouches, 4-flavor line-up, counter display; transparent PNG | 6 |
| `02_Print_Ready_Outlined_Vectors/` | `.ai` `.eps` `.pdf` (CMYK, 3 mm bleed, TrimBox) and `.svg` per flavor; all type outlined | 16 |
| `03_Editable_Layered_SVGs/` | `.svg` per flavor with live text and named layers | 4 |
| `04_HighRes_Flat_Artwork_PNG/` | 1880 × 5648 px flat artwork per flavor | 4 |
| `NewTrition_Glucose_Shot_Presentation.pdf` | The four presentation sheets | 1 |

## Production notes

- Nominal trim is 47.0 × 141.2 mm, scaled from the 50 ml size rendering. Check it against the converter's die before plating.
- The `.ai` files are PDF-compatible Illustrator files. The `.svg` masters are sRGB; the `.ai` / `.eps` / `.pdf` masters are DeviceCMYK.
- The header is placed as the supplied raster inside its die shape. If a vector header exists, drop it into the `header-client-locked` layer.
- Pantone numbers on sheet 02 are nearest Pantone Coated references, to be confirmed on a press proof.
- Editable SVGs use Barlow Condensed and Montserrat (both SIL Open Font License).

## Rebuild

```
python3.11 scripts/build_flat.py                 # flat vector masters
python3.11 scripts/build_pouches.py              # pouch renders + sheet 01
python3.11 scripts/build_retail.py 2400 2160 160 # counter display (Blender Cycles)
python3.11 scripts/build_boards_and_package.py   # sheets 02-04, PDF, ZIP, docs/ assets
```

Requires `rsvg-convert`, Ghostscript, Blender, and the Python packages numpy, scipy, opencv-python, Pillow, PyMuPDF, uharfbuzz.
