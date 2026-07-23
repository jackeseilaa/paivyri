# Päivyri

Jarmo Aaltosen päivittäinen ajopäiväkirja / kirjaustyökalu. Nykyinen versio **v8.1.20-dev**.

- Firebase-projekti: `jsailing-f716c` (sama jaettu projekti ja sama Firebase-web-app-rekisteröinti — sama `apiKey`/`appId` — kuin Tilaukset-sovelluksessa)
- Firestore-kokoelmat: `paivyri_trips`, `paivyri_clients`, `paivyri_settings` (yksi dokumentti `company`, yritys-/ajoneuvoasetukset), `paivyri_dev_state_days` (BETA-ominaisuus "Tila", erillinen kokeilu virallisesta ajopäiväkirjasta)
- Auth: Google, rajattu osoitteeseen jacke.seilaa@gmail.com
- Deploy: GitHub Pages (legacy-builder, ei Actions-workflowia — puhdas `git push` riittää)
- Tietovarasto: Firestore (real-time, synkronoituu kaikkien laitteiden kesken).
  IndexedDB-yhteensopiva shim-kerros pitää vanhan sovelluslogiikan ennallaan.

**Deploy oli jumissa v8.1.19-dev:ssä** (GitHub Pagesin build commitille `7d3cb60f`/v8.1.20-dev päättyi `failure`-tilaan 2026-07-05). ✅ **Korjattu 23.7.2026**: uudelleenjulkaisu ajettu, live-sivu vastaa nyt varmennetusti HEAD:iä (v8.1.20-dev, yritysasetusten Firestore-synkka kaikille laitteille).

✅ **Firestore-suojaus tarkistettu 23.7.2026**: tunnistautumaton REST-pyyntö kaikkiin neljään kokoelmaan (`paivyri_trips`, `paivyri_clients`, `paivyri_settings/company`, `paivyri_dev_state_days`) palautti `403 PERMISSION_DENIED` — konsoliin julkaistut säännöt vastaavat käytännössä alla olevaa `firestore.rules`-tiedostoa (yksi sallittu sähköposti per kokoelma, muu oletuksena estetty).

## Deploy

```bash
git add index.html
git commit -m "update"
git push
```

## Firestore-säännöt

Kopioi `firestore.rules`-tiedoston sisältö Firebase-konsolin
(projekti `jsailing-f716c`) Firestore → Rules -välilehdelle ja julkaise.
Säännöt EIVÄT päivity automaattisesti GitHub-pushista - tämä täytyy tehdä
käsin Firebase-konsolissa.
