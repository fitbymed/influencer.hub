# influencer.hub — CRM dla influencerów (FitbyMed)

Lekki CRM do zarządzania współpracami z influencerami. Cały produkt to jeden plik
(`index.html` / `influencer-crm.html`). Działa w przeglądarce, a dane synchronizują się
na żywo między urządzeniami przez Supabase.

## Dostęp online

Hostowane przez GitHub Pages. Wchodzisz na link, podajesz hasło dostępu i pracujesz.
URL + klucz Supabase są wbudowane w plik, więc nie trzeba nic konfigurować ręcznie.

## Co umie

- Pipeline współpracy (statusy: weryfikacja, negocjacje, aktywna, zakończona, odrzucony)
- Profil influencera: dane, stawki, kod rabatowy, wątki mailowe
- Sprzedaż z afiliacji (import CSV z GoAffPro): obrót, sztuki, prowizja
- Wykres dzienny PLN i rozbicie „co sprzedał" na profilu
- Dashboard: kto sprzedał, kto nie, łączny obrót i zasięg
- Wspólne dane w chmurze (Supabase) — kilka urządzeń na żywo

## Import sprzedaży (GoAffPro → CSV)

Eksportujesz CAŁOŚĆ z GoAffPro i wgrywasz przez „📥 Sprzedaż z GoAffPro (CSV)".
Tryb pełnego eksportu = zastąpienie. Kolumny: `Coupon, Date, Product, Quantity, Amount, Commission`.

## ⚠️ Bezpieczeństwo — WAŻNE (status: MVP do testów)

Obecna wersja używa **jednego wspólnego hasła wpisanego w kod**. To świadomy
kompromis na etap testowy i ma realne ograniczenia:

- Plik jest publiczny (wymóg darmowego GitHub Pages), więc **hasło i klucz Supabase
  są widoczne w kodzie** dla każdego, kto zajrzy do źródła.
- Polityka RLS w bazie jest otwarta (`using (true)`), więc dane nie są twardo chronione
  na poziomie bazy.

**Przed wpuszczeniem prawdziwych danych influencerów (RODO) należy:**
1. Przejść na **Supabase Auth** (konto e-mail + hasło, weryfikowane przez serwer).
2. Zamknąć RLS na `authenticated` (tylko zalogowani czytają/piszą).

Do tego czasu: trzymaj link i hasło w wąskim gronie i nie wprowadzaj wrażliwych danych.

## Plik źródłowy

Jeden plik źródłowy: `index.html` (kopia: `influencer-crm.html`). Edytuj jeden,
zsynchronizuj drugi przed commitem (są identyczne).
