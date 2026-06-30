# Päivyri

Jarmo Aaltosen päivittäinen ajopäiväkirja / kirjaustyökalu.

- Firebase-projekti: `jsailing-f716c` (sama jaettu projekti jota Tilaukset-sovellus käyttää)
- Firestore-kokoelmat: `paivyri_trips`, `paivyri_clients`
- Auth: Google, rajattu osoitteeseen jacke.seilaa@gmail.com
- Deploy: GitHub Pages
- Tietovarasto: Firestore (real-time, synkronoituu kaikkien laitteiden kesken).
  IndexedDB-yhteensopiva shim-kerros pitää vanhan sovelluslogiikan ennallaan.

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
