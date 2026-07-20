# Podcast × TV valuator

Interaktivni dashboard za **oceno vrednosti oglaševanja / pojavnosti na podcastu**, izražene v valuti, ki jo pozna slovenski medijski zakup — **TV GRP in cena na tisoč kontaktov (CPT)**.

Namen: podcast ustvarjalcu (in sponzorju) dati transparenten, uredljiv model, ki pove:
- koliko je vreden doseg po **posameznih omrežjih** (YouTube, FB, IG, TikTok, LinkedIn, X, audio),
- kolikšna je **bruto medijska vrednost** ene epizode,
- koliko bi **enak doseg stal na linearni TV** (GRP-ekvivalent × CPP),
- kakšen je **priporočeni razpon cene sponzorstva** na epizodo.

## Zaženi

Odpri `index.html` v brskalniku. Ni odvisnosti, ni build koraka — vse (podatki, logika, grafi) je v eni datoteki. Deluje offline in ga je mogoče gostiti kjerkoli (GitHub Pages, statični gostitelj).

## Kaj je notri

| Datoteka | Vsebina |
|---|---|
| `index.html` | Celoten interaktivni dashboard (HTML + CSS + JS, brez zunanjih odvisnosti) |
| `data/macarol-show.json` | Realni vzorčni podatki (benchmark vprašalnik Macarol Show, T+30) |
| `docs/metodologija.md` | Podroben opis modela vrednotenja, formul in virov |

## Model na kratko

1. **Doseg → medijska vrednost (CPM).** Vsakemu omrežju/formatu pripišemo tržni CPM; `vrednost = doseg × CPM ÷ 1000`.
2. **Pozornostno uteževanje.** Vsak stik pomnožimo s **pozornostnim koeficientom** platforme (YouTube longplay = 1,00 = TV-referenca, drsni formati manj) → `kakovostni doseg = doseg × utež`. Podlaga: Nielsen The Gauge (YouTube #1 v TV gledanosti) in meritve pozornosti (Amplified Intelligence / Adelaide / Dentsu).
3. **Doseg → GRP-ekvivalent.** `GRP = kakovostni doseg ÷ ciljna skupina × 100`. Ker se SI TV prodaja prek GRP, s tem postavimo podcast na isto os. (Pozornostni model se da izklopiti → računa iz surovega dosega.)
4. **Primerjava na tisoč kontaktov.** `CPT_TV = CPP × 100.000 ÷ ciljna skupina`; efektivni podcast CPM primerjamo s TV CPT.
5. **Kakovostne prilagoditve.** Pribitek za host-read integracijo, netiranje prekrivanja omrežij → priporočeni razpon cene.

### Kredibilnostni učinek (creator) — opcijski modul

Raziskave kažejo, da priporočilo voditelja/creatorja proži **večji oglasni učinek** kot enak TV ali klasični oglas: host-read dvigne nakupno namero za **+50–67 %**, podcast oglas doseže **80 %** priklic (proti 45 % mobilni / 35 % namizni digital), poslušalci so **5×** bolj nagnjeni k angažiranju, Nielsen pa ugotavlja, da influencer programi **presegajo** TV oglase. Modul (privzeto izklopljen, uredljiv multiplikator) izrazi to kot strošek **enakega oglasnega učinka** na TV.

### Relevanca glede na Slovenijo

Doseg epizode in skupnost osebne blagovne znamke sta izražena kot **delež populacije Slovenije** (~2,1 mio, uredljivo) — nacionalni kontekst, ki mu klasičen medijski zakup pogosto ne pripiše teže.

### Zakaj ne vrednotimo vseh platform enako

En ogled cele epizode na YouTubu (ki v tujini nadomešča linearno TV v dnevni sobi) ni enakovreden bežnemu prehodu Reels med drsanjem. Zato platforme utežimo po pozornosti — YouTube in audio nosita TV-primerljivo težo, drsni formati manj. To iz "surovega večkrat ceneje" naredi pošteno primerjavo, ki je tipično blizu **TV parnosti** — verodostojnejši prodajni argument.

Vse predpostavke (ciljna skupina, CPP, CPM po omrežjih, pribitki) so uredljive v vmesniku; grafi in KPI se preračunajo v živo.

## Vzorčni rezultat (Macarol Show, privzete predpostavke)

- Doseg ≈ **554.616 stikov / epizodo** (surovi seštevek platform, T+30)
- Kakovostni (pozornostni) doseg ≈ **208.867** (ø utež ×0,38)
- Bruto medijska vrednost ≈ **€3.235 / epizodo**
- TV-ekvivalent (pozornostni) ≈ **23,2 GRP** = **€2.785** na TV → ≈ **parnost** s TV na tisoč pozornostnih stikov
- Priporočeni razpon cene ≈ **€2.900–4.700 / epizodo** (trenutna dogovorjena cena: €1.500–3.500)

*(Ob izklopljenem pozornostnem modelu: 61,6 GRP = €7.395 in podcast 2,3× ceneje na surovi doseg.)*

> Model ni uradni cenik nobene medijske hiše. Privzeti CPM in CPP so tržne ocene za sidranje pogovora; realne cene se dogovarjajo.
