# SSLCertVerificationError

Implementace jednoho z těchto řešení by vám měla pomoci vyřešit problém s ověřením SSL certifikátu, se kterým se setkáváte při použití `pandas.read_csv`.

Po opatřeních viz níže ještě vypni/zapni VS Code.

## Pro uživatele macOS

### Instalace certifikátů macOS:
Python 3.6 a novější na macOS obsahuje dodatečný skript, který instaluje certifikáty. Spusťte tento skript pro instalaci potřebných certifikátů.
```py
/Applications/Python\ 3.x/Install\ Certificates.command
```

Nahraďte 3.x vaší konkrétní verzí Pythonu.

### Instalace certifikátů pomocí Certifi:
Instalace Pythonu na macOS obvykle nezahrnuje potřebné certifikáty pro ověření SSL spojení. Můžete potřebovat nainstalovat balíček certifi a nastavit vaše Python prostředí, aby používalo tyto certifikáty.Nejprve se ujistěte, že máte nainstalovaný balíček certifi:
```py
pip install certifi
```

Poté, v Python skriptu, můžete explicitně určit cestu k souboru s certifikátem:
```py
import ssl
import certifi
import pandas as pd

# Nastaví SSL kontext pro použití certifikátu z balíčku certifi
ssl_context = ssl.create_default_context(cafile=certifi.where())

# Nyní použijte pandas k načtení CSV s určeným SSL kontextem

url = "https://your-secure-url.com/data.csv"
df = pd.read_csv(url, storage_options={'ssl_context': ssl_context})
```



## Pro uživatele Windows a Linux
- Kontrola vašeho SSL certifikátového prostředí: Ujistěte se, že vaše prostředí obsahuje vhodné SSL certifikáty. To obvykle není na těchto operačních systémech problém, ale stále můžete specifikovat svazek certifikátů, jak je ukázáno výše pomocí certifi.
- Aktualizace nebo reinstalace Pythonu: Někdy může prostá reinstalace Pythonu vyřešit tyto problémy, protože se ujistí, že SSL certifikáty jsou správně nastaveny během instalace.

## Obecné tipy

**Vypnutí ověření SSL (Nedoporučuje se):**
Pouze pro testovací účely (a nikoli v produkčním prostředí) můžete vypnout ověřování SSL. Obecně se to nedoporučuje kvůli bezpečnostním obavám:

# UPOZORNĚNÍ: Vypnutí ověření SSL vás vystavuje bezpečnostním rizikům
```py
df = pd.read_csv("https://your-secure-url.com/data.csv", storage_options={'ssl_context': False})
``` 

**Aktualizace requests a urllib3:**
Někdy může pouhá aktualizace těchto knihoven pomoci, protože zahrnují vlastní zlepšení bezpečnosti:
```py
pip install --upgrade requests urllib3
```

