# Keyword Map — запит → сторінка

Жорстка прив'язка пошукових запитів до URL. Головний захист від канібалізації: коли дві наші сторінки борються за один запит, Google не знає, яку показати, і просідають обидві.

**Джерело кластерів:** `vero-search-demand-analysis.html` (липень 2026)
**Джерело інвентарю URL:** `content-strategy.html` v2.4

---

## Правило одного власника

**У кожного запиту рівно одна сторінка-власник.** Решта сторінок можуть згадувати тему, але не оптимізуються під неї: не виносять у title, не роблять H1, не будують під неї FAQ.

Якщо з'являється новий запит, а власника немає — див. «Коли створювати нову сторінку» внизу.

---

## Ядро — транзакційні запити

| Запит-власник | Сторінка | Варіації, які теж належать цій сторінці |
|---|---|---|
| `house cleaning toronto` | `/` (головна) | house cleaning services toronto, cleaning service toronto, home cleaning toronto |
| `deep cleaning toronto` | `/deep-cleaning-toronto` | deep house cleaning toronto, spring cleaning toronto, one-time deep clean |
| `move out cleaning toronto` | `/move-out-cleaning-toronto` | move in cleaning toronto, end of lease cleaning, moving out cleaning service |
| `regular cleaning toronto` | `/regular-cleaning-toronto` | **maid service toronto**, recurring house cleaning, weekly cleaning, biweekly house cleaning |
| `post construction cleaning toronto` | `/post-renovation-cleaning` | post renovation cleaning, after construction cleanup |
| `condo cleaning toronto` | `/condo-cleaning-toronto` | apartment cleaning toronto, condo cleaning services |
| `house cleaning services toronto` (тип житла) | `/house-cleaning-toronto` | townhouse cleaning → якір `#townhouse` |
| `airbnb cleaning toronto` | `/airbnb-cleaning-toronto` | short term rental cleaning, turnover cleaning |

🔴 **`maid service` — окремо.** Дослідження показало, що це системний гап: конкуренти ранжуються за ним, у нас термін відсутній. Власник — `/regular-cleaning-toronto`. Реалізація: H2 «Recurring maid service in Toronto», `alternateName` у схемі `[Maid Service, Recurring House Cleaning]`, FAQ про weekly/biweekly + знижку 15%. Це найцінніший кластер за LTV.

---

## Інформаційні запити

| Запит-власник | Сторінка | Примітка |
|---|---|---|
| `how much does house cleaning cost in toronto` | `/cleaning-prices-toronto` | **Найбільший непокритий кластер.** Головне джерело AI-цитат |
| `cleaning prices toronto` | `/cleaning-prices-toronto` | те саме |
| `deep cleaning vs regular cleaning` | `/deep-cleaning-toronto` (порівняльна зона) | не окрема сторінка — вісь розведення слабка |

🔴 **Cost guide — стратегічний пріоритет.** Ринок публікує діапазони ($150–220 regular, $300–450 deep для 2-bed). Ми єдині, хто відповідає точним числом. AI-системи цитують саме конкретні числа. Заголовок оновлюється щороку: 2026 → 2027.

---

## Комерційні запити

| Запит-власник | Сторінка |
|---|---|
| `commercial cleaning toronto` | `/commercial-cleaning-toronto` |
| `office cleaning toronto` | `/office-cleaning-toronto` |
| `janitorial services toronto` | `/janitorial-cleaning-toronto` |
| `medical office cleaning` | `/healthcare-cleaning-toronto` |
| `retail cleaning toronto` | `/retail-cleaning-toronto` |

Якорі всередині `/commercial-cleaning-toronto`: `#warehouse`, `#rental`, `#fitness`, `#spa-salon` — поки не окремі сторінки.

---

## Спеціалізовані послуги

| Запит | Сторінка / якір | Статус |
|---|---|---|
| `carpet cleaning toronto` | `/carpet-cleaning-toronto` | окрема сторінка |
| `rug cleaning toronto` | `/rug-cleaning-toronto` | окрема сторінка · ⚠ ціни немає |
| `appliance cleaning toronto` | `/appliance-cleaning-toronto` | SKU-сітка |
| `kitchen cleaning toronto` | `/kitchen-cleaning-toronto` | — |
| `bathroom cleaning toronto` | `/bathroom-cleaning-toronto` | — |
| `steam cleaning` | `/cleaning-add-ons#steam` | якір |
| `upholstery cleaning` | `/cleaning-add-ons#upholstery` | якір |
| `mattress cleaning` | `/cleaning-add-ons#mattress` | якір |
| `hardwood floor cleaning` | `/cleaning-add-ons#hardwood` | якір · ⚠ чистка чи полірування — не вирішено |
| `tile and grout cleaning` | `/cleaning-add-ons#tile-grout` | якір |
| `basement cleaning` | `/deep-cleaning-toronto#basement` | якір |
| `patio cleaning` | `/cleaning-add-ons#patio` | якір |

---

## 🔴 Запити, за які ми НЕ боремось

| Запит | Чому |
|---|---|
| `window cleaning toronto` | Інтент належить exterior-спеціалістам із water-fed pole обладнанням, ціни $130–380/будинок. Наш продукт — interior windows $30/вікно як add-on. Конкурувати без обладнання — програшна ставка. Власник: `/cleaning-add-ons#windows`, реframe на «interior window cleaning» |
| `cleaning jobs toronto` | Інтент працевлаштування, не клієнтський |
| `cleaning supplies toronto` | Товарний інтент |
| Погодинні запити (`cleaning service hourly rate`) | Суперечать fixed-price моделі — головному УТП |

---

## Гео-запити

Формат: `[послуга] + [місто]`. Наразі всі гео-варіації обслуговує блок Service areas на кожній сторінці (20 міст).

Окремі локаційні сторінки (`/deep-cleaning-mississauga` тощо) **не створені** і не плануються до появи сигналів у Search Console. Причина: 20 міст × 8 послуг = 160 сторінок тонкого контенту — класична пастка масштабування.

---

## Коли створювати нову сторінку

Сторінка створюється **лише** за наявності осі розведення з усіма наявними сторінками:

| Вісь | Приклад |
|---|---|
| Scope | deep vs regular — різний обсяг робіт |
| Аудиторія | residential vs commercial |
| Метод | extraction vs wiping |
| Ціна | fixed vs quote-based |

🔴 **«Стадія воронки» — не вісь.** Якщо єдине розведення — «ця сторінка для тих, хто ще думає» — це не обґрунтування, а бажання мати ще одну сторінку. Саме через це скасовано `/residential-cleaning-toronto`: пара «головна ↔ residential-хаб» не мала жодної з чотирьох осей.

---

## Перевірка перед публікацією сторінки

- [ ] Головний запит цієї сторінки є в таблиці вище і не належить іншій
- [ ] Title містить запит-власник
- [ ] H1 містить запит-власник
- [ ] Жодна інша сторінка не має цей запит у title чи H1
- [ ] Якщо запиту в таблиці немає — визначена вісь розведення

---

## Як перевірити канібалізацію постфактум

У Google Search Console → Performance → фільтр по запиту. Якщо за одним запитом показуються дві наші сторінки з чергуванням позицій — канібалізація. Рішення: слабшу сторінку переорієнтувати або злити в сильнішу з 301.

---

## Відкриті питання

| Питання | Впливає на |
|---|---|
| Ціна Rug Cleaning невідома | `/rug-cleaning-toronto` — не публікувати без ціни |
| Hardwood: чистка чи полірування? | Якір `#hardwood`, формулювання і скоуп |
| Чи є в нас обладнання для extraction? | Carpet і Rug — чи ми виконавець, чи посередник |
