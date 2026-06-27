# influencer.hub — CRM dla influencerów (FitbyMed)

Lekki CRM do zarządzania współpracami z influencerami. Cały produkt to jeden plik
`influencer-crm.html`, który otwierasz dwuklikiem w przeglądarce — działa offline,
a po podłączeniu Supabase synchronizuje dane na żywo między urządzeniami.

## Co umie

- Pipeline współpracy (statusy: kontakt, negocjacje, aktywny, zakończony, notatka)
- Profil influencera: dane, stawki, kod rabatowy, wątki mailowe
- Sprzedaż z afiliacji (import CSV z GoAffPro): obrót, sztuki, prowizja
- Wykres dzienny PLN i rozbicie „co sprzedał" na profilu
- Dashboard: kto sprzedał, kto nie, łączny obrót i zasięg
- Tryb chmury (Supabase) — wspólne dane na kompie i telefonie

## Uruchomienie

Otwórz `influencer-crm.html` dwuklikiem w przeglądarce. Tyle.

## Tryb chmury (opcjonalny)

1. Załóż projekt na [supabase.com](https://supabase.com) (region: Central EU / Frankfurt).
2. W **SQL Editor** uruchom SQL dostępny w aplikacji pod ⚙︎ → „Kopiuj SQL"
   (tworzy tabelę `influencers`, realtime i politykę dostępu).
3. W **Project Settings → API** skopiuj **Project URL** oraz klucz **anon public**.
4. W aplikacji ⚙︎ → wklej URL i klucz → **Połącz**. Nagłówek pokaże „Chmura: połączono".

> ⚠️ Używaj wyłącznie klucza **anon public**, nigdy `service_role`.

## Import sprzedaży (GoAffPro → CSV)

Eksportujesz CAŁOŚĆ z GoAffPro i wgrywasz przez „📥 Sprzedaż z GoAffPro (CSV)".
Tryb pełnego eksportu = zastąpienie, więc liczby zawsze zgadzają się ze źródłem.
Oczekiwane kolumny: `Coupon, Date, Product, Quantity, Amount, Commission`
(parser łapie też warianty nazw i separator `,` lub `;`).

## Uwaga o bezpieczeństwie

Klucz `anon` w pliku HTML jest publiczny z natury, a RLS jest otwarte (narzędzie
wewnętrzne). Nie publikuj pliku z wpisanym kluczem w miejscu dostępnym dla obcych.
