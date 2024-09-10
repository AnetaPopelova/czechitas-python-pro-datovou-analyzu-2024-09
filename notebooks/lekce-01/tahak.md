# Tahák pro lekci Načtení dat

## Import pandas
```
import pandas
```

## Vytvoření prázdného DataFrame
```
prazdny_dataframe = pandas.DataFrame()
dataframe_se_sloupecky = pandas.DataFrame(columns=["sloupec1", "sloupec2", "sloupec3"])
```

## Načítání dat
Data mohu načítat z různých druhů souborů třeba csv (pandas.read_csv), json (pandas.read_json), excel (pandas.read_excel) atd. 
```
novy_dataframe = pandas.read_csv("nazev_souboru.csv")
```

## Základní informace o tabulce
```
muj_dataframe.info() # názvy sloupců, datové typy, počet neprázdných hodnot atd.
muj_dataframe.shape # na prvním místě je počet řádků a na druhém počet sloupců
muj_dataframe.columns # názvy všech sloupců 
muj_dataframe.describe() # informace o hodnotách ve sloupcích s čísly

muj_dataframe.head() # vraci prvnich 5 radku
muj_dataframe.tail() # vraci poslednich 5 radku
```

## Výběr sloupců
```
muj_dataframe["Nazev sloupce"] # vraci Series
muj_dataframe["Nazev sloupce", "Dalsi nazev sloupce"] # vraci DataFrame
```

## Výběr řádků pomocí indexu
```
muj_dataframe.iloc[1:10]    # od druhého do desátého řádku
muj_dataframe.iloc[:3]      # první tři řádky
muj_dataframe.iloc[-3:]     # posledni tri řádky
muj_dataframe.iloc[8:]      # od sedmého řádku dál
```

## Výběr řádků i sloupců
```
muj_dataframe.iloc[:,[0,3]] # všechny řádky a první a čtvrtý sloupec podle indexu
muj_dataframe["Nazev Sloupce"].iloc[1:4] # vybraný sloupec(e) dle názvu a řádky dle indexu
```
