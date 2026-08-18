# Ombra Prime — världen

En sida som förklarar världen för någon som inte vet någonting om den. Den
sitter före simulatorsidan i kedjan: **först vad Ombra Prime är, sedan hur
den byggs.**

| | |
|---|---|
| Publicerad | <http://ombraprime.com/ombra-prime-varlden/> |
| Repo | `steffost/ombra-prime-varlden`, GitHub Pages från `main` |
| Går vidare till | <http://ombraprime.com/ombra-prime/simulator.html> |

Domänen sitter på `steffost/steffost.github.io` (CNAME `ombraprime.com`), så
varje projektrepo med Pages påslaget hamnar automatiskt på
`ombraprime.com/<reponamn>/`. Det här repot behövde alltså ingen egen
domänkonfiguration.

## Filerna

Tre stycken, och det är hela sajten.

- `index.html` — allt. Struktur, stil och text i en fil, ingen byggkedja.
- `ombra-prime.jpg` — moderskeppet, 2000 px brett, 128 kB. Nedskalad från
  originalet i `Downloads/OmbraPrime_00.jpeg_2K_202608151923.jpeg` med
  `ffmpeg -vf scale=2000:-2 -q:v 4`.
- `.nojekyll` — säger åt Pages att servera filerna rakt av.

## Att veta innan den ändras

**Sidan har ett enda tema.** Simulatorsidan har tre — ljust, mörkt och system
— därför att den är ett dokument. Den här är rymden utanför skrovet, och den
ska se likadan ut hos alla. Alla färger står därför en gång på `:root`, och
det finns med flit varken `prefers-color-scheme` eller `[data-theme]`.
Lägger man till en färg någon annanstans bryter man den regeln.

**Ingen webbfont laddas.** Displayen är Bahnschrift med DIN- och
systemreserver, brödtexten är Charter med Georgia-reserv. Det gör att sidan
ser lite olika ut på olika system, och det är billigare än en tyst reserv som
slår ut hela typografin.

**Bilden bär rubriken.** Namnet OMBRA PRIME står i själva bilden, så det finns
ingen `<h1>` ovanpå den. Byts bilden mot en utan text måste rubriken tillbaka.

**Siffrorna kommer ur lagtexten**, inte ur simulatorns tillstånd — 16,9 km,
6 km, 100 000 invånare, tredje generationen. De står i
`canon/laws/01-skeppet.md` och `03-samhalle.md` i simulatorrepot, och ändras
bara om lagen ändras. Det är skillnaden mot simulatorsidan, vars siffror är
avlästa och åldras.

## Publicera om

```bash
git add -A && git commit -m "…" && git push
```

Pages bygger om av sig självt och tar en minut eller två. Kontrollera med
`curl -sI http://ombraprime.com/ombra-prime-varlden/` innan du tror att det
gått igenom.

## Var resten ligger

Själva simulatorn — koden som genererar världen, radion, romanen — bor i
`I:\OmbraPrimeSimulator` (`steffost/OmbraPrimeSimulator`, privat). Sidan som
förklarar den bor i `steffost/ombra-prime`. Det här repot vet ingenting om
någotdera; den enda kopplingen är länken i `index.html`.
