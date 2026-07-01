# Quran Word-by-Word Audio Packages

Pre-built word-by-word audio packages for **Mishary Al-Afasy** recitation. These packages power the word-by-word playback feature in the [Noor Al-Imaan](https://github.com/Mohamedd-Ashraf/Noor-Al-Imaan) app.

## Structure

```
manifest.json          — Manifest listing all 114 surahs with checksums and metadata
001.pack               — Surah Al-Fatiha (ZIP containing 29 word MP3s)
001.index.json         — Index with word timing, offsets, and checksums
002.pack               — Surah Al-Baqarah (6,121 words)
002.index.json
...
114.pack               — Surah An-Nas (20 words)
114.index.json
```

## Stats

| Metric | Value |
|--------|-------|
| Surahs | 114 |
| Total words | 77,491 |
| Package format version | 1 |
| Min compatible version | 1 |
| Total size | ~3.25 GB |

## Usage

### Download URL pattern

```
https://github.com/Mohamedd-Ashraf/quran-word-by-word-audio/releases/download/v1.0.0/{filename}
```

### Integrating in your app

```dart
final baseUrl = 'https://github.com/Mohamedd-Ashraf/quran-word-by-word-audio/releases/download/v1.0.0';

// Fetch manifest
final manifest = await http.get('$baseUrl/manifest.json');

// Download a surah pack
final surahPack = await http.get('$baseUrl/001.pack');

// Load word index
final index = await http.get('$baseUrl/001.index.json');
```

### Manifest format

```json
{
  "version": 1,
  "kind": "word_by_word",
  "editionId": "word_by_word_mishary",
  "minCompatibleVersion": 1,
  "entries": [
    {
      "surahNumber": 1,
      "wordCount": 29,
      "audioFile": "001.pack",
      "checksum": "sha256-of-pack",
      "bytes": 1794871,
      "indexFile": "001.index.json",
      "indexChecksum": "sha256-of-index"
    }
  ]
}
```

## License

The audio content belongs to Mishary Al-Afasy and is publicly available via [QuranCentral](https://audio.qurancdn.com/wbw/). This repository is a redistributable packaging format for app integration.

## Build

These packages were built using the [Noor Al-Imaan](https://github.com/Mohamedd-Ashraf/Noor-Al-Imaan) build tool (`tool/build_word_by_word_packages.dart`). Source MP3s: `https://audio.qurancdn.com/wbw/{NNN}_{AAA}_{WWW}.mp3`.
