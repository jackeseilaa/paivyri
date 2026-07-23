# Päivyri

Jarmo Aaltosen päivittäinen ajopäiväkirja / kirjaustyökalu. Nykyinen versio **v8.1.20-dev**.

- Firebase-projekti: `jsailing-f716c` (sama jaettu projekti ja sama Firebase-web-app-rekisteröinti — sama `apiKey`/`appId` — kuin Tilaukset-sovelluksessa)
- Firestore-kokoelmat: `paivyri_trips`, `paivyri_clients`, `paivyri_settings` (yksi dokumentti `company`, yritys-/ajoneuvoasetukset), `paivyri_dev_state_days` (BETA-ominaisuus "Tila", erillinen kokeilu virallisesta ajopäiväkirjasta)
- Auth: Google, rajattu osoitteeseen jacke.seilaa@gmail.com
- Deploy: GitHub Pages (legacy-builder, ei Actions-workflowia — puhdas `git push` riittää)
- Tietovarasto: Firestore (real-time, synkronoituu kaikkien laitteiden kesken).
  IndexedDB-yhteensopiva shim-kerros pitää vanhan sovelluslogiikan ennallaan.

⚠️ **Viimeisin deploy epäonnistui**: GitHub Pagesin build commitille `7d3cb60f` (v8.1.20-dev, 2026-07-05) päättyi `failure`-tilaan. ✅ **Tarkistettu 23.7.2026**: live-sivu palvelee tällä hetkellä versiota **v8.1.19-dev**, ei repon HEAD:iä. HEAD:in muutos (yritysasetusten Firestore-synkka kaikille laitteille) ei siis ole vielä oikeasti julkaistuna — kannattaa yrittää uudelleenjulkaisua (esim. tyhjä commit tai Settings → Pages).

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
