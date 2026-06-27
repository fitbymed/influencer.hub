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

Logowanie odbywa się przez **Supabase Auth** (e-mail + hasło). Hasła **nie ma w kodzie** —
sprawdza je serwer Supabase. Dostęp do danych chroni **RLS**: czytać i pisać mogą
wyłącznie zalogowani użytkownicy (`to authenticated`).

Konta zakłada się ręcznie w panelu Supabase (Authentication → Users). Publiczna
rejestracja jest wyłączona — nikt obcy nie założy sobie konta sam. Dzięki temu repo
może być publiczne (potrzebne dla darmowego GitHub Pages) bez ryzyka dla danych:
nawet znając klucz `anon` z kodu, bez zalogowania nie odczyta się nic z bazy.

Dodanie/odebranie dostępu = dodanie/usunięcie użytkownika w Authentication → Users.

## Plik źródłowy

Jeden plik źródłowy: `index.html` (kopia: `influencer-crm.html`). Edytuj jeden,
zsynchronizuj drugi przed commitem (są identyczne).
