
# pandas: Manipulace a převodní funkce

1. **`pivot()`**:
   ```python
   df.pivot(index="foo", columns="bar", values="zoo")
   ```
   - **Popis**: Převádí tabulku tím, že nastaví hodnoty jednoho sloupce jako index (řádky), jiného sloupce jako sloupce, a hodnoty třetího sloupce jako obsah buňky.
   - **Použití**: Používá se, když máte plochou tabulku a potřebujete ji převést na matici (například při vytváření kontingenčních tabulek).
   - **Omezení**: Musí existovat jedinečné kombinace hodnot v indexu a sloupcích, jinak dojde k chybě.

---

2. **`pivot_table()`**:
   ```python
   df.pivot_table(index="foo", columns="bar", values="zoo")
   ```
   - **Popis**: Velmi podobné jako `pivot()`, ale umí se lépe vypořádat s duplicitními kombinacemi hodnot v indexech a sloupcích. Navíc umožňuje specifikovat agregační funkce (např. průměr, součet, minimum, maximum).
   - **Použití**: Pokud máte data s duplicitami a chcete provést agregaci. Například: průměrné prodeje produktů podle jednotlivých dnů.
   - **Možnosti agregace**: Lze použít různé funkce, jako je `aggfunc='sum'` nebo `aggfunc='mean'`.

---

3. **`stack()`**:
   ```python
   df.stack()
   ```
   - **Popis**: Převede sloupce DataFrame na řádky. Vrátí Series, kde každý sloupec se stane hodnotou nové úrovně indexu.
   - **Použití**: Užitečné, když chcete "zmenšit" DataFrame s více sloupci a převést je na sérii. Tímto způsobem můžete zpracovat více sloupců jako jednu dlouhou strukturu.
   - **Výsledek**: Nový DataFrame nebo Series, kde každý původní sloupec je přetvořen na nový řádek.

---

4. **`unstack()`**:
   ```python
   df.unstack()
   ```
   - **Popis**: Opačná operace k `stack()`. Převede víceřádkovou Series (po `stack()`) zpět do sloupců.
   - **Použití**: Pokud máte DataFrame po operaci `stack()`, lze tímto způsobem znovu obnovit původní tvar. Hodí se také pro reorganizaci víceúrovňových indexů.
   - **Výsledek**: Vrátí DataFrame, kde jsou z původních řádků opět sloupce.

---

5. **`melt()`**:
   ```python
   pd.melt(df, id_vars="foo", value_vars=["zoo", "bar"])
   ```
   - **Popis**: Tato funkce "roztaví" DataFrame z širokého formátu do dlouhého formátu. Slouží k přeměně sloupců na řádky.
   - **Použití**: Používá se, když potřebujete převést sloupce na řádky, například při přípravě dat pro vizualizaci nebo analýzu. Je velmi užitečná při práci s "tidy data".
   - **Argumenty**: 
     - `id_vars`: Určuje sloupce, které budou ponechány jako identifikátory.
     - `value_vars`: Určuje, které sloupce se mají převést na řádky.

---

6. **`groupby()`**:
   ```python
   df.groupby("foo")
   ```
   - **Popis**: Rozdělí DataFrame na skupiny podle hodnot ve specifikovaném sloupci a umožní provádět různé agregační nebo transformační operace na těchto skupinách.
   - **Použití**: Kdykoliv potřebujete rozdělit data do skupin (např. podle kategorie produktů nebo zemí) a následně provést nějakou agregaci (např. součet, průměr).
   - **Příklad**: Lze využít pro výpočet průměrné ceny produktů v jednotlivých kategoriích.

---

7. **`crosstab()`**:
   ```python
   pd.crosstab(df["foo"], df["zoo"])
   ```
   - **Popis**: Vytvoří kontingenční tabulku, která ukazuje četnost výskytu kombinací hodnot z dvou sloupců. Ukazuje, kolikrát se určité hodnoty v jednom sloupci (řádcích) vyskytly společně s hodnotami z druhého sloupce (sloupců).
   - **Použití**: Skvělé pro tvorbu četnostních tabulek (frekvenčních tabulek) při analýze dat, například počet prodejů podle kategorií produktů.
   - **Výsledek**: Vytvoří tabulku, kde jsou zobrazeny počty výskytů pro každou kombinaci hodnot z obou sloupců.

---

8. **`explode()`**:
   ```python
   df.explode("foo")
   ```
   - **Popis**: Rozdělí položky typu seznam (list) ve sloupci na jednotlivé řádky. Každý prvek seznamu ve sloupci se stane samostatným řádkem.
   - **Použití**: Pokud máte sloupec, který obsahuje seznamy nebo jiný iterovatelný objekt, a potřebujete rozdělit tento seznam na jednotlivé řádky.
   - **Výsledek**: Vytvoří DataFrame, kde každá hodnota z původního seznamu je na samostatném řádku.
