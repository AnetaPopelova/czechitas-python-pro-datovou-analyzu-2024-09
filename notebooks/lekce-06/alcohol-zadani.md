
# Vliv alkoholu na výkonnost studentů

## Cíl analýzy
Zjistit, jak konzumace alkoholu ovlivňuje akademické výsledky studentů. 

Cílem je analyzovat, zda existuje souvislost mezi množstvím konzumovaného alkoholu, četností sociálních aktivit a výkonem ve škole.

Zdroj dat: https://www.kaggle.com/datasets/joshuanaude/effects-of-alcohol-on-student-performance/data


### Krok 1: Načtení a příprava dat

- Načtěte data,
- přejmenujte sloupce pro lepší manipulaci,
- zkontrolujte typy dat,
- zjistěte počet 
  - záznamů v každém sloupci,
  - chybějících hodnot v každém sloupci,
  - počet unikátních hodnot v každém sloupci a 
- upravte datový typ sloupce `Timetamp` na `datetime` - časové pásmo zanedbejte (může se hodit parametr `format`).

Sloupce k přejmenování:
```py
columns={
        "Timestamp": "Timestamp",
        "Your Sex?": "Sex",
        "Your Matric (grade 12) Average/ GPA (in %)": "Matric_GPA",
        "What year were you in last year (2023) ?": "Year",
        "What faculty does your degree fall under?": "Faculty",
        "Your 2023 academic year average/GPA in % (Ignore if you are 2024 1st year student)": "Yearly_GPA",
        "Your Accommodation Status Last Year (2023)": "Accommodation",
        "Monthly Allowance in 2023": "Monthly_Allowance",
        "Were you on scholarship/bursary in 2023?": "Scholarship",
        "Additional amount of studying (in hrs) per week": "Study_Hours",
        "How often do you go out partying/socialising during the week? ": "Socialising_Frequency",
        "On a night out, how many alcoholic drinks do you consume?": "Drinks_Per_Night",
        "How many classes do you miss per week due to alcohol reasons, (i.e: being hungover or too tired?)": "Missed_Classes",
        "How many modules have you failed thus far into your studies?": "Modules_Failed",
        "Are you currently in a romantic relationship?": "In_Relationship",
        "Do your parents approve alcohol consumption?": "Parents_Approve",
        "How strong is your relationship with your parent/s?": "Relationship_Parents",
    }
```


### Krok 2: Explorativní analýza dat (EDA)
- Proveďte základní statistický popis dat, 
- pro sloupce `["Sex", "Accommodation", "Monthly_Allowance"]` vypiš unikátní hodnoty a jejich počet
- vizualizujte distribuci klíčových proměnných:
  - histogram a boxpot pro Yearly GPA (identifikujte extrémní hodnoty)
  - sloupcovy graf pro počet žen vs mužů v datasetu
- vytvořte kontingenční tabulku, která ukáže počet studentů na jedtlivých fakultách podle pohlaví a
- formulujte 3 vlastní hypotézy, které lze na datech ověřit.


**Příklad možných hypotéz**
1. **Vliv konzumace alkoholu na akademický výkon:** Hypotéza zkoumá, zda existuje souvislost mezi množstvím konzumovaného alkoholu a akademickými výsledky studentů, měřenými pomocí ročního GPA.
2. **Vliv frekvence společenských aktivit na akademický výkon:** Hypotéza posuzuje, jak časté účasti na party a jiných společenských akcích ovlivňují akademické výsledky studentů.
3. **Souvislost mezi konzumací alkoholu a absencí ve škole:** Hypotéza zkoumá, zda studenti, kteří konzumují alkohol větší množství, mají tendenci častěji chybět ve škole kvůli důsledkům spojeným s pitím, jako jsou kocoviny nebo únavu.


### Krok 3: Čištění dat
- Odstraňte všechny záznamy, kde chybí informace o měsíčním kapesném,
- textové hodnoty ve sloupci měsíční kapesné nahraďte celým číslem (středová hodnota) a
- odstraňte všechny záznamy studentů `Postgraduate` studia.

### Krok 4: Vizualizace výsledků
- Vytvořte vizualizace souvisejících s vašimi hypotézami.
- Pokud potřebujete provést dodatečné čistění nebo tranformaci dat, učiňte tak.

### Krok 5: Závěr a doporučení
- Sumarizujte zjištěné výsledky, diskutujte o jejich významu a uveďte možná doporučení pro zainteresované strany, jako jsou univerzitní poradci a studenti.
