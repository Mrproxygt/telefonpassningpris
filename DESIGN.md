# DESIGN.md — telefonpassningpris.se

Satellit i Menodis nätverk. Vinkel: **prisjämförelse-hub** för sökfrasen "telefonpassning pris" — inte en produktsida, utan en oberoende-klingande guide som jämför svarsservice / callcenter / anställd / AI och landar läsaren hos Menodi.

## 1. Brand-identitet

- **Paper**: `#F9F7F2` (bakgrund), `#EFEBE1` (paper-mid, alternerande sektion/tabellhuvud)
- **Ink**: `#141412` (text), `rgba(20,20,18,.62)` (ink-60, brödtext/sub)
- **Accent (deep green)**: `#007C4C` (primär), `#005937` (accent-deep, hover/länkar), `#F2F8F4` (highlight-rad-tint), `#7FC8A6` (eyebrow på mörk botten)
- **Rule**: `rgba(20,20,18,.14)` — alla borders
- **Typografi**: rubriker i **Georgia/Times New Roman serif** (auktoritet, "oberoende rapport"-känsla), brödtext i **system-sans** (Segoe UI/-apple-system) för läsbarhet på skärm. H1 `clamp(34px,5.4vw,56px)`, tight letter-spacing (`-.015em`).
- **Ton**: säljande men saklig — sifferdrivet, källhänvisande, korta stycken, inga utropstecken. Skriver som en oberoende prisjämförare, inte som Menodis reklam (trust genom distans).

## 2. Sektionsplan (uppifrån-ner)

1. **Sticky header** — halvtransparent (blur), logo "Telefonpassning**pris**.se" + CTA-knapp. Behålls som är, lägg till 1 nav-ankare extra ("Priser", "Räkna själv") för sekundär nav.
2. **Hero** — eyebrow ("Prisguide · uppdaterad") + H1 + lede + "Snabbt svar"-ruta (featured-snippet-bete) + trust-chips (t.ex. "Oberoende sammanställning", "Uppdaterad juli 2026", "4 lösningar jämförda"). Lägg till sekundär CTA bredvid huvud-CTA.
3. **Prisjämförelsetabell** — kärnan i sidan. 4 rader (svarsservice/callcenter/receptionist/AI), highlight-rad på AI. Behålls, städa kolumnbredd för mobil.
4. **Räkneexempel** — 3-korts grid, "vad kostar ett missat samtal". Behålls oförändrat, stark konverterande logik.
5. **Vad påverkar priset** — faktor-lista (2-kolumns), fungerar som "så funkar det"-ersättning givet hub-vinkeln (inga numrerade produktsteg behövs — lägg istället in en liten numrerad "Så räknar du ut ditt pris" 3-stegsmodul ovanför faktorerna för att möta briefens "numrerade steg"-krav).
6. **Stats-band** — NYTT: bryt ut 3-4 verifierade siffror (28–50k receptionist, 15–35kr/samtal, 40-50k/mån) i eget kompakt band med källrad ("Källa: sammanställning juli 2026, se metodik i footer") mellan tabell och räkneexempel.
7. **FAQ accordion** — 5 frågor, behålls (matchar FAQPage JSON-LD 1:1 — rör ej ordning/text utan att uppdatera schema parallellt).
8. **Slutlig CTA-band** (mörk `--ink` bakgrund) — behålls, dubbel knapp (demo + läs mer).
9. **Flerkolumns-footer** — UPPGRADERA från nuvarande enkelrad till 3 kolumner: Om sajten/metodik, Jämför (länkar till andra Menodi-satelliter vid behov), Menodi-hänvisning + uppdateringsdatum.

## 3. Vad BEHÅLLS från nuvarande version

- Hela **FAQ-innehållet** (5 frågor/svar) + FAQPage JSON-LD — verifierat och SEO-bärande, ändra inte utan att synka schema.
- **Prisjämförelsetabellens siffror**: 1 000–5 000 kr/mån (svarsservice), 15–35 kr/samtal, 5 000–20 000+ kr/mån (callcenter), 40 000–50 000 kr/mån (receptionist), "fast pris från några hundralappar" (AI).
- **Räkneexempel-siffrorna**: 8 000 kr/jobb, 4 av 10 missade samtal, >30×.
- **"Vad påverkar priset"-faktorerna** (6 punkter) — saklig, ej säljig, behåll som trust-signal.
- **IntersectionObserver reveal-scriptet** — fungerar, återanvänd rakt av.
- Alla `rel="sponsored"` UTM-länkar till menodi.se — behåll UTM-schema, bygg ut med fler ankare vid behov.

## 4. Mockup-bildplan (placeholders)

- **Hero**: ingen produktskärmdump (hub ≠ produktsida) — istället en liten inline-SVG "kalkylator-ikon" eller stiliserad prisgraf-illustration bredvid H1 på desktop (valfri, kan skippas för renodlad textkonvertering).
- **Stats-band**: ingen bild, rena siffror + källrad.
- **Faktorer-sektion**: 6 st små inline-SVG-ikoner (telefon, klocka, kalender, lås, flagga, plugg) — en per faktor, ersätter nuvarande punkt-prickar.
- **FAQ/CTA**: inga bilder — text bär sektionen.

## 5. Unika differentierare mot övriga 10 satelliter

- Enda satelliten byggd som **jämförelse-hub med prisTABELL** (övriga är produkt/kategori-fokuserade: aisvarstjanst.se, aitelefonsvarare.se etc. säljer "vad är X", inte "vad kostar X").
- Explicit **"oberoende sammanställning"-positionering** — sänker garden, ökar trust innan CTA.
- **Räkneexempel/ROI-logik** (missat samtal → 30× kostnad) är unikt konverteringsgrepp, inte återanvänt på övriga satelliter.
- Serif+cream+green identitet ska vara **denna sajts unika visuella fingeravtryck** i nätverket — kontrollera att ingen av de andra 10 redan äger samma paper/green-kombo innan lansering.
