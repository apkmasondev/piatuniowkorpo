# CODEX PROMPT — Mobile Game Landing Page Generator

## TWOJE ZADANIE

Wygeneruj kompletną, produkcyjną landing page dla gry mobilnej. Strona ma być wizualnie oszałamiająca, konwertująca i w pełni responsywna — zbudowana jako **pojedynczy plik `index.html`** z wbudowanym CSS i JS.

---

## KROK 1 — SKANOWANIE PROJEKTU (OBOWIĄZKOWE, WYKONAJ JAKO PIERWSZE)

Przed napisaniem jakiegokolwiek kodu **zeskanuj cały folder projektu** w poszukiwaniu informacji o grze.

Sprawdź kolejno:
1. `README.md` — nazwa gry, opis, gatunek, mechaniki
2. `package.json` / `app.json` / `config.json` — metadane, wersja, linki
3. `assets/`, `images/`, `screenshots/` — screenshoty, ikony, grafiki gry
4. `store/` lub `marketing/` — opisy App Store / Google Play, taglines
5. `GAME_INFO.md`, `design_doc.md`, `brief.md` — dowolne dokumenty projektowe
6. Dowolne pliki `.txt`, `.md`, `.json` w katalogu głównym

**Z zebranych informacji wyodrębnij:**
- `GAME_NAME` — nazwa gry
- `GAME_DESCRIPTION` — opis (1–3 zdania)
- `GENRE` — gatunek (RPG, puzzle, action, strategy, hyper-casual itp.)
- `KEY_FEATURES` — lista 3–5 kluczowych cech / mechanik
- `TARGET_AUDIENCE` — do kogo gra jest skierowana
- `PLATFORMS` — iOS / Android / oba
- `APP_STORE_URL` / `GOOGLE_PLAY_URL` — jeśli dostępne
- `SCREENSHOTS` — ścieżki do screenów gry (jeśli istnieją)
- `ICON_PATH` — ścieżka do ikony gry (jeśli istnieje)
- `COLOR_PALETTE` — dominujące kolory (z ikon/screenów lub z dokumentów)
- `TAGLINE` — hasło reklamowe (z dokumentów lub własne, pasujące do klimatu gry)

Jeśli czegoś nie ma w plikach — **wymyśl to sam** na podstawie nazwy i gatunku gry. Nie pytaj — działaj.

---

## KROK 2 — PROJEKTOWANIE (STRATEGIC DESIGN BRIEF)

Na podstawie zebranych danych **wybierz jeden z poniższych trybów estetycznych** (dopasuj do gatunku gry):

| Gatunek gry | Rekomendowany styl |
|---|---|
| RPG / Fantasy / Adventure | Dark cinematic — głębokie czernie, złote akcenty, efekty ognia/dymu, particle system |
| Action / Shooter / Battle | Neon cyberpunk — ciemne tło, neonowe glowy, speed lines, glitch effects |
| Puzzle / Casual / Cozy | Soft pastel maximalism — jasne pastele, bubbly shapes, confetti, playful typography |
| Strategy / Tower Defense | Tactical dark — khaki + neon, grid backgrounds, HUD-style UI elements |
| Hyper-casual / Arcade | Bold pop — saturowane kolory, oversized typography, flat + 3D mix, bouncy animations |
| Horror / Survival | Gothic atmosphere — głęboka purpura/czerwień, mgła, flickering light, noise texture |

**JEŚLI nie pasujesz do żadnej — wybierz Dark Cinematic jako domyślny.**

---

## KROK 3 — GENEROWANIE KODU

Zbuduj `index.html` zawierający kompletną landing page zgodnie z poniższymi wymaganiami:

### STRUKTURA SEKCJI (w tej kolejności)

```
1. HERO              — pełnoekranowy, z tytułem gry, tagline i CTA
2. GAMEPLAY TRAILER  — osadzony trailer lub mockup telefonu ze screenshotem
3. KEY FEATURES      — 3–5 feature cards z ikonami i opisami
4. SCREENSHOTS       — karuzela / swiper z ekranami gry
5. SOCIAL PROOF      — oceny (gwiazdki), liczba pobrań, recenzje
6. DOWNLOAD CTA      — przyciski App Store + Google Play
7. FOOTER            — minimalistyczny
```

### WYMAGANIA TECHNICZNE

**HTML/CSS:**
- Pojedynczy plik `index.html`, zero zewnętrznych zależności (tylko CDN fonts)
- Czcionki z Google Fonts (NIE używaj Inter, Roboto, Arial — wybierz coś ekspresywnego)
- CSS Custom Properties (`--color-*`, `--font-*`, `--space-*`) dla spójności
- Pełna responsywność: mobile-first (375px → 768px → 1440px)
- Sekcja Hero: min-height 100dvh, CTA w zasięgu kciuka (dolna połowa ekranu)

**Animacje i efekty (OBOWIĄZKOWE):**
- Scroll-triggered fade-in dla sekcji (Intersection Observer API)
- Parallax na tle Hero (CSS transform + JS scroll listener, lekki — max 20px offset)
- Particle system lub CSS-animated background w Hero (gwiazdy / cząsteczki / geometryczne kształty — dopasowane do gatunku)
- Hover states na CTA buttons: scale + glow + color shift (CSS transition 200ms)
- Staggered animation dla feature cards (animation-delay: 0ms, 100ms, 200ms...)
- Glassmorphism na kartach (backdrop-filter: blur + translucent background)
- Micro-interaction: przycisk Download pulsuje co 4s gdy jest w viewport

**Typografia:**
- Display font (Google Fonts) — duży, ekspresywny, pasujący do gatunku
- Body font — czytelny, charakterny
- Hierarchia: Hero title ≥ 64px, section titles ≥ 36px, body ≥ 16px
- Letter-spacing i line-height celowo dobrane do klimatu

**Kolory:**
- Użyj `COLOR_PALETTE` z kroku 1
- Jeśli brak — wybierz paletę pasującą do gatunku (patrz tabela powyżej)
- Dominant bg + 1–2 akcenty + text color
- Przyciski App Store / Google Play: oryginalne brand colors (#000 + #fff / #01875f)

**Screenshoty gry:**
- Jeśli `SCREENSHOTS` istnieją → użyj ich jako `<img src="...">` z relatywną ścieżką
- Jeśli brak → stwórz CSS mockupy telefonów z gradient placeholder i tekstem nazwy gry
- Mockup telefonu: border-radius: 40px, box-shadow wielowarstwowy, "notch" na górze

**CTA Buttons:**
- "Download on App Store" — czarny, apple logo (SVG inline)
- "Get it on Google Play" — ciemnozielony (#01875f), play store logo (SVG inline)
- Jeśli brak URLi: `href="#download"` z anchor do sekcji

### SOCIAL PROOF (jeśli brak danych — użyj tych placeholderów):
```
★★★★★  4.8/5  •  50,000+ Downloads  •  "Absolutely addictive!" — AppAdvice
```

### SEO & META
```html
<title>{GAME_NAME} — {TAGLINE}</title>
<meta name="description" content="{GAME_DESCRIPTION}">
<meta property="og:title" content="{GAME_NAME}">
<meta property="og:image" content="{ICON_PATH lub pierwszy screenshot}">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="{dominant color}">
```

---

## KROK 4 — QUALITY CHECKLIST

Przed zapisaniem pliku sprawdź każdy punkt:

- [ ] Plik otwiera się bez błędów w przeglądarce (zero broken JS)
- [ ] Na mobile (375px) hero CTA jest widoczne bez scrollowania
- [ ] Wszystkie animacje mają `prefers-reduced-motion` fallback
- [ ] Kontrast tekstu ≥ 4.5:1 (WCAG AA)
- [ ] Brak hardcodowanych URLi bez zmiennych (użyj CSS vars i JS constants na górze)
- [ ] Czas ładenia: brak blokowaych zasobów, CSS inline, JS defer/async
- [ ] Screenshoty/ikony ładują się z relatywnych ścieżek (nie absolutnych)
- [ ] Footer zawiera: copyright, platformy, (opcjonalnie) Privacy Policy link

---

## KROK 5 — OUTPUT

Zapisz gotową stronę jako `index.html` w katalogu głównym projektu.

Na końcu wypisz krótkie podsumowanie:
```
✅ GAME:        {GAME_NAME}
✅ GENRE:       {GENRE}
✅ STYLE:       {wybrany styl estetyczny}
✅ FONTS:       {display font} + {body font}
✅ COLORS:      {primary} / {accent1} / {accent2}
✅ SCREENSHOTS: {ile użyto / czy są placeholdery}
✅ STORE LINKS: {App Store: tak/nie} {Google Play: tak/nie}
```

---

## DODATKOWE ZASADY

- **Nigdy** nie pytaj o brakujące dane — infer lub wymyśl na podstawie kontekstu
- **Nigdy** nie używaj stockowych zdjęć z zewnętrznych URLi (tylko relative paths lub CSS)
- **Nigdy** nie generuj pliku jeśli nie przeskanowałeś najpierw folderu projektu
- Jeśli gra ma silny lore / świat — oddaj go w copy (hero subtitle, feature descriptions)
- Kod ma być czysty, komentowany i gotowy do produkcji
- Jeden plik. Zero frameworków. Działa offline.

---

*Prompt stworzony z uwzględnieniem trendów 2026: mobile-first design, glassmorphism, scroll-triggered animations, particle systems, bold typography, thumb-zone CTA placement.*
