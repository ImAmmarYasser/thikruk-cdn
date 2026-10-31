# thikruk-cdn

Files the Thikruk app downloads on demand, served through jsDelivr:
`https://cdn.jsdelivr.net/gh/ImAmmarYasser/thikruk-cdn@main/<path>`.

## adhan/

- `catalog.json`: the list the app reads. Fields per muezzin: `id`, `name_ar`, `name_en`, `country`, `source`,
  and any of `full`, `takbeer`, `fajr_full`, `fajr_takbeer` (MP3, for Android), `ios_sound`, `fajr_ios_sound`
  (CAF, 30 seconds at most, as iOS notification sounds). Each file is `{ "url": ..., "size": bytes }`.
  `dua_voices`: `id`, `name_ar`, `name_en`, `source`, `file`.
- `<id>/…`: each muezzin's recordings.

To add a voice, put its files under `adhan/<id>/`, add it to `catalog.json`, push, then purge the cache:
`https://purge.jsdelivr.net/gh/ImAmmarYasser/thikruk-cdn@main/adhan/catalog.json`.

iOS sounds can be made from an MP3 on a Mac with:
`afconvert -f caff -d ima4 -c 1 in.mp3 out.caf` (trim to 30 seconds first).
