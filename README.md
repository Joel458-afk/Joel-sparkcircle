# SparkCircle — local-first seven-persona prototype

A static web app shell for seven regional personas, teen/adult experience selection, prepared social guidance, browser speech, and optional in-browser text generation. It uses no paid AI API, API key, application backend, or server-side chat storage.

## Run / publish
Serve the repository root over HTTPS (GitHub Pages/Netlify) or a local static server. `file://` is not supported because ES modules and JSON/assets need HTTP. Three.js and the optional WebLLM package currently load from public CDNs; an internet connection is required. GitHub Pages must be enabled in repository settings (branch `main`, root).

## Local language model
The **Enable local AI** button lazily imports WebLLM and requests `Qwen2-0.5B-Instruct-q4f16_1-MLC`. The model is downloaded from its configured public model source and cached by the browser; it is not included in this repository. Approximate downloads vary by model build and cache; expect a large download (roughly 1 GB, not guaranteed). Users must explicitly opt in, have a compatible WebGPU-enabled browser/device, sufficient GPU/browser memory, and network access. Unsupported devices get prepared-topic matching instead. Test the exact model ID against the current WebLLM model catalog before shipping; model availability can change.

Inference runs in the browser after the weights load; there is no app API endpoint. However, the page still fetches JS/CDN libraries and model files from third parties. This is not a fully offline application until those dependencies and model files are self-hosted. A tiny model is less capable than Gemini-class services, may make mistakes, and is not guaranteed to handle every prompt safely. Safety keyword checks are limited heuristics, not dependable crisis detection. A qualified review, clear user reporting path, rate limits/abuse controls, and robust age verification/moderation are required before public dating-app deployment.

## Age-separated experience
Users explicitly select teen (13–17) or adult (18+) mode in the UI. The mode changes the local model instruction, but this client-side selector is **not age verification or an enforceable security boundary**. Do not use this prototype to mix minors with adult dating features. A production teen product needs legally reviewed age assurance, privacy/data-minimization design, safeguarding and moderation, and truly separate product/data access controls. Adult mode remains non-explicit and consent-centered in this prototype.

## Personas and 3D assets
`data/personas.js` contains seven configurable names, regions, voice locales/pitch preferences, and per-persona model paths. Actual character model assets were not attached to the repository in this task, so each persona shows a neutral placeholder until the licensed model is provided at its configured path. Put compatible `.obj` files and referenced texture/material assets under `models/`; the loader currently supports OBJ and applies a neutral material. For production-quality characters, prefer optimized GLB with documented license, rig/animation, facial morph targets, and a loading/error fallback. Regional identity is a setting, not a stereotype; avoid accent imitation and assumptions about personality.

## Voice limitations
Speech synthesis uses the system/browser voices and asks for the persona's English locale (`en-US`, `en-GB`, `en-IN`, or `en-AU`) plus a modest pitch adjustment. Web Speech does not standardize a voice's gender, and voice inventory differs by operating system. The app cannot guarantee a feminine voice on every device. Speech recognition support also varies and may use browser/vendor services; disclose this and provide typing as the alternative.

## Content and behavior
Prepared topic guidance lives in `index.html` for this prototype. The local model receives the conversation prompt plus topic guidance. Chat is held in page memory only and is not persisted by the app. Add reviewed content, reporting, consent UX, privacy policy, and safeguarding controls before launch. The site discloses that companions are AI, not real people.
