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

Privzete vrednosti so realni podatki podcasta **Macarol Show** (povprečje 5 zaporednih epizod, mar–apr 2026). Pomembno: navedene številke so **seštevek stikov po platformah**, ne unikatni doseg (isti človek lahko vidi vsebino na več omrežjih).

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

## 4. Pozornostno uteževanje — zakaj platform ne vrednotimo enako

Doseg ni enakovreden. En ogled cele epizode na **YouTubu** (lean-back, velik zaslon, dolg dwell) ni isto kot bežen prehod Reels med drsanjem. Zato vsakemu stiku pripišemo **pozornostni koeficient** — koliko "TV-vrednega" stika dejansko prinese.

**YouTube longplay = 1,00** je referenca, ker je najbolj TV-podoben in TV dejansko nadomešča:

- Po Nielsenovem **The Gauge (2025)** je YouTube **#1 v TV gledanosti** med vsemi mediji (~12–13 % vsega časa gledanja TV), pred Netflixom; gledanost na TV zaslonu je v dveh letih zrasla za **53 %**.
- Meritve pozornosti (**Amplified Intelligence / Adelaide / Dentsu**) kažejo, da YouTube, CTV in **audio** dosegajo TV-primerljivo pozornost, medtem ko drsni formati (TikTok, Reels, display) za enako pozornost zahtevajo **~2× večji** vložek.

### Privzeti koeficienti (uredljivo)

| Format | Utež | Zakaj |
|---|---|---|
| YouTube longplay | 1,00 | TV-referenca: velik zaslon, dolg dwell, lean-back |
| Spotify / Apple (audio) | 0,85 | pozornost blizu TV; dolgo, a lahko v ozadju |
| Drugi audio | 0,80 | |
| Facebook longplay | 0,55 | daljši video, a pogosto nemi autoplay v feedu |
| LinkedIn | 0,50 | profesionalni kontekst, a feed |
| YouTube Shorts / TikTok | 0,35 | visok completion, a kratek, mobilni scroll |
| Instagram Reels | 0,32 | |
| Facebook Reels | 0,28 | |
| Instagram Story | 0,22 | efemerno, hiter tap-through |
| X / Twitter | 0,18 | impresija ni ogled, nizek dwell |

### Vpliv na model

```
kakovostni_doseg   = Σ (doseg_i × utež_i)
GRP_ekvivalent     = kakovostni_doseg / ciljna_skupina × 100     # ob vklopljenem pozornostnem modelu
strošek_dosega_TV  = GRP_ekvivalent × CPP
```

Ob **izklopljenem** pozornostnem modelu se GRP in strošek računata iz surovega dosega (primerjava "na papirju"). Ob vklopljenem se pokaže poštena, pozornostno izenačena primerjava — tipično blizu **TV parnosti**, kar je močnejši in verodostojnejši argument kot surovi "večkrat ceneje".

## 5. Kakovostne prilagoditve

Surova impresija sistematično **podceni** podcast, zato model doda dva eksplicitna, uredljiva faktorja:

- **Pribitek za host-read integracijo** (privzeto ×1,30) — nativno branje voditelja nosi pozornost in zaupanje, ki ju cenik impresij ne zajame. TV spot je preskočljiv “prekinjevalec”; podcast integracija je vsebina.
- **Netiranje prekrivanja omrežij** (privzeto ×0,80) — ker je doseg seštevek in ne unikat, ta faktor oceni delež dejansko unikatnega dosega (uporabljen v prevodu v TV jezik, ne za napihovanje cene).

```
priporočena_cena_low  = medijska_vrednost × 0,90
priporočena_cena_high = medijska_vrednost × pribitek × 1,12
```

Razpon je namenoma pogajalsko okno, ne ena sama točka.

## 6. Parametri ciljne skupine in TV (uredljivo)

| Parameter | Privzeto | Opomba |
|---|---|---|
| Ciljna skupina | 900.000 (odrasli 18–54) | ali ~1,9 mio (vsi 4+); manjša skupina → več GRP na isti doseg |
| CPP (cena GRP) | €120 | SI razpon ≈ 25–200 € (POP TV najvišji) |
| Referenčni 30-sek. spot (prime) | €3.000 | za prevod v “koliko TV spotov”; POP TV prime do ~7.000 € |

## 7. Omejitve

- Model **ni uradni cenik** nobene medijske hiše. Privzeti CPM, CPP in pozornostni koeficienti so tržne/raziskovalne ocene za sidranje pogovora.
- Doseg je seštevek stikov, ne merjen unikatni doseg; surovi GRP-ekvivalent je zato zgornja ocena “dosega” (pozornostni model ga korigira navzdol).
- Pozornostni koeficienti so izpeljani iz javnih meritev pozornosti in gledanosti, ne iz panelne meritve tega konkretnega podcasta.
- Namen je **argumentacija vrednosti**, ne dokončna cenitev.

## 8. Viri

- Omisli.si — [TV oglaševanje cena 2026](https://omisli.si/oglasevanje-marketing/tv-oglasevanje/cene/)
- Pro Plus / POP TV — [Pogoji prodaje 2026](https://www.24ur.com/s/Cf3gbX)
- Castoola — [valute merjenja gledanosti in zakupa TV](https://castoola.com/sl/valute-merjenja-gledanosti-in-zakupa-tv/)
- RTV SLO — [prodajni pogoji za oglaševanje](https://www.rtvslo.si/files/marketing/prodajni_pogoji_2017_javna_objava-__istopis.pdf)
- Nielsen — [The Gauge: YouTube ohranja največji delež TV gledanosti (2025)](https://www.nielsen.com/news-center/2025/youtube-maintains-largest-share-of-tv-viewing-among-media-companies-for-third-consecutive-month/)
- Amplified Intelligence / Adelaide — [meritve pozornosti po platformah](https://www.westwoodone.com/blog/2024/08/12/adelaide-attentiveness-measurement-1000-of-am-fm-radio-ads-require-2635-worth-of-facebook-ads-to-achieve-the-same-level-of-attention-audio-platforms-generate-nearly-the-same-attentiveness-as-tv/)
- AGB Nielsen Slovenija — merjenje gledanosti TV
- Interni benchmark vprašalnik in tabela dosegov Macarol Show (2026)
