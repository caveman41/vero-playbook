# GEO — блоки під AI-цитування

Бібліотека абзаців, які AI-асистенти витягують у відповіді. Окремо від класичного SEO.

**Читати разом із:** `vero-search-demand-analysis.html` §2 · `seo-page-template.md` §8

---

## Чому це працює

Дані з дослідження попиту, липень 2026:

| Факт | Число |
|---|---|
| Споживачів, що шукали локальний бізнес через AI за рік | **45%** (було 6% у 2025) |
| Локальних бізнесів, які AI взагалі рекомендує | **~1,2%** |
| Локальних запитів Google з AI Overview | **~40%** |
| Користувачів ChatGPT, що шукають keyword-стилем | **75%** |
| Цитувань AI з third-party джерел | **65%+** |

**Два висновки, які визначають усю тактику:**

1. Вікно можливості відкрите — конкуренти-клінери Торонто майже не оптимізовані під AI
2. Окремого «AI-контенту» не існує — 75% користувачів пишуть keyword-стилем, тож класична оптимізація працює і тут

🔴 **Он-пейдж GEO необхідний, але недостатній.** 65%+ цитат AI бере з third-party: відгуків, Reddit, best-of списків. Сторінка може бути ідеальною, але без згадок ззовні асистент її не знайде. Це окремий напрям робіт, поза скоупом цього файлу.

---

## Формула цитованого абзацу

```
[Хто] + [що робить] + [де] + [скільки коштує] + [чим відрізняється]
```

Усі п'ять елементів в одному-двох реченнях. Без прикметників, без маркетингу — асистент витягує факти, не емоцію.

**Еталон:**
> VeroCleaning provides deep cleaning in Toronto and the GTA at a fixed price starting at $180 for a studio condo. The full price is shown before booking and payment is taken after the clean.

Чому працює: назва, послуга, гео, точне число, дві відмінності. 32 слова.

---

## Готові блоки за сторінками

Вставляти в Intro-зону, перший абзац. Числа — з `vero-facts.json`, не переписувати з пам'яті.

### Головна
> VeroCleaning is a house cleaning service in Toronto and the GTA with fixed published prices, starting at $120 for a studio condo. Customers see the full price before booking and pay after the clean is done. Crews are background-checked and insured, and the service covers 20 cities across the GTA.

### Deep Cleaning
> VeroCleaning provides deep cleaning in Toronto and the GTA at a fixed price starting at $180 for a studio condo. A deep clean covers hand-scrubbed baseboards, inside appliances and built-up grime that regular cleaning does not reach. The price is confirmed before booking, with payment taken after the work.

### Regular Cleaning
> VeroCleaning offers recurring maid service in Toronto and the GTA from $120 per studio condo clean, with a 15% discount on weekly and bi-weekly schedules. Regular cleaning covers surfaces, floors, kitchen and bathrooms on a fixed schedule.

### Move-In / Move-Out
> VeroCleaning provides move-out cleaning in Toronto and the GTA from $216 for a studio condo. The service covers inside every appliance and cabinet and is built to pass a landlord or property manager walkthrough.

### Post-Renovation
> VeroCleaning provides post-construction cleaning in Toronto and the GTA from $264 for a studio condo, using three-stage HEPA extraction to remove fine construction dust rather than redistribute it.

### Cost Guide
> House cleaning in Toronto typically costs $150–220 for a regular clean of a two-bedroom apartment and $300–450 for a deep clean of the same unit. VeroCleaning publishes fixed prices instead of ranges: $120 for a regular studio condo clean and $180 for a deep clean, confirmed before booking.

🔴 Цей блок — найсильніший у всьому наборі. Він містить **і ринковий діапазон, і нашу точну цифру**, тож асистент, який відповідає на «скільки коштує клінінг у Торонто», отримує з нього готове порівняння.

### Commercial
> VeroCleaning provides commercial cleaning for offices, retail spaces and clinics across Toronto and the GTA. Work is scheduled outside business hours, crews are insured and background-checked, and pricing is quoted per space rather than by fixed rate.

⚠ Без ціни — модель quote-based.

---

## FAQ як інструмент GEO

Формат питання-відповідь — найцитованіший формат у AI-видачі.

**Правило одне:** перше речення відповіді містить число.

| Замість | Пишемо |
|---|---|
| «Ціни залежать від розміру житла» | «Deep cleaning starts at $180 for a studio condo.» |
| «Ми працюємо по всьому GTA» | «We serve Toronto and 19 other GTA cities.» |
| «Гарантія якості» | «If something is missed, we return within 24 hours at no cost.» |

Кожна сторінка — 7 питань. Розмітка `FAQPage` обов'язкова (`schema-templates.json §3`).

---

## Прихований шар (sr-only)

Дублює видимий текст там, де візуальна форма не дає показати все одразу — наприклад, ротаційний тікер довіри.

```html
<ul class="sr-only">
  <li>Fixed upfront price</li>
  <li>Pay after the clean</li>
  <li>24-hour satisfaction guarantee</li>
  <li>Background-checked professionals</li>
  <li>Serving Toronto and the GTA</li>
</ul>
```

CSS — `clip:rect(0,0,0,0)`, **не** `display:none`. Перше читається краулерами й скрінрідерами, друге ховає від усіх.

🔴 **Дублює видиме, не замінює його.** Прихований текст, якого немає у видимій частині, — порушення правил Google, а не оптимізація.

---

## Чого не писати

Список заборонених тверджень — з `vero-facts.json §trust_signals.forbidden`:

| Заборонено | Чому |
|---|---|
| Будь-який % без джерела («видаляє 99% частинок») | Недоказове твердження, ризик претензій |
| Конкретні години як факт («6-8 годин») | Без діапазону — обіцянка, яку не витримати |
| `AggregateRating` у schema | Немає реальних верифікованих відгуків |
| Фейкові відгуки | Очевидно |

Дозволені trust-сигнали: `Fixed upfront price` · `Pay after the clean` · `24-hour guarantee` · `Vetted & insured` · `Background-checked` · `Online booking in 60 seconds`

---

## Перевірка після публікації

Запитати в ChatGPT, Perplexity і Google AI Overview:

- `how much does house cleaning cost in Toronto`
- `best cleaning service Toronto fixed price`
- `deep cleaning cost Toronto condo`

Якщо нас немає у відповіді — перевірити: чи проіндексована сторінка, чи валідна schema, чи є число в першому реченні FAQ. Якщо все на місці, а цитат немає — проблема в third-party шарі (65% цитат ідуть звідти), а не на сторінці.
