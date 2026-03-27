Krátký návod k Firestore pravidlům

1) Soubor `firestore.rules` (v kořeni projektu) obsahuje základní pravidla. Pro rychlé testování je tam povoleno veřejné čtení a zakázán zapis.

2) Jak nasadit pravidla (vyžaduje nainstalovaný Firebase CLI a přihlášený účet):

```bash
# Ujistěte se, že jste v kořenové složce projektu (kde je firebase.json)
firebase deploy --only firestore:rules
```

3) Poznámky a bezpečnost:
- Pravidla `allow read: if true;` je vhodné použít jen krátkodobě pro debug. V produkci použijte pravidla podle přístupu, např. `if request.auth != null` nebo detailnější pravidla pro kolekce.
- Po testování upravte pravidla na přísnější a otestujte pomocí Firebase Rules Simulator v konzoli.

4) Pro naši aplikaci: chyba `Missing or insufficient permissions` znamená, že aktuální pravidla neumožňují čtení kolekce `rezervace`. Pokud chcete číst jen veřejně, nasadíte tento testovací soubor. Pokud chcete povolit přístup pouze přihlášeným uživatelům, přepněte na produkční variantu v `firestore.rules`.
