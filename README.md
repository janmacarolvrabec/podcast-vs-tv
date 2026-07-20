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
2. **Doseg → GRP-ekvivalent.** `GRP = doseg ÷ ciljna skupina × 100`. Ker se SI TV prodaja prek GRP, s tem postavimo podcast na isto os.
3. **Primerjava na tisoč kontaktov.** `CPT_TV = CPP × 100.000 ÷ ciljna skupina`; efektivni podcast CPM primerjamo s TV CPT.
4. **Kakovostne prilagoditve.** Pribitek za host-read integracijo, netiranje prekrivanja omrežij → priporočeni razpon cene.

Vse predpostavke (ciljna skupina, CPP, CPM po omrežjih, pribitki) so uredljive v vmesniku; grafi in KPI se preračunajo v živo.

## Vzorčni rezultat (Macarol Show, privzete predpostavke)

- Doseg ≈ **554.616 stikov / epizodo** (seštevek platform, T+30)
- Bruto medijska vrednost ≈ **€3.235 / epizodo**
- TV-ekvivalent ≈ **61,6 GRP** = **€7.395**, če bi doseg kupil na TV
- Priporočeni razpon cene ≈ **€2.900–4.700 / epizodo** (trenutna dogovorjena cena: €1.500–3.500)

> Model ni uradni cenik nobene medijske hiše. Privzeti CPM in CPP so tržne ocene za sidranje pogovora; realne cene se dogovarjajo.
