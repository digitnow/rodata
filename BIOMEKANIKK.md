# Biomekaniske måling og betraktninger
To kjente systemer, - BioRow (Kleshnev) https://biorow.com og Peach Innovations peachinnovations.com. 

Se artikkel fra 7. november 2025 publisert av BioRow https://biorow.com/rbn2025_10/ 
Kort oppsummert (PI overestimerer verdier):
- PI samler hovedsakelig inn data om svivlevinkler og kraft i svivel (og beregner verdier for slipp i catch og finish)
- BioRow kan også samle data om bladarbeid i vannet, rostil og gjør også avanserte beregninger basert på data fra de spesifikke sensorene
- 3 x 2k, JW8+, step-rate test (8 dataserier per 2k fra takt 20 til 34),
  - PI med 50 Hz (måling hver 1/50 sekund); (1) avlesing av rådata (periodiske data) fra sensorer (tekstil .dat) og lastet inn i BioRow program; tak-data synkronisert og prosessert som "native"-data (2) data fra hver tak (aperiodiske) ble også sammenlignet
  - BiRow med 25 Hz (måling hver 1/25 sekund)
- årebevegelser er kontrollert av roer, mens en svivel er ikke tett koblet til åre og det vil oppstå "kaotiske" bevegelser i catch og finish i forhold til "sleeve" og "button" (se bilde)
- ![Engelsk åre-terminologi](https://github.com/digitnow/rodata/blob/main/docs/images/oars-terminology.png?raw=true)
- påstand fra BioRow er at PI hadde 1.3 grader lengre catch-vinkel og 2.5 grader lenger finish-vinkel enn BioRow (ca. 3.9 grader/3% større sektor med PI)
- PI kraftkurve er forskjøvet mot finish (i forhold til BioRow kraftkurve som baserer målingene fra sensorer i åre og ikke i svivel)
- i begynnelsen av "recovery" viser PI negativ kraft, siden "sleeve" er ikke festet til svivelflaten
- når det nærmer seg catch, kraften i svivelen blir positiv, siden akselerasjon av åre endrer fortegn ("sleeve" må få kontakt med svivelfalten)
- i PI kraften i svivel øker kontinuerlig gjennom "recovery", men i BioRow blir kurven flat (ingen økning)
- kraften målt med PI sensorer er 5.2% høyere
- gjennomsnittlig båtfart 1.8% høyere med PI (målt med GPS)
- dataene fra systemene (PI og BioRow) korrelerer mest på kraft i enkelt tak og gradienten (økningen) til catch kraft, og korrelerer minst (størst forskjell) i maksimal kraft

# Bruk av biomekaniske data
En pågående prosess:
- Hvordan ser det ut? (kartlegging av teknikk, prestasjonsnivå)
- Hva er årsaken?
- Hvordan kan vi jobbe med det?

Teknikk Taktikk

Psykologi Fysiologi

- diverse sensorer er datakilder 
- i programvaren kalles dataserier for "channels"

## Noen bilder fra økt 20251106
![Værdata fra itasmobaws1](https://github.com/digitnow/rodata/blob/main/docs/images/vaerdata-aarungen-20251106-SJ2-.png?raw=true)
Figur 1. Værdata fra itasmobaws1

![Trace i medvin1](https://github.com/digitnow/rodata/blob/main/docs/images/oktaarungen20251106tracemedvind.png?raw=true)
Figur 2. Trace i medvind fra økt 20251106

![Trace i motvind](https://github.com/digitnow/rodata/blob/main/docs/images/oktaarungen20251106tracemotvind.png?raw=true)
Figur 3. Trace i motvind fra økt 20251106


# Om analyse av tidsserier
Mest interesse i sub-serier av store mengder av tidsavhengige dataserier. Man ønsker å se på mønster i data ved hjelp av metoder som
- klassifisering
- prognose / prediksjon
- clustering
- motivrekognisering
- anomalier/avvik

Likhet mellom gjentagende mønstre (som et tak)

# Referanser
- "Everything You Need to Know About Sculling Oars - Angus Rowboats", from angusrowboats.com, last reviewed 2025-11-09
- "Data comparison between BioRow and Peach systems", from https://biorow.com/rbn2025_10/, last reviewed 2025-11-10
- "Row.Team - A conversation with Conny Draper, Sports Biomechanist", 2020,  https://www.youtube.com/watch?v=zqhbk9UYxH8 øast viewed 2025-11-10
