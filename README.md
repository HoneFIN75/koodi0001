# KilpailuKalenteri – Prototyyppi v1

Selainkäyttöinen käyttöliittymäprototyyppi kilpailukalenterille.  
Ei backend-riippuvuuksia, ei tietokantaa, ei autentikointia – pelkkä frontend mock-datalla.

---

## 🚀 Käynnistys

### Vaihtoehto 1 – Suoraan selaimessa (nopein)

Avaa tiedosto suoraan selaimessa:

```
index.html
```

Kaksoisnapsauta tiedostoa tai vedä se selainikkunaan. Toimii kaikilla moderneilla selaimilla
(Chrome, Edge, Firefox, Safari).

### Vaihtoehto 2 – Paikallinen kehityspalvelin (suositus)

Jos sinulla on Node.js asennettuna:

```bash
npx serve .
```

tai Python:

```bash
python3 -m http.server 8080
```

Avaa sen jälkeen selaimessa: `http://localhost:8080`

---

## 🗂️ Rakenne

```
koodi0001/
└── index.html    ← koko prototyyppi yhdessä tiedostossa (HTML + CSS + JS)
```

---

## 👥 Roolit

| Rooli            | Oletusnäkymä | Hakemukset | Kalenteri | Lista | Kartta |
|------------------|-------------|------------|-----------|-------|--------|
| Admin            | Hakemukset  | ✅          | ✅         | ✅    | ✅      |
| Liitto           | Hakemukset  | ✅          | ✅         | ✅    | ✅      |
| Kilpailunjohtaja | Hakemukset  | ✅          | ✅         | ✅    | ✅      |
| Kilpailija       | Kalenteri   | ❌          | ✅         | ✅    | ✅      |
| Yleisö           | Kalenteri   | ❌          | ✅         | ✅    | ✅      |

Roolia vaihdetaan yläpalkin pudotusvalikosta – käyttäjähallintaa ei ole.

---

## 📊 Hakemuksen statukset ja värikoodit

| Status       | Väri     | Kuvaus                         |
|-------------|----------|-------------------------------|
| Luonnos      | Harmaa   | Kesken, ei lähetetty           |
| Lähetetty    | Sininen  | Odottaa käsittelyä             |
| Käsittelyssä | Keltainen | Liitto/Admin käsittelee       |
| Hyväksytty   | Vihreä   | Vahvistettu, ei vielä julkinen |
| Julkaistu    | Tumman vihreä | Julkinen, näkyy kaikille  |
| Hylätty      | Punainen | Ei hyväksytty                  |

---

## 🔮 Myöhempiin vaiheisiin jätetty (tarkoituksella)

- Tietokantaintegraatio (MySQL)
- Käyttäjähallinta ja autentikointi
- Oikea karttapalvelu (Leaflet / Google Maps)
- Hakemuksen täysi lomake ja editointi
- Workflow-toiminnot (tilanmuutokset, kommentointi, hyväksynnät)
- Hakemusten massatuonti tiedostosta
- Hakemuksen tietojen näkyvyyssäännöt roolikohtaisesti
- Suodatus ja hakutoiminnot
- Backend API -integraatio
