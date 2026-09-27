# Kommunal tillväxtanalys – SCB

Webbrapport för att analysera samband mellan kommunal befolkningstillväxt och månadsvariabler från SCB.

## Analyslägen

**Alla kommuner – tvärsnitt**
- en observation per kommun
- X = förändring i vald variabel mellan periodens början och slut
- Y = befolkningens förändring under samma period

**En kommun – över tid**
- en observation per kommun och månad
- X och Y jämförs månad för månad
- lag 0–12 månader

**Alla kommuner – kommun × månad**
- panel av kommuner och månader
- använd främst som explorativ analys eftersom både kommunskillnader och tidsvariation blandas

## Variabler

Rapporten hämtar bland annat:
- befolkning
- folkökning
- födelseöverskott
- inrikes inflyttningar
- invandringar/utvandringar
- totalt flyttningsöverskott
- sysselsatta
- arbetslösa
- arbetskraft
- arbetslöshet
- sysselsättningsgrad
- arbetskraftsdeltagande
- sysselsatta efter bransch: totalt, tillverkning, bygg, handel, transport, ICT, företagstjänster, offentlig förvaltning, utbildning samt vård/omsorg
- median disponibel inkomst

SCB:s månadsserie för befolkning finns i en äldre tabell 2000–2024 och en aktuell tabell från 2025. BAS månadsdata finns 2020M01–2026M06 och sysselsatta efter bransch 2020M01–2026M06. Disponibel inkomst i månadsstatistiken är en nyare serie från 2025M01. 

## Varför rapporten inte längre frågar SCB direkt från webbläsaren

Den tidigare versionen skickade POST-frågor direkt från webbläsaren till SCB:s API. Det gav `NetworkError` i browsermiljö.

Den nya versionen använder i stället GitHub Actions:
1. GitHub Action hämtar SCB:s metadata och data server-side.
2. `data.json` byggs.
3. GitHub Pages publicerar den statiska rapporten.
4. Actionen körs automatiskt vardagar och kan även startas manuellt.

Det gör själva rapporten stabil och snabb.

## Publicera

1. Skapa ett GitHub-repository.
2. Lägg filerna i repositoryt.
3. Kör **Actions → Build SCB data → Run workflow**.
4. Därefter körs publiceringen.
5. Under **Settings → Pages** ska Source vara **GitHub Actions**.

