# KilpailuKalenteri – Prototyyppi v1

Selainkäyttöinen käyttöliittymäprototyyppi **Suomen Frisbeegolfliiton** kilpailukalenterille ja hakemusten hallinnalle.  
Ei backend-riippuvuuksia, ei tietokantaa, ei autentikointia – pelkkä frontend mock-datalla.

**Ulkoiset riippuvuudet (CDN):** Leaflet 1.9.4 (kartta) + OpenStreetMap-taustakartta.

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

## 🧭 Navigaation osiot

### Etusivu
Yleiskatsaus prototyypistä ja lyhyt kuvaus jokaisesta osiosta.

### Hakemukset *(vain työroolit)*
Kanban-taulu, jossa hakemukset on ryhmitelty elinkaaren tilojen mukaan sarakkeisiin.
- Haku nimellä, paikkakunnalla, tasolla tai radalla
- Suodatus kilpailutason (A/B/C/L-tier) ja elinkaaren tilan mukaan
- Hakemuksen valitseminen avaa yksityiskohtapaneelin elinkaariaskelmalla
- **"+ Uusi hakemus"** -painike avaa hakemuslomake-mockunäkymän omana sivuna

### Uusi hakemus *(lomakemockup)*
Täysikokoinen hakemussivunäkymä, jossa 11 accordion-osioita:
1. Hakemuksen ohjeistus (kustannukset, linkit, yhteystiedot)
2. Hakijan yhteystiedot
3. Kilpailun perustiedot
4. Kilpailun yhteystiedot (julkaistavat)
5. Kilpailun toimihenkilöt (TD ja apu-TD)
6. Aikataulu
7. Kilpailun tyyppi, taso, muoto ja luokat
8. Pros Playing Am
9. Paikallis- ja erikoissäännöt
10. Kilpailun maksut ja palkinnot
11. Faciliteetit

> Huom: Lomake on mockup – tietoja ei tallenneta. "Tallenna luonnos" ja "Lähetä hakemus" näyttävät vain toast-ilmoituksen.

### Kalenteri
Hyväksytyt ja julkiset kilpailut korttinäkymänä. Korttia klikkaamalla avautuu kilpailun lisätietomodaali.
Kuukausinavigointi: ←/→ -nuolet, "Kaikki tulevat kilpailut" ja "Nykyinen kuukausi".

### Lista
Tiivis taulukkonäkymä julkisista kilpailuista samoilla kuukausinavigointisuodattimilla.
Riviä klikkaamalla avautuu kilpailun lisätietomodaali.

### Kartta
Kilpailut paikkakunnittain Leaflet + OpenStreetMap -kartalla.
- Yksi ympyrämarkeri per paikkakunta; markerin koko kasvaa kilpailumäärän mukaan
- Markeria klikkaamalla avautuu popup, jossa paikkakunnan kilpailut linkkeinä lisätietomodaaliin
- Kuukausinavigointisuodattimet käytössä kuten Kalenterissa ja Listassa

---

## 🗺️ Karttakoordinaatit

Tuetut paikkakunnat (koordinaatit kovakoodattu `CITY_COORDS`-objektiin):
Espoo, Helsinki, Hämeenlinna, Joensuu, Jyväskylä, Kajaani, Kotka, Kouvola, Kuopio,
Lahti, Mikkeli, Oulu, Pori, Rovaniemi, Seinäjoki, Tampere, Turku, Vaasa.

Puuttuvat paikkakunnat tulostetaan varoituksena selaimen konsoliin.

---

## 👥 Roolit

| Rooli            | Oletusnäkymä | Hakemukset | Kalenteri | Lista | Kartta |
|------------------|-------------|------------|-----------|-------|--------|
| Admin            | Etusivu     | ✅          | ✅         | ✅    | ✅      |
| Liitto           | Etusivu     | ✅          | ✅         | ✅    | ✅      |
| Kilpailunjohtaja | Etusivu     | ✅          | ✅         | ✅    | ✅      |
| Kilpailija       | Etusivu     | ❌          | ✅         | ✅    | ✅      |
| Yleisö           | Etusivu     | ❌          | ✅         | ✅    | ✅      |

Roolia vaihdetaan yläpalkin pudotusvalikosta – käyttäjähallintaa ei ole.  
Työroolit (Admin, Liitto, Kilpailunjohtaja) näkevät kaikki hakemukset tiloista riippumatta.  
Julkiset roolit (Kilpailija, Yleisö) näkevät vain **Julkaistu**-tilaiset kilpailut.

---

## 🏅 Kilpailutasot ja värikoodit

| Taso   | Väri           |
|--------|---------------|
| A-tier | Violetti       |
| B-tier | Sininen        |
| C-tier | Syaani         |
| L-tier | Vihreä         |

---

## 📊 Hakemuksen statukset ja värikoodit

| Status       | Väri          | Kuvaus                         |
|-------------|---------------|-------------------------------|
| Luonnos      | Harmaa        | Kesken, ei lähetetty           |
| Lähetetty    | Sininen       | Odottaa käsittelyä             |
| Käsittelyssä | Keltainen     | Liitto/Admin käsittelee       |
| Hyväksytty   | Vihreä        | Vahvistettu, ei vielä julkinen |
| Julkaistu    | Tumman vihreä | Julkinen, näkyy kaikille      |
| Hylätty      | Punainen      | Ei hyväksytty                  |

---

## 🔮 Myöhempiin vaiheisiin jätetty (tarkoituksella)

- Tietokantaintegraatio (MySQL)
- Käyttäjähallinta ja autentikointi
- Hakemuksen tietojen tallennus ja editointi
- Workflow-toiminnot (tilanmuutokset, kommentointi, hyväksynnät)
- Hakemusten massatuonti tiedostosta
- Roolikohtaiset näkyvyyssäännöt hakemuksen kentille
- Backend API -integraatio
