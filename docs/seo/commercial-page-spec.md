# Commercial Page — специфікація

Сторінка `/commercial-cleaning-toronto` — **аналог головної для бізнес-аудиторії**, не money-сторінка послуги. Модель принципово інша, тому загальний шаблон `seo-page-template.md` до неї застосовується частково.

**Читати разом із:** `keyword-map.md` (комерційний кластер) · `schema-templates.json` · `design-system-v3.md`

---

## 🔴 Головна відмінність: ціни немає

Residential працює на фіксованих цінах — це основне УТП. Commercial працює **за запитом**: обсяги рахуються індивідуально за площею, частотою та типом приміщення.

Наслідки, які пронизують усю сторінку:

| Елемент | Residential | Commercial |
|---|---|---|
| Ціна в hero | `from $120` | `Custom quote` |
| Калькулятор | є, 4 тайли | **немає** |
| `Offer` у schema | є, з ціною | **не вставляється** |
| CTA | `Get my price` → `/book` | `Request a quote` → форма запиту |
| Обіцянка | точне число до бронювання | відповідь протягом дня |

⚠ **Не вигадувати ціну, щоб «було як на головній».** Число в schema, якого немає на сторінці, — порушення. Число, яке не відповідає реальній угоді, — втрата довіри на першому ж дзвінку.

---

## Аудиторія та інтент

Хто шукає: офіс-менеджери, власники малого бізнесу, керуючі будівель, франчайзі.

Що для них важливо — у порядку пріоритету:

1. **Страхування й відповідальність** — хто платить, якщо щось пошкодили
2. **Робота після годин** — бізнес не має зупинятись
3. **Контракт і регулярність** — не разова послуга, а графік
4. **Перевірені люди** — доступ до приміщення поза робочим часом
5. **Ціна** — важлива, але не перша

Це інший порядок, ніж на residential, де ціна й швидкість бронювання — перші два пункти.

---

## Пошукові запити

Власник: `commercial cleaning toronto`

| Запит | Де живе |
|---|---|
| `commercial cleaning toronto` | ця сторінка, H1 |
| `office cleaning toronto` | `/office-cleaning-toronto` (окрема) |
| `janitorial services toronto` | `/janitorial-cleaning-toronto` (окрема) |
| `medical office cleaning` | `/healthcare-cleaning-toronto` (окрема) |
| `retail cleaning toronto` | `/retail-cleaning-toronto` (окрема) |

Якорі всередині цієї сторінки, поки не окремі URL: `#warehouse`, `#rental`, `#fitness`, `#spa-salon`

⚠ Ця сторінка — хаб над комерційним кластером. Вона **не** оптимізується під `office cleaning` — той запит належить окремій сторінці. Інакше канібалізація всередині власного кластера.

---

## Мета-теги

**Title:**
```
Commercial Cleaning Toronto & GTA · Insured & After-Hours | VeroCleaning
```
Не ціна в title, а те, що реально шукають: страхування й робота після годин.

**Meta description:**
```
Insured commercial cleaning for offices, retail and clinics across Toronto and the GTA. After-hours service, background-checked crews, custom quote within one business day.
```

---

## Структура зон

Із 12 універсальних зон money-сторінки застосовуються не всі. Порядок під B2B-інтент:

| # | Зона | H2 (приклад) | Примітка |
|---|---|---|---|
| 1 | Hero | — | H1 + lede + `Request a quote`, без ціни |
| 2 | Trust strip | — | insured · bonded · background-checked · after-hours |
| 3 | Типи приміщень | `Spaces we clean` | сітка: офіс, ритейл, клініка, склад, спортзал, салон, оренда |
| 4 | Що входить | `What a commercial clean covers` | чеклист за зонами приміщення |
| 5 | Графік і частота | `Daily, weekly or one-time` | контрактна модель |
| 6 | Після годин | `We work when you don't` | ⭐ ключовий блок для B2B |
| 7 | Страхування | `Insured and accountable` | ⭐ другий ключовий блок |
| 8 | Як почати | `From quote to first clean` | 3 кроки |
| 9 | Service areas | `Toronto & the GTA` | ті самі 20 міст |
| 10 | FAQ | `Commercial cleaning questions` | під B2B, не під побут |
| 11 | Форма запиту | `Request a quote` | замість калькулятора |
| 12 | Final CTA | — | телефон + форма |

**Зони, яких тут немає:** калькулятор, Before/After (побутовий формат), Related services у residential-сенсі.

---

## FAQ — під B2B-інтент

7 питань. Побутові питання («чи потрібно надавати миючі засоби») сюди не переносяться.

Приблизний набір:

1. How is commercial cleaning priced?
2. Do you work after business hours?
3. Are you insured?
4. Do I need to sign a contract?
5. How quickly can you start?
6. Do you clean medical or food-service spaces?
7. Who has access to our space?

Ліміти ті самі, що в `seo-page-template.md`: питання 32–56 символів, відповідь 110–229.

🔴 **Перше речення відповіді — конкретика.** Для B2B це не ціна, а термін, умова або факт: «Quotes are returned within one business day», «We carry $2M liability insurance» (⚠ число підтвердити у власника — без підтвердження не писати).

---

## Structured data

| Блок | Джерело | Особливість |
|---|---|---|
| `Service` | `schema-templates.json §2` | **БЕЗ `offers`** |
| `FAQPage` | `schema-templates.json §3` | — |
| `BreadcrumbList` | `schema-templates.json §4` | — |

Приклад Service без ціни:
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "serviceType": "Commercial Cleaning",
  "name": "Commercial Cleaning in Toronto & the GTA",
  "provider": { "@id": "https://verocleaning.ca/#business" },
  "areaServed": { "@type": "City", "name": "Toronto" }
}
```

⚠ `LocalBusiness` тут не дублюється — він живе тільки на головній. Посилання йде через `@id`.

---

## Перелінковка

| Напрямок | Реалізація |
|---|---|
| Головна → Commercial | перемикач у хедері |
| Commercial → Головна | той самий перемикач, зворотно |
| Commercial → підсторінки | картки типів приміщень ведуть на `/office-cleaning-toronto` тощо |
| Commercial → форма | CTA в hero, після кожного ключового блока, у Final CTA |

⚠ **Commercial не посилається на `/book`.** Residential-калькулятор не обслуговує комерційні обсяги — це гарантований негативний досвід.

---

## Відкриті питання до власника

Без відповідей сторінку публікувати не можна — це не косметика, а фактаж, який не вигадується:

| Питання | Навіщо |
|---|---|
| Сума страхового покриття | Ключовий trust-сигнал для B2B, має бути числом |
| Чи є bonding, не тільки insurance | Різні речі, B2B-клієнти питають окремо |
| Мінімальний обсяг або площа | Щоб не витрачати час на нерелевантні заявки |
| Чи працюємо з клініками / харчовими | Інші санітарні вимоги |
| Термін відповіді на запит | Обіцянка в hero має бути реальною |
| Чи є контрактна форма | «Do I need to sign a contract» — питання FAQ №4 |

🔴 Жоден із цих фактів не береться з residential-сторінок і не вигадується за аналогією з ринком.
