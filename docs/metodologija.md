# Metodologija: vrednotenje pojavnosti na podcastu v TV valuti

Ta dokument razloži, kako dashboard oceni vrednost oglaševanja na podcastu in ga naredi primerljivega s TV oglaševanjem na slovenskem trgu.

## 1. Izhodišče: dve valuti

| Medij | Kako se prodaja | Valuta |
|---|---|---|
| **Linearna TV** (POP TV, Kanal A, Planet TV, TV SLO) | zakup **GRP** (Gross Rating Points) po ciljni skupini; cena spota po dolžini prek faktorja | **CPP** — cena ene GRP točke |
| **Digital / podcast** | impresije / ogledi po formatu | **CPM** — cena na 1000 impresij |

- **1 GRP = 1 % dosežene ciljne skupine.** Gledanost meri AGB Nielsen.
- Da sta medija primerljiva, podcast doseg pretvorimo v **GRP-ekvivalent** in oba izrazimo kot **ceno na tisoč doseženih (CPT/CPM)**.

## 2. Vhodni podatki (na epizodo)

Za vsako omrežje/format:
- **Doseg (T+30)** — stiki 30 dni po objavi (nativni števci platform; audio = streams/plays).
- **CPM (€)** — tržna cena na 1000 impresij za ta format.

Privzete vrednosti so realni podatki oddaje **Macarol Show** (povprečje 5 zaporednih epizod, mar–apr 2026). Pomembno: navedene številke so **seštevek stikov po platformah**, ne unikatni doseg (isti človek lahko vidi vsebino na več omrežjih).

### Privzeti CPM po formatih (tržne ocene, uredljivo)

| Format | CPM (€) | Zakaj |
|---|---|---|
| Spotify / Apple (audio, host-read) | 25 | premijska pozornost, nativno branje |
| Drugi audio | 18 | |
| YouTube longplay | 12 | dolga pozornost, in-content |
| LinkedIn | 12 | premijsko B2B občinstvo |
| Instagram Reels / FB longplay | 6 | |
| Instagram Story | 5 | |
| YouTube Shorts / FB Reels / TikTok | 4 | kratki, hitro drseč format |
| X / Twitter (impresije) | 3 | |

## 3. Formule

```
medijska_vrednost      = Σ (doseg_i × CPM_i / 1000)        # bruto, po omrežjih
GRP_ekvivalent         = doseg / ciljna_skupina × 100
CPT_TV                 = CPP × 100.000 / ciljna_skupina    # € / 1000 kontaktov na TV
strošek_dosega_na_TV   = GRP_ekvivalent × CPP              # = doseg/1000 × CPT_TV
efektivni_CPM_podcast  = medijska_vrednost / doseg × 1000
stroškovna_učinkovitost= CPT_TV / efektivni_CPM_podcast    # kolikokrat ceneje je podcast
```

Ekvivalenca `strošek_dosega_na_TV = GRP × CPP` sledi iz tega, da je 1 GRP = `ciljna_skupina / 100` kontaktov — obe poti (prek GRP ali prek CPT) dasta isti znesek.

## 4. Kakovostne prilagoditve

Surova impresija sistematično **podceni** podcast, zato model doda dva eksplicitna, uredljiva faktorja:

- **Pribitek za host-read integracijo** (privzeto ×1,30) — nativno branje voditelja nosi pozornost in zaupanje, ki ju cenik impresij ne zajame. TV spot je preskočljiv “prekinjevalec”; podcast integracija je vsebina.
- **Netiranje prekrivanja omrežij** (privzeto ×0,80) — ker je doseg seštevek in ne unikat, ta faktor oceni delež dejansko unikatnega dosega (uporabljen v prevodu v TV jezik, ne za napihovanje cene).

```
priporočena_cena_low  = medijska_vrednost × 0,90
priporočena_cena_high = medijska_vrednost × pribitek × 1,12
```

Razpon je namenoma pogajalsko okno, ne ena sama točka.

## 5. Parametri ciljne skupine in TV (uredljivo)

| Parameter | Privzeto | Opomba |
|---|---|---|
| Ciljna skupina | 900.000 (odrasli 18–54) | ali ~1,9 mio (vsi 4+); manjša skupina → več GRP na isti doseg |
| CPP (cena GRP) | €120 | SI razpon ≈ 25–200 € (POP TV najvišji) |
| Referenčni 30-sek. spot (prime) | €3.000 | za prevod v “koliko TV spotov”; POP TV prime do ~7.000 € |

## 6. Omejitve

- Model **ni uradni cenik** nobene medijske hiše. Privzeti CPM in CPP so tržne ocene za sidranje pogovora.
- Doseg je seštevek stikov, ne merjen unikatni doseg; GRP-ekvivalent je zato zgornja ocena “dosega”.
- Primerjava kakovosti kontakta (pozornost, dokončanje, kontekst) je zajeta le prek pavšalnih pribitkov — ne prek panelnih meritev.
- Namen je **argumentacija vrednosti**, ne dokončna cenitev.

## 7. Viri

- Omisli.si — [TV oglaševanje cena 2026](https://omisli.si/oglasevanje-marketing/tv-oglasevanje/cene/)
- Pro Plus / POP TV — [Pogoji prodaje 2026](https://www.24ur.com/s/Cf3gbX)
- Castoola — [valute merjenja gledanosti in zakupa TV](https://castoola.com/sl/valute-merjenja-gledanosti-in-zakupa-tv/)
- RTV SLO — [prodajni pogoji za oglaševanje](https://www.rtvslo.si/files/marketing/prodajni_pogoji_2017_javna_objava-__istopis.pdf)
- AGB Nielsen Slovenija — merjenje gledanosti TV
- Interni benchmark vprašalnik in tabela dosegov Macarol Show (2026)
