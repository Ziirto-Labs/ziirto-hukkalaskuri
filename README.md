# Ziirto HukkaLaskuri

> Toimialakohtainen piilohukan suuruusluokka-arvio sisälogistiikan myyntityökaluksi.

**Käytössä:** Ziirto Oy:n myyntihenkilöstö asiakaskeskusteluissa.
**Tuottaa:** 2-sivuinen PDF-raportti asiakkaan johtoryhmälle.
**Tukee:** Rakentaminen, FMCG / Logistiikka, Teollisuus / Valmistus.

## Käyttötarkoitus

HukkaLaskuri on Ziirton myyntityökalu. Toni tai Tommi täyttää laskurin asiakkaan
tiedoilla, ja työkalu tuottaa 2-sivuisen tutkimusperusteisen raportin
piilohukan suuruusluokasta. Raportti **avaa keskustelun** piilohukan
suuruudesta, ei sulje sitä myyntiviestiin.

Laskuri tukee kolmea toimialaa:

- **Rakentaminen** — talonrakennus ja laivanrakennus (ETO-tuotanto)
- **FMCG / Päivittäistavaralogistiikka** — varastointi, keräily, tilausvirta
- **Teollisuus / Valmistus** — materiaalituotanto, prosessiteollisuus

## Käyttö

### Verkossa (GitHub Pages)

Avaa: `https://<kayttaja>.github.io/ziirto-hukkalaskuri/`

URL päivittyy kun GitHub Pages -deploy on aktivoitu repon asetuksista.

### Paikallisesti (kehitys)

```bash
git clone git@github.com:<kayttaja>/ziirto-hukkalaskuri.git
cd ziirto-hukkalaskuri
npx http-server -p 8000 -c-1
```

Avaa selaimessa: `http://localhost:8000/`

**Huom:** Älä avaa `index.html`-tiedostoa suoraan kaksoisklikkaamalla.
Selaimien `file://`-rajoitukset estävät joitakin tulostustoimintoja.

## Raportin tulostus

1. Täytä asiakkaan nimi ja laskurin parametrit
2. Klikkaa **"Avaa raportti tulostukseen"**
3. Selaimen tulostusesikatselu avautuu
4. Valitse:
   - **Microsoft Print to PDF** tai **Tallenna PDF:nä** → tallentaa tiedoston
   - Oikea tulostin → tulostaa fyysisen kopion
5. Asetukset:
   - Paperikoko: **A4**
   - Suunta: **Pysty**
   - Marginaalit: **Ei mitään** tai **Oletus**
   - **Taustagrafiikka: PÄÄLLÄ** (kriittinen — muuten siniset taustat eivät näy)

## Tekninen toteutus

- **Yhden HTML-tiedoston SPA** — ei build-prosessia, ei npm:ää
- **Inter Tight** fontti Google Fontsista, fallback systeemifontteihin
- **Selaimen oma tulostus PDF:ksi** (`window.print()` + `@media print`)
- **Deterministinen laskenta** — ei AI-kutsuja, sama syöttö → sama tulos
- **Deterministinen sanallistus** — tutkimusperusteiset template-pohjat
- **SVG-logo upotettu** suoraan HTML:ään, ei verkkopyyntöjä
- **Ziirton brändivärit** v2.0 graafisen ohjeen mukaisesti

## Brändi

| Väri | Hex | Käyttö |
|---|---|---|
| Tutkimus | `#002337` | Pääbrändiväri, otsikot, headline-laatikko |
| Tekeminen | `#EB506E` | CTA, korostukset, raportin kontaktilaatikko |
| Teknologia | `#D0CAC6` | Neutraalit aksentit |
| Korostevärit | `#AAFAB4` | Positiiviset tulokset |

**Fontti:** Inter Tight (700/800 otsikot, 400/500 leipä)

## Laskentaperiaatteet

Kaikki kertoimet ovat tutkimuspohjaisia keskiarvoja, eivät tarkkoja mittauksia.

| Lähde | Käyttö |
|---|---|
| Fieldwire / Hilti | Rakentamisen 8 hukkaa, wasteRatio 28–45 % |
| McKinsey Supply Chain 2017 | FMCG hukka, ostotilausvirheaste 8 % |
| Cadre Tech / Dematic | Keräilyautomaation virhevähennys 85 % |
| eMoldino 2025 | Materiaalihukka 2,2 % liikevaihdosta |
| Kela 2023 | Sairauspoissaolokeskiarvo 9,5 pv/hlö/v |
| Gallup Q12 | Engagement-poissaolokorrelaatio 30–60 % |
| Crosby / ITT Corporation | PONC 25 % → 6 % liikevaihdosta |
| Taylor & Francis 2025 | 41 % poikkeamatoistuvuus |
| ASCE 2026 | Rework aliraportoitu 4× |
| Industry-Science 2025 | Laivanrakennuksen suunnittelumuutokset |
| SSI 2017 | Sister ship -ongelma |
| Hypertherm 2024 | Ergonomiakuorman vaikutus virheisiin |

## Roadmap

### v1.0 — Nykyinen (toukokuu 2026)

- Kolme toimialaa: Rakentaminen (talo + laiva), FMCG, Teollisuus
- Dual Input (slider + inline-edit klikkaamalla)
- 2-sivuinen PDF-raportti, neljä kappaletta sanallistusta sivulla 1
- Henkilöstöriski- ja merkityksellisyyspaneeli
- Ziirton brändi v2.0
- Selaimen oma tulostus, ei kolmannen osapuolen kirjastoja

### v1.1 — Suunniteltu

- Mobiilioptimointi tarkemmin
- Useampien asiakkaiden vertailu samalla istunnolla
- localStorage-persistenssi (valinnainen)
- Lisää toimialoja (mahdolliset: terveydenhuolto, kauppa, julkinen)

### v2.0 — Visio

- React + TypeScript -refaktori (jos käytön volyymi nousee tarpeeksi)
- MyZiirto-integraatio (PT-portaali)
- Rekla+ -kytkös: laskuri antaa potentiaalin, Rekla+ mittaa todellisuuden
- Asiakaskäyntiraportit historiakannassa

## Tekijät

| Rooli | Henkilö |
|---|---|
| Alkuperäinen spec | Mika Eskola, Ziirto Oy |
| Laajennus, sanallistus, brändi | Toni Salminen, Ziirto Oy |
| Tekninen toteutus | Claude (Anthropic) |

## Poikkeamat alkuperäisestä speksistä

Mika Eskolan alkuperäinen kehotus ehdotti React + TypeScript + Vite + Tailwind
+ Recharts -stackia. Toteutus on vanilla HTML + JS tuotantopolun yksinkertaisuuden
takia. Muut poikkeamat:

- Värit: Ziirton oikeat brändivärit, ei Nexus-teal
- Fontti: Inter Tight, ei Cabinet Grotesk + Satoshi
- Kaaviot: yksinkertaiset div-palkit, ei Recharts
- Pois: dark mode, radar-kaavio, localStorage
- Lisätty: asiakkaan nimi -kenttä, PDF-raportti, sanallistus, Crosby ITT -vertailu

## Lisenssi

Sisäinen Ziirto Oy:n työkalu. Ei julkista lisenssiä. Kaikki oikeudet pidätetään.

© 2026 Ziirto Oy
