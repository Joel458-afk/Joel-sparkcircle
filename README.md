# SparkCircle — Static 3D Companion MVP

A static, client-side social-confidence guidance demo. It uses prepared responses from `data/content.json`, Three.js for the 3D stage, and browser-native speech features. There is no AI API, backend, account system, or server-side chat storage.

## Run and publish

- Open the deployed GitHub Pages URL over HTTPS, or serve this repository with any static web server. `index.html` loads `data/content.json` with `fetch`, so opening it directly as a `file://` URL may not work.
- GitHub Pages can serve the site, but this repository's Pages setting must be enabled in **Settings → Pages** (Deploy from a branch, `main`, root).
- Three.js and Tailwind are loaded from public CDNs, so the first load needs an internet connection.

## 3D model asset

The viewer tries to load these relative paths:

- `USCHighPack/model.obj`
- `USCHighPack/texture_diffuse.png`

If either is not present or fails to load, the app renders a procedural Three.js character instead. Put the extracted model files at those paths in the repository to use the supplied model. The normal and specular maps are listed in `manifest.json` but are not currently applied. Large texture files may exceed GitHub's file-size limits; consider resizing/compressing them before committing.

The chat has no generative AI: it picks matching, author-prepared topic responses from `data/content.json`. Unmatched topics use the prepared fallback. Browser speech recognition support varies by browser, and may require microphone permission and HTTPS. Speech synthesis uses voices installed/provided by the browser/operating system.

## Content editing

Edit `data/content.json` to add companions, keywords, topics, approved responses, tips, and follow-up prompts. A companion's `approvedTopics` controls which topics are available to that character. Avoid collecting sensitive personal information; chat content is currently only held in page memory.

## Safety note

SparkCircle is a static demo, not a professional counseling or emergency service. Keep guidance age-appropriate, respectful, and transparent about its prepared/non-AI nature.
