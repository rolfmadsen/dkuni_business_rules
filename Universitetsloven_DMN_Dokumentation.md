# **Implementering af Decision Model and Notation (DMN) for Universitetsloven**

## **Indledning**

Formålet med dette dokument er at præsentere en fuldstændig dokumentation af Universitetsloven ved hjælp af Decision Model and Notation (DMN). Ved at modellere lovens bestemmelser i DMN skaber vi en struktureret og klar repræsentation af de forretningsregler, der styrer universitetets drift. Dette vil understøtte vores arbejde med procesoptimering, applikationsintegrationer og sikre, at vi overholder lovgivningen i vores daglige aktiviteter.

## **Formål med at bruge DMN**

- **Standardisering**: DMN er en international standard for modellering af beslutningslogik, hvilket sikrer en ensartet tilgang til dokumentation og implementering af forretningsregler.
- **Gennemsigtighed**: Gør beslutningsprocesser tydelige og forståelige for alle interessenter, herunder ledelse, administrative medarbejdere og IT-specialister.
- **Effektivitet**: Understøtter automatisering af beslutningsprocesser i vores IT-systemer, hvilket reducerer manuel arbejdskraft og minimerer fejl.
- **Vedligeholdelse**: Letter opdatering og vedligeholdelse af forretningsregler i takt med ændringer i lovgivningen eller interne politikker.

## **Metode**

For at dokumentere Universitetsloven i DMN har vi fulgt disse trin:

1. **Analyse af loven**: Gennemgået hele Universitetsloven for at identificere alle relevante bestemmelser og forretningsregler.
2. **Udledning af beslutninger**: Identificeret de beslutninger, der skal træffes baseret på lovens bestemmelser.
3. **Identifikation af input og output**: Fastlagt hvilke data og informationer, der er nødvendige for hver beslutning, samt de forventede resultater.
4. **Udarbejdelse af DMN-diagrammer**: Modellering af beslutningerne i DMN, inklusive beslutningstabeller og beslutningskræfter.
5. **Validering**: Sikret, at modellerne er i overensstemmelse med lovens intentioner og er anvendelige i praksis.

## **Dokumentation af Universitetsloven i DMN**

Nedenfor præsenteres den fuldstændige dokumentation af Universitetsloven ved hjælp af DMN. Hver paragraf og stykke er analyseret og modelleret i overensstemmelse med DMN-standarderne.

### **1. Beslutning: Udbud af uddannelser**

**Lovhenvisning**: § 3, stk. 1-4

**Beskrivelse**: Universitetet beslutter, hvilke forskningsbaserede uddannelser det vil udbyde inden for sine fagområder i Danmark. Uddannelserne skal kvalitetssikres og godkendes før udbud.

**DMN-komponenter**:

- **Beslutning**: Udbud af uddannelse
- **Input**:
  - **Strategisk relevans** (`strategiskRelevans`): Boolean
  - **Fagligt grundlag** (`fagligtGrundlag`): Boolean
  - **Ressourcer til rådighed** (`ressourcerTilRådighed`): Boolean
  - **Kvalitetssikring opnået** (`kvalitetssikringOpnået`): Boolean
  - **Ministeriel godkendelse** (`ministerielGodkendelse`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Udbud godkendt", "Udbud afvist")
  
**Hit Policy**: **U** (Unique) – Kun én regel kan gælde.

**Beslutningstabel**:

| **Regel** | `strategiskRelevans` | `fagligtGrundlag` | `ressourcerTilRådighed` | `kvalitetssikringOpnået` | `ministerielGodkendelse` | `beslutning`      |
|-----------|----------------------|-------------------|-------------------------|--------------------------|--------------------------|-------------------|
| 1         | Ja                   | Ja                | Ja                      | Ja                       | Ja                       | Udbud godkendt    |
| 2         | Nej                  | -                 | -                       | -                        | -                        | Udbud afvist      |
| 3         | -                    | Nej               | -                       | -                        | -                        | Udbud afvist      |
| 4         | -                    | -                 | Nej                     | -                        | -                        | Udbud afvist      |
| 5         | -                    | -                 | -                       | Nej                      | -                        | Udbud afvist      |
| 6         | -                    | -                 | -                       | -                        | Nej                      | Udbud afvist      |

### **2. Beslutning: Optagelse af studerende**

**Lovhenvisning**: § 8, stk. 1-3

**Beskrivelse**: Universitetet skal fastsætte adgangskrav og optagelsesprocedurer i overensstemmelse med ministeriets regler.

**DMN-komponenter**:

- **Beslutning**: Optagelsesbeslutning
- **Input**:
  - **Adgangskrav opfyldt** (`adgangskravOpfyldt`): Boolean
  - **Adgangsprøve bestået** (`adgangsprøveBestået`): Boolean
  - **Karakterkrav opfyldt** (`karakterkravOpfyldt`): Boolean
  - **Kapacitet til rådighed** (`kapacitetTilRådighed`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Optaget", "Afvist")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `adgangskravOpfyldt` | `adgangsprøveBestået` | `karakterkravOpfyldt` | `kapacitetTilRådighed` | `beslutning` |
|-----------|----------------------|-----------------------|-----------------------|------------------------|--------------|
| 1         | Ja                   | Ja                    | Ja                    | Ja                     | Optaget      |
| 2         | Nej                  | -                     | -                     | -                      | Afvist       |
| 3         | Ja                   | Nej                   | -                     | -                      | Afvist       |
| 4         | Ja                   | Ja                    | Nej                   | -                      | Afvist       |
| 5         | Ja                   | Ja                    | Ja                    | Nej                    | Afvist       |

### **3. Beslutning: Kvalitetssikring af uddannelser**

**Lovhenvisning**: § 3, stk. 1

**Beskrivelse**: Uddannelserne skal kvalitetssikres og akkrediteres i henhold til gældende lovgivning, før de kan udbydes.

**DMN-komponenter**:

- **Beslutning**: Kvalitetssikringsgodkendelse
- **Input**:
  - **Akkrediteringsrapport positiv** (`akkrediteringsrapportPositiv`): Boolean
  - **Kvalitetsstandarder opfyldt** (`kvalitetsstandarderOpfyldt`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Godkendt", "Ikke godkendt")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `akkrediteringsrapportPositiv` | `kvalitetsstandarderOpfyldt` | `beslutning`    |
|-----------|-------------------------------|------------------------------|-----------------|
| 1         | Ja                            | Ja                           | Godkendt        |
| 2         | Nej                           | -                            | Ikke godkendt   |
| 3         | -                             | Nej                          | Ikke godkendt   |

### **4. Beslutning: Udbud af uddannelser i udlandet**

**Lovhenvisning**: § 3 a, stk. 1-6

**Beskrivelse**: Universitetet kan udbyde hele eller dele af uddannelser i udlandet i samarbejde med udenlandske universiteter under visse betingelser.

**DMN-komponenter**:

- **Beslutning**: Udbud af international uddannelse
- **Input**:
  - **Samarbejdsaftale eksisterer** (`samarbejdsaftaleEksisterer`): Boolean
  - **Kvalitetssikring opnået** (`kvalitetssikringOpnået`): Boolean
  - **Juridiske krav opfyldt** (`juridiskeKravOpfyldt`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Godkendt", "Afvist")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `samarbejdsaftaleEksisterer` | `kvalitetssikringOpnået` | `juridiskeKravOpfyldt` | `beslutning` |
|-----------|------------------------------|--------------------------|------------------------|--------------|
| 1         | Ja                           | Ja                       | Ja                     | Godkendt     |
| 2         | Nej                          | -                        | -                      | Afvist       |
| 3         | Ja                           | Nej                      | -                      | Afvist       |
| 4         | Ja                           | Ja                       | Nej                    | Afvist       |

### **5. Beslutning: Tilmelding til fag og prøver**

**Lovhenvisning**: § 8, stk. 1-3

**Beskrivelse**: Studerende skal tilmeldes fag og prøver i overensstemmelse med uddannelsens studieordning og ministeriets regler.

**DMN-komponenter**:

- **Beslutning**: Tilmelding til fag og prøver
- **Input**:
  - **Studieaktivitetskrav opfyldt** (`studieaktivitetskravOpfyldt`): Boolean
  - **Tidligere fag bestået** (`tidligereFagBestået`): Boolean
  - **ECTS-begrænsninger overholdt** (`ectsBegrænsningerOverholdt`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Godkendt", "Afvist")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `studieaktivitetskravOpfyldt` | `tidligereFagBestået` | `ectsBegrænsningerOverholdt` | `beslutning` |
|-----------|-------------------------------|-----------------------|------------------------------|--------------|
| 1         | Ja                            | Ja                    | Ja                           | Godkendt     |
| 2         | Nej                           | -                     | -                            | Afvist       |
| 3         | -                             | Nej                   | -                            | Afvist       |
| 4         | -                             | -                     | Nej                          | Afvist       |

### **6. Beslutning: Opkrævning af deltagerbetaling**

**Lovhenvisning**: § 26, stk. 1-9

**Beskrivelse**: Universitetet skal opkræve deltagerbetaling for visse uddannelsesaktiviteter i overensstemmelse med loven.

**DMN-komponenter**:

- **Beslutning**: Beregning af deltagerbetaling
- **Input**:
  - **Uddannelsestype** (`uddannelsestype`): String ("Heltid", "Deltid", "Ekstra aktivitet")
  - **Tilskud modtaget** (`tilskudModtaget`): Boolean
  - **Statsborgerskab** (`statsborgerskab`): String ("Dansk/EU", "Ikke-EU")
- **Output**:
  - **Deltagerbetaling** (`deltagerbetaling`): String ("Ingen betaling", "Delvis betaling", "Fuld betaling")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `uddannelsestype`    | `tilskudModtaget` | `statsborgerskab` | `deltagerbetaling` |
|-----------|----------------------|-------------------|-------------------|--------------------|
| 1         | Deltid               | Ja                | Dansk/EU          | Delvis betaling    |
| 2         | Heltid               | Nej               | Ikke-EU           | Fuld betaling      |
| 3         | Ekstra aktivitet     | Nej               | Dansk/EU          | Ingen betaling     |
| 4         | Heltid               | Ja                | Dansk/EU          | Ingen betaling     |

### **7. Beslutning: Tildeling af fripladser og stipendier**

**Lovhenvisning**: § 19, stk. 9-10

**Beskrivelse**: Universitetet kan tildele fripladser og stipendier til visse udenlandske studerende inden for rammerne af finansloven.

**DMN-komponenter**:

- **Beslutning**: Tildeling af friplads/stipendium
- **Input**:
  - **Nationalitet** (`nationalitet`): String ("Udenlandsk (uden for EU)", "Dansk/EU")
  - **Akademiske kvalifikationer opfyldt** (`akademiskeKvalifikationerOpfyldt`): Boolean
  - **Økonomiske behov dokumenteret** (`økonomiskeBehovDokumenteret`): Boolean
  - **Ramme til rådighed** (`rammeTilRådighed`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Tildeling", "Afslag", "Ikke relevant")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `nationalitet`                | `akademiskeKvalifikationerOpfyldt` | `økonomiskeBehovDokumenteret` | `rammeTilRådighed` | `beslutning`     |
|-----------|-------------------------------|------------------------------------|-------------------------------|--------------------|------------------|
| 1         | Udenlandsk (uden for EU)      | Ja                                 | Ja                            | Ja                 | Tildeling        |
| 2         | Udenlandsk (uden for EU)      | Nej                                | -                             | -                  | Afslag           |
| 3         | Dansk/EU                      | -                                  | -                             | -                  | Ikke relevant    |
| 4         | Udenlandsk                    | Ja                                 | Nej                           | -                  | Afslag           |

### **8. Beslutning: Klagebehandling**

**Lovhenvisning**: § 34

**Beskrivelse**: Behandling af retlige spørgsmål ved universitetets afgørelser om studerendes forhold.

**DMN-komponenter**:

- **Beslutning**: Klageafgørelse
- **Input**:
  - **Klage rettidig** (`klageRettidig`): Boolean
  - **Retligt spørgsmål** (`retligtSpørgsmål`): Boolean
  - **Tidligere behandlet** (`tidligereBehandlet`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Klage behandles", "Klage afvises", "Klage afvist - allerede behandlet")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `klageRettidig` | `retligtSpørgsmål` | `tidligereBehandlet` | `beslutning`                            |
|-----------|-----------------|--------------------|----------------------|-----------------------------------------|
| 1         | Ja              | Ja                 | Nej                  | Klage behandles                         |
| 2         | Nej             | -                  | -                    | Klage afvises                           |
| 3         | Ja              | Nej                | -                    | Klage afvises                           |
| 4         | Ja              | Ja                 | Ja                   | Klage afvist - allerede behandlet       |

### **9. Beslutning: Ansættelse og afskedigelse af personale**

**Lovhenvisning**: § 29

**Beskrivelse**: Universitetet skal følge de fastsatte regler om løn- og ansættelsesvilkår for personale.

**DMN-komponenter**:

- **Beslutning**: Ansættelsesbeslutning
- **Input**:
  - **Krav opfyldt** (`kravOpfyldt`): Boolean
  - **Kvalifikationer passende** (`kvalifikationerPassende`): Boolean
  - **Overenskomst overholdt** (`overenskomstOverholdt`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Ansættelse", "Afslag")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `kravOpfyldt` | `kvalifikationerPassende` | `overenskomstOverholdt` | `beslutning` |
|-----------|---------------|---------------------------|--------------------------|--------------|
| 1         | Ja            | Ja                        | Ja                       | Ansættelse   |
| 2         | Nej           | -                         | -                        | Afslag       |
| 3         | Ja            | Nej                       | -                        | Afslag       |
| 4         | Ja            | Ja                        | Nej                      | Afslag       |

### **10. Beslutning: Økonomiske dispositioner**

**Lovhenvisning**: § 21

**Beskrivelse**: Universitetet disponerer frit inden for sit formål ved anvendelse af tilskud, indtægter og kapital under ét, dog under overholdelse af tilskudsbetingelser og disponeringsregler.

**DMN-komponenter**:

- **Beslutning**: Økonomisk disposition
- **Input**:
  - **Formål overholdt** (`formålOverholdt`): Boolean
  - **Tilskudsbetingelser overholdt** (`tilskudsbetingelserOverholdt`): Boolean
  - **Budget dækning** (`budgetDækning`): Boolean
- **Output**:
  - **Beslutning** (`beslutning`): String ("Godkendt", "Afvist")
  
**Hit Policy**: **U** (Unique)

**Beslutningstabel**:

| **Regel** | `formålOverholdt` | `tilskudsbetingelserOverholdt` | `budgetDækning` | `beslutning` |
|-----------|-------------------|--------------------------------|-----------------|--------------|
| 1         | Ja                | Ja                             | Ja              | Godkendt     |
| 2         | Nej               | -                              | -               | Afvist       |
| 3         | Ja                | Nej                            | -               | Afvist       |
| 4         | Ja                | Ja                             | Nej             | Afvist       |

## **Implementering i Applikationslandskabet**

For at integrere disse DMN-modeller i vores systemer skal vi:

- **Udvikle eller tilpasse eksisterende IT-systemer** til at understøtte beslutningsmodellerne.
- **Træne personale** i anvendelse og vedligeholdelse af DMN-modellerne.
- **Etablere governance-processer** for at sikre løbende opdatering i overensstemmelse med lovændringer.
- **Sikre integration** mellem DMN-modellerne og vores forretningsprocesser samt applikationer.

## **Konklusion**

Ved at dokumentere Universitetsloven i DMN opnår vi en klar og struktureret forståelse af de forretningsregler, der styrer vores aktiviteter. Dette vil forbedre vores evne til at overholde lovgivningen, optimere processer og understøtte vores strategiske mål.

Vi anbefaler derfor, at universitetet implementerer DMN som en standard for dokumentation og implementering af forretningsregler.

## **Bilag**

**DMN-diagrammer**: De fulde DMN-diagrammer for hver beslutning er vedlagt som bilag til dette dokument.

**Referencer**:

- **Universitetsloven**: Bekendtgørelse af lov om universiteter.
- **DMN-specifikation**: OMG Decision Model and Notation (DMN), Version 1.6.