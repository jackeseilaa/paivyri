# Päivyri

Jarmo Aaltosen päivittäinen kirjaustyökalu.

- Firebase projekti: `paivuri`
- Firestore kokoelma: `paivyri/{päivämäärä}`
- Auth: Google (jacke.seilaa@gmail.com)
- Deploy: GitHub Pages

## Deploy

```bash
# Ensimmäinen kerta
git add .
git commit -m "init"
git push

# Päivitykset
git add index.html
git commit -m "update"
git push
```

## Firestore säännöt

Kopioi `firestore.rules` sisältö Firebase-konsolin
Firestore → Rules -välilehdelle.
