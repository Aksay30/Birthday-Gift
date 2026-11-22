# Birthday Surprise

A single-page birthday gift:

1. **Countdown.** Before the birthday, a live timer shows instead of the lock.
2. **Date lock.** The password is the date 15 / 09 / 2023.
3. **Three gift boxes:**
   - **Box 1, photo story.** Your song starts, then the photos deal in one at a time as polaroids, slowly zooming, with captions. Each finished photo drops onto a scattered pile behind the next. At the end they settle into a wall, and tapping any photo enlarges it.
   - **Box 2, a coupon.**
   - **Box 3, the real gift.** It's locked behind a three-question quiz.
4. **Finale.** A cake with candles to blow out.

There's no build step and no libraries.

## Folder layout

```
index.html
song.mp3          your background song
photos/
  1.jpg
  2.jpg
  ...
```

Until you add them, the photos show as coloured placeholders, and the song falls back to a built-in Happy Birthday tune.

## Customise

Everything is in the `CONFIG` block near the top of the `<script>` in `index.html`.

| Field          | What it does |
|----------------|--------------|
| `friendName`   | Name in the headings |
| `fromName`     | Your name. **Don't use the quiz answer here**, or the page gives it away. |
| `friendsSince` | Start date for the "Friends for N days" counter |
| `birthday`     | `"YYYY-MM-DD"`. The countdown runs until midnight on that day, in the viewer's time zone. Leave `""` to skip it. |
| `hint`         | Shown after two wrong password tries |
| `song`         | File name of the song, e.g. `"song.mp3"` |
| `songStart`    | Second to start the song from, e.g. `42` to jump to the chorus |
| `photoSeconds` | How long each photo stays on screen |
| `photos`       | List of `{ src, caption }`. Add or remove as many as you like. |
| `gifts`        | Text for the three boxes |
| `quiz`         | Questions, answers and hints. Answers ignore capitals, spaces and punctuation. |
| `finaleWish`   | Message shown after the candles go out |

### Photo tips

- Portrait photos look best, since the frame is 4:5.
- Resize them to about 1200px on the long side and keep each under 500 KB, so they load fast on mobile data. You can use squoosh.app to do this.
- File names are case-sensitive on GitHub Pages: `1.JPG` is not the same as `1.jpg`.

### Song tips

- Use an mp3 under about 8 MB.
- The song starts when your friend taps box 1. Phones only allow audio after a tap, which is why it doesn't start on page load.

## Test before you share

| Link | What it shows |
|------|---------------|
| `index.html?preview` | Skips the countdown, so you can test the whole flow before the birthday |
| `index.html?test-countdown` | Shows a 10-second countdown, then the lock |

Open `index.html` in your browser to try it. Photos and the song also load when you open the file directly.

## Change the password

The date is stored as a hash, not as text. Open the page, open the browser console and run `cyrb53("DDMMYYYY")` with your date, then paste the result into `PASS_HASH`.

## Host on GitHub Pages (free)

1. Create a repository, for example `happy-birthday`.
2. Upload `index.html`, `song.mp3` and the `photos` folder to its root.
3. Go to **Settings → Pages**, choose **Deploy from a branch**, then branch `main` and folder `/ (root)`, and save.
4. After a minute or two it's live at `https://<your-username>.github.io/happy-birthday/`.

## Privacy note

A free GitHub Pages site comes from a public repository. Anyone who finds the repo or views the page source can see the photos, the gift text and the quiz answers. Pick a repo name that doesn't give away the surprise.
