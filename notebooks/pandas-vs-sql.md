
# SQL vs Pandas


## Základní
Zde je srovnávací tabulka základních příkazů v SQL a jejich ekvivalentů v knihovně **pandas**:

| Úkol                      | SQL                                    | Pandas                              |
|----------------------------|----------------------------------------|-------------------------------------|
| **Načíst data z tabulky**   | `SELECT * FROM table_name;`            | `df = pd.read_csv('file.csv')` nebo `pd.read_sql('SELECT * FROM table_name', connection)` |
| **Filtrování řádků**        | `SELECT * FROM table WHERE condition;` | `df[df['column'] == value]`        |
| **Výběr konkrétních sloupců**| `SELECT column1, column2 FROM table;` | `df[['column1', 'column2']]`       |
| **Řazení dat**              | `SELECT * FROM table ORDER BY column;` | `df.sort_values(by='column')`      |
| **Agregace**                | `SELECT SUM(column) FROM table;`       | `df['column'].sum()`               |
| **Skupinové agregace**      | `SELECT column, SUM(column2) FROM table GROUP BY column;` | `df.groupby('column')['column2'].sum()` |
| **Spojování tabulek**       | `SELECT * FROM table1 JOIN table2 ON table1.column = table2.column;` | `df1.merge(df2, on='column')`      |
| **Přidání nového sloupce**  | `ALTER TABLE table ADD COLUMN new_col;` | `df['new_col'] = values`           |
| **Odebrání duplicit**       | `SELECT DISTINCT(column) FROM table;`  | `df['column'].drop_duplicates()`   |
| **Výpočet průměru**         | `SELECT AVG(column) FROM table;`       | `df['column'].mean()`              |
| **Seskupení podle a počítání** | `SELECT column, COUNT(*) FROM table GROUP BY column;` | `df.groupby('column').size()` nebo `df['column'].value_counts()` |
| **Filtrování na základě více podmínek** | `SELECT * FROM table WHERE condition1 AND condition2;` | `df[(df['column1'] == value1) & (df['column2'] == value2)]` |



## Pokročilejší 

| Úkol                          | SQL                                                       | Pandas                                               |
|-------------------------------|-----------------------------------------------------------|------------------------------------------------------|
| **Poddotazy**                  | `SELECT * FROM (SELECT * FROM table WHERE condition);`     | `df[df['column'].apply(lambda x: condition)]`         |
| **Pivotování**                 | `SELECT * FROM (SELECT pivot) PIVOT(...);`                | `df.pivot(index='column', columns='column', values='value')` |
| **Kumulativní operace**        | `SELECT SUM(column) OVER (ORDER BY column) FROM table;`    | `df['column'].cumsum()`                               |
| **Vyhledání hodnoty**          | `SELECT CASE WHEN condition THEN value ELSE value END`     | `df['column'].apply(lambda x: value if condition else value)` |
| **Mazání řádků**               | `DELETE FROM table WHERE condition;`                      | `df = df[df['column'] != value]`                      |
| **Úprava existujícího řádku**  | `UPDATE table SET column = value WHERE condition;`        | `df.loc[df['column'] == value, 'column'] = new_value` |
| **Spojování více tabulek**     | `SELECT * FROM table1 JOIN table2 ON condition JOIN ...`   | `df1.merge(df2, on='column').merge(df3, on='column')` |
| **Výpočet min a max hodnoty**  | `SELECT MIN(column), MAX(column) FROM table;`             | `df['column'].min(), df['column'].max()`              |
| **Výpočet mediánu**            | `SELECT PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY col);` | `df['column'].median()`                               |
| **Renaming columns**           | `ALTER TABLE table RENAME column1 TO new_name;`           | `df.rename(columns={'column1': 'new_name'})`          |
| **Práce s NaN hodnotami**      | `SELECT * FROM table WHERE column IS NOT NULL;`           | `df.dropna(subset=['column'])`                        |

### Výhody SQL vs Pandas:

#### SQL výhody:
1. **Velká škálovatelnost**: SQL dotazy lze spouštět na velkých databázích a servery zvládnou i enormní množství dat.
2. **Optimalizace výkonu**: SQL databáze mají zabudované optimalizátory pro rychlé dotazy a indexování.
3. **Centralizovaná správa dat**: Data jsou často uložena na centrálním serveru, kde mohou být snadno sdílena a spravována.

#### Pandas výhody:
1. **Flexibilita**: Pandas je extrémně flexibilní při práci s daty, manipulace s datovými rámci je snadná a rychlá.
2. **Lepší práce s nečistými daty**: Pandas nabízí robustní nástroje pro práci s NaN hodnotami a filtrování nekonzistentních dat.
3. **Python ekosystém**: Lze snadno integrovat s jinými knihovnami jako NumPy, Matplotlib nebo Scikit-learn, což usnadňuje datovou analýzu, vizualizace a strojové učení.

### Nevýhody SQL vs Pandas:

#### SQL nevýhody:
1. **Statická syntaxe**: SQL je přísný a nelze jej snadno rozšiřovat o další výpočty nebo logiku (např. složité matematické funkce).
2. **Komplicovanost poddotazů**: Složitější operace jako vnořené dotazy nebo vlastní funkce mohou být obtížné na implementaci a ladění.
3. **Chybějící práce s nečistými daty**: SQL není tak dobře vybaveno pro práci s neúplnými či nečistými daty jako pandas.

#### Pandas nevýhody:
1. **Není škálovatelné pro velké datové sady**: Pandas je paměťově náročný a při práci s velmi velkými datovými sadami se výkon zhoršuje.
2. **Výkon**: Pandas při zpracování velkých objemů dat není tak efektivní jako optimalizované databázové dotazy.
3. **Neexistence transakčních mechanismů**: Pandas nemá transakce, což znamená, že jakákoli změna v datech se projeví ihned, bez možnosti „vrátit“ změny zpět.

### Na co si dát pozor:

- **Paměťové omezení**: Pandas načítá všechna data do paměti, takže při práci s velkými datovými sadami by mohlo dojít k problémům s výkonem a nedostatkem paměti.
- **Optimalizace dotazů**: SQL dotazy je nutné optimalizovat pomocí správného indexování a práce s poddotazy, aby byly výkonné.
- **Čistota dat**: Pandas poskytuje lepší nástroje pro práci s nečistými daty, SQL naopak vyžaduje, aby byla data správně strukturovaná a čistá.
- **Změny dat**: SQL provádí změny dat na úrovni databáze, zatímco pandas je používán především pro analýzu dat bez jejich změny na úrovni databáze.

Oba nástroje mají své místo a často je nejlepší využívat kombinaci SQL pro získání dat a pandas pro pokročilejší analýzy a úpravy.