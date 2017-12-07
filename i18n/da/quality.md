# Kvalitetssikring 

Følgende er en foreslået model for QA-workflow. Selvom det er lineært i natur, kan enhver fase arbejdes individuelt, hvis det er nødvendigt - så længe alle faser til sidst tages op.

## Fase 1: Grundlæggende gennemgang

- Gennemgå open issues på vores [Issue Tracker](https://github.com/monero-project/kovri/issues/)
- Gennemgå vores [Vulnerability Response Process](https://github.com/anonimal/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md)
- Alt kode skal overholde vores bidragsretningslinjer
- Bemærk områder, der skal forbedres 
(mentalt eller i kode)
- Opret TODO's og tildele, hvis det er muligt

## Fase 2: Specifikations gennemgang / Implementation / Kode dokumentering

- Komplet specifikationsoversigt pr. Modulmodel fx Streaming, I2PControl osv.
 - Koden skal være in-line med væsentlige dele af specifikationen, der vil opretholde samme (eller bedre) niveau af anonymitet, som java I2P giver
 - Refactoring / implementer / patch når / hvor det er nødvendigt
- Sørge for C + + 11/14-kompatibel implementering
 - Gennemgå fase 2 om nødvendigt
- Løs alle relaterede TODO'er
- Dokumenter kode så meget som muligt, med kursive kommentare og Doxygen
 - Kode skal forstås af nybegynder til erfarne kodere
 - Kode skal vejlede læseren til en bedre forståelse af I2P
   - I2P er meget kompleks, så vores kode skal fungere som suveræn erstatning af spec dokumentation og ikke blot som et supplement (dette kan være et kedeligt mål, men meget givende med hensyn til vedligeholdelse og software levetid)
   
## Fase 3: Krypto Gennemgang / Sikkerhedsrevision
   
- Sørg for, at krypto er ajourført og korrekt implementeret
- Etablere hver vektor for kendt udnyttelse
- Vær opmærksom på disse vektorer, når du skriver prøver
- Ødelæg Kovri på hvilken som helst måde
     - Fiks hvad du ødelægger
- Brug altid troværdige, velskrevne biblioteker, når det er muligt
  - Undgå homebrewed, ad hoc, * Jeg er sikker på, at jeg ved bedre end fællesskabet * type af kode
- Søg 2. (eller flere) meninger fra kollegere, før du fortsætter til næste fase

## Fase 4: Bug squashing / Teste / Profilering

- Løsning af prioriterede fejl / problemer
- Skriv enhedsprøvningstest for hvert modul
  - Kør teste. Kør dem igen
  - Fuld gennemgang af testresultater. Patch hvis det er nødvendigt. Refactoring efter behov
- Sørg for, at automation kører regelmæssigt
  - valgrind, doxygen, clang-format
  - Patch efter behov, refactoring efter behov
  
## Fase 5: Konferere

- Konference med kolleger og samfundet
  - Konferencen skal ske offentligt via ticket, møder og / eller IRC
- Accepter alle tilbagemeldinger og som reaktion producere konkrete resultater
- Hvis du er tilfreds, fortsæt med næste fase, gentag denne fase (eller start fra en tidligere fase)

## Fase 6: Gentag cyklen fra begyndelsen