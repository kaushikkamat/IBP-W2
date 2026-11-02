# Farm to First Bite

A 60-second phone game for **Nutrielle Ragi & Millet** by IBP. Players harvest ragi and millet on a partner farm in Karnataka, bake them into cookies, drive the packs to the shops and take the first bite. The game ends on a ₹45 trial-pack offer.

It was made for IBP's launch press conference in *Baking a Strategic Mix 2026*, the Marketing Strategy & Innovation simulation in the GIM PGDM programme. A QR code on the event poster opens it on the audience's phones.

![Title screen, harvest, kitchen and end card](screenshots/preview.jpg)

Once GitHub Pages is on, the game lives at `https://<your-username>.github.io/farm-to-first-bite/`. The steps are under [Put it online](#put-it-online).

## How it plays

All four stages share one 60-second clock, and each stage feeds the next: the grain you catch is all the kitchen has to bake with, and every pack you seal rides on the truck.

| Stage | Time | What you do |
| --- | --- | --- |
| 1. Harvest | 15 s | Slide your finger to move the basket and catch ragi and millet. Golden ragi counts as three. A stone knocks one ragi out; husk just costs points. |
| 2. Bake | 30 s | Take each order through Mill, Mix, Bake and Pack, and pull the tray out while the marker is in the golden zone. An underbaked or burnt tray, or the wrong ingredient, gets the QC stamp: *"Only perfect cookies leave an IBP kitchen."* |
| 3. Deliver | 10 s | Swipe between three lanes. Drive over the Kirana, Supermarket and Quick-Commerce drops and miss the potholes. |
| 4. First Bite | 5 s | Open wide at the camera, or tap, for the crunch. |

The end card reads **Ragi & Millet · ragi from Karnataka · by IBP** and shows a star rating, Share and the **₹45 Trial Pack Offer**.

![The QC stamp, the Mix station and the delivery run](screenshots/stages.jpg)

**Controls.** On a phone you slide, tap and swipe. On a laptop the mouse does the same jobs, and the arrow keys move the basket and the truck. The clock stops during each stage's intro card, while the tab is in the background and while the phone is turned sideways.

### Scoring

| Action | Points |
| --- | --- |
| Ragi or millet caught | +10 |
| Golden ragi | +40 |
| Stone / husk | −15 / −5 |
| Order packed | +100 per cookie, plus 50 if packed within 6 s of starting it (25 within 9 s) |
| Kitchen cleared early | +5 for each second left |
| Pack delivered / pothole | +60 / −20 |
| First bite | +100 by camera, +60 by tap, +30 if time runs out |

Everyone starts on one star and earns another at 400, 800, 1,200 and 1,600 points. The best score is kept on the phone.

## Put it online

The camera bite only works on a secure (https) page, and GitHub Pages gives you one for free.

1. Create a new **public** repository on GitHub called `farm-to-first-bite`, without a README or licence. On a free account, Pages only works with public repositories.
2. On the empty repository's page, click **uploading an existing file**. Drag in what's *inside* this folder (`index.html`, `README.md` and the `screenshots` folder), not the folder itself, so `index.html` sits at the top level. Click **Commit changes**.
3. Open **Settings → Pages**. Under **Build and deployment**, set the source to **Deploy from a branch**, pick **main** and **/ (root)**, and click **Save**.
4. After a few minutes the Pages settings show the live address, `https://<your-username>.github.io/farm-to-first-bite/`. Use that link for the poster's QR code.

Before the event, scan the QR with an iPhone and an Android phone over the venue Wi-Fi.

If you'd rather use git:

```bash
cd farm-to-first-bite
git init -b main
git add .
git commit -m "Add Farm to First Bite"
git remote add origin https://github.com/<your-username>/farm-to-first-bite.git
git push -u origin main
```

## Record the press-conference clip

Add `#demo` to the end of the address and the game plays itself. It catches grain, works the kitchen, burns one tray on purpose (when there's grain to spare) so the QC stamp shows, drives the route and takes the bite. Start a screen recording and press **Start demo**. Switch the camera off first if you'd rather keep your face out of the clip.

## Run it on your computer

There's no build step: open `index.html` in a browser. To try the camera bite on your own machine, serve the folder instead, because browsers only allow the camera on https pages or localhost:

```bash
python3 -m http.server 8000
```

On Windows the command is `python -m http.server 8000`. Then go to http://localhost:8000.

## Change things

Everything lives in `index.html`. The settings you're most likely to change sit together at the top of the script:

| Constant | Controls |
| --- | --- |
| `STAGES` | Stage names, lengths in seconds and the goal line on each intro card |
| `RECIPE` | The cookie's name and how much ragi and millet each cookie uses |
| `DISTRACTORS` | The wrong ingredients offered at the Mix station |
| `STORES` | The three delivery stops |
| `RATING_STEPS` | Points needed for two, three, four and five stars |
| `OFFER_CODE` | The code shown with the ₹45 offer |

It's plain HTML, CSS and JavaScript with no libraries. The farm and the road are drawn on a canvas, the kitchen and the end card are ordinary page elements, and every sound is synthesised with the Web Audio API, so there are no audio files. The only outside request is for Google Fonts (Rozha One, Hind and Kalam); offline, the game falls back to system fonts.

## Privacy and accessibility

- The camera is optional. Players can switch it off on the title screen, and the game asks for permission before the clock starts.
- To spot an open mouth, the game shrinks each camera frame to 48 × 36 pixels on the phone. Nothing is recorded, stored or uploaded, and the camera turns off right after the bite.
- Only the best score and the sound and camera settings are saved, in the browser's local storage. There's no analytics or tracking.
- The kitchen stations, the bite, the offer and Share are ordinary buttons, so they work with a keyboard and screen readers. Stage starts, QC rejects and the final score are read out to screen readers, and the game follows the phone's reduce-motion setting.

## About

IBP (Indian Biscuit Products Ltd) and Nutrielle are fictional brands from a classroom simulation. They have no link to any real company, and the ₹45 offer and its code are a demo, not a real promotion.
