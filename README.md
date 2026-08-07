# Hydraulic_Jack_127_Training

GitHub Pages / iOS PWA package.

## Publish on GitHub Pages

Upload the contents of this folder to the root of the selected GitHub Pages branch/folder. Keep `index.html`, `manifest.webmanifest`, `service-worker.js`, `.nojekyll`, `icons/`, and `signature/` together.

GitHub Pages provides HTTPS, which is required for service-worker/PWA operation.

## Install on iPhone / iPad

Open the published GitHub Pages URL in Safari, use **Share → Add to Home Screen**, then launch it from the Home Screen. The package is configured for standalone, landscape-oriented use and caches the app shell for offline reopening after the first successful load.

## Integrity / cryptographic signature

`signature/integrity.sha256` contains SHA-256 hashes of the deployable package files. `signature/integrity.sig` is an Ed25519 detached signature of that hash manifest. `signature/public_key.pem` is the public verification key.

The private signing key is intentionally not included in this ZIP.

Example verification with OpenSSL 3.x from the package root:

```bash
openssl pkeyutl -verify -pubin -inkey signature/public_key.pem -rawin -in signature/integrity.sha256 -sigfile signature/integrity.sig
sha256sum -c signature/integrity.sha256
```
