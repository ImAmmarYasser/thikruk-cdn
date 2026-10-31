# thikruk-cdn

Files the Thikruk app downloads on demand, served straight from GitHub:
`https://raw.githubusercontent.com/ImAmmarYasser/thikruk-cdn/main/<path>`.
(jsDelivr is not used: it refuses repositories over 50 MB.)

## adhan/

- `catalog.json`: the list the app reads. Fields per muezzin: `id`, `name_ar`, `name_en`, `country`, `source`,
  and any of `full`, `takbeer`, `fajr_full`, `fajr_takbeer` (MP3, for Android), `ios_sound`, `fajr_ios_sound`
  (CAF, 30 seconds at most, as iOS notification sounds). Each file is `{ "url": ..., "size": bytes }`.
  `dua_voices`: `id`, `name_ar`, `name_en`, `source`, `file`.
- `<id>/…`: each muezzin's recordings: `full.mp3`, `takbeer.mp3`, `takbeer.caf`, and the same with a
  `fajr_` prefix for Fajr's adhan.
- `dua/<id>.mp3`: the supplication after the adhan.

To add a voice, put its files under `adhan/<id>/`, add it to `catalog.json` and push; GitHub serves the
new files within about five minutes. Copy `catalog.json` into the app's `assets/data/adhan_catalog.json`
too, so the list shows before the app reaches the server.

iOS sounds can be made from an MP3 on a Mac with:
`afconvert -f caff -d ima4 -c 1 in.mp3 out.caf` (trim to 30 seconds first).
