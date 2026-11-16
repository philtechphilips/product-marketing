# NIVEA Black & White shoppable banner

A shoppable banner built like the Derma Control reference ad (https://nivea-shoppable.onrender.com/), using the Black & White artwork in `images/`.

- Each bottle has a pulsing **+** hotspot. Tapping it opens a product card with the Jumia photo, price and discount. Tapping the card opens that product on Jumia.
- **BUY NOW** (which pulses) and the rest of the banner open the main product on Jumia.

## Links

| Where you tap | Opens on Jumia |
| --- | --- |
| BUY NOW, background, men's bottle | [NIVEA MEN Black & White Invisible Original Roll-on 72h, 50ml (Pack of 3)](https://www.jumia.com.ng/nivea-men-black-white-invisible-original-anti-perspirant-roll-on-for-men-72h-50ml-pack-of-3-104325951.html) |
| Women's bottle | [NIVEA Black & White Invisible Clear Roll-on 72h, 50ml (Pack of 3)](https://www.jumia.com.ng/nivea-black-white-invisible-clear-anti-perspirant-roll-on-for-women-72h-50ml-pack-of-3-104325949.html) |

To change a link, a price or a product name, edit `MAIN_URL` and `PRODUCTS` at the top of the script in `index.html`. The prices shown on the cards (₦4,000, was ₦6,125, −35%) were copied from Jumia on 16 Nov 2026 and do not update by themselves. Set `old` and `off` to `''` to hide the old price and the discount badge.

## Desktop and mobile

The page adapts to the screen it is opened on:

| Screen | What it shows |
| --- | --- |
| Desktop (900px wide or more) | The 300×600 ad, enlarged to fit the window height, with a shop panel beside it listing both products and their Buy on Jumia buttons. |
| Phone, tablet, landscape phone | The ad alone, filling as much of the screen as it can. It uses whichever of the three banners best matches the screen shape: 300×600 on tall phones, 320×480 on tablets, 300×250 in landscape. |
| Ad slot (300×600, 320×480, 300×250) | Exactly the banner at its real size, as before. |

Any space the ad does not cover is filled with a blurred copy of the banner. The ad is never enlarged beyond 1.6× (`MAX_SCALE` in `index.html`), because the artwork is only 300px wide and would go soft.

## URLs

| URL | Shows |
| --- | --- |
| `/` | Picks the layout for the screen (see above) |
| `/?size=300x600`, `/?size=320x480`, `/?size=300x250` | Forces that banner size |
| `/preview.html` | All three sizes side by side |

To track clicks through an ad server, add its click macro, for example `/?size=300x250&click=${CLICK_URL}`. Every link in the ad then goes to the macro with the Jumia URL encoded after it.

If you move a size's artwork, the hotspot and BUY NOW positions for that size are in `LAYOUTS` in `index.html`, in banner pixels.

## Run locally

```sh
python3 -m http.server 8080
# open http://localhost:8080
```

## Deploy on Render

1. Push this folder to a GitHub repo.
2. In Render, choose **New → Static Site** and select the repo.
3. Leave the build command empty and set the publish directory to `.`
