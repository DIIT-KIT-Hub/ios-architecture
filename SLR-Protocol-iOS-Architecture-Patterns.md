# SLR Protocol — Software Architecture Patterns for Swift-Based iOS Applications

> **Systematic Literature Review Protocol.** Цей документ фіксує всі методологічні рішення *до* початку пошуку літератури і стане основою розділу **Methods** статті.

| Поле | Значення |
|---|---|
| Робоча назва статті | *Software Architecture Patterns for Swift-Based iOS Applications: A Systematic Literature Review* |
| Методологія | PRISMA 2020 (Page et al., 2021) + Kitchenham & Charters (2007) guidelines for SLR in software engineering |
| Команда | Андрєєв В. Р. (студент, виконавець), Жеваго О. О. (ментор), Шаравара В. В. (ментор) |
| Репозиторій | https://github.com/DIIT-KIT-Hub/ios-architecture (гілка `dev`) |

---

## 0. Загальні положення

### Мета огляду

Систематизувати рецензовану наукову літературу про архітектурні патерни (MVC, MVP, MVVM, VIPER, Clean Architecture, TCA та інші підходи) для **iOS-застосунків, розроблених мовою Swift**, визначити, за якими критеріями та метриками їх порівнюють, які переваги/обмеження підтверджено якими типами доказів, і які прогалини лишаються. Результати огляду стануть базою для другого (емпіричного) дослідження.

---

## 1. Research Questions

Формулювання англійською — піде в статтю; українською — пояснення для команди.

**RQ1.** *Which software architecture patterns for iOS applications developed in Swift are studied in the peer-reviewed literature, and how are they defined and implemented?*
> Які архітектурні патерни для iOS-застосунків, розроблених мовою Swift, розглядаються в рецензованій літературі та як саме вони визначаються й реалізуються?

**RQ2.** *Which quality attributes, criteria, and metrics are used to evaluate or compare these patterns, and by which research methods (controlled experiment, case study, survey, repository mining, analytical comparison, experience report)?*
> Які атрибути якості, критерії та метрики використовують для оцінювання/порівняння патернів і якими методами дослідження?

**RQ3.** *What advantages and limitations are reported for each pattern?*
> Які переваги й обмеження заявлено для кожного патерну?

**RQ4.** *What research gaps and directions for future work are identified, in particular regarding modern Swift-specific approaches?*
> Які прогалини та напрями майбутніх досліджень визначено, зокрема щодо сучасних Swift-специфічних підходів?

Додатково (не окреме RQ, а описова статистика в Results): розподіл включених робіт за роками, типами видань (журнал/конференція), країнами, типами дослідження.

**Зв'язок RQ ↔ протокол:** RQ1 → PICOC-P/I, IC1; RQ2 → PICOC-O/C, форма екстракції; RQ3 → PICOC-O; RQ4 → секція Discussion.

---

## 2. PICOC framework

| Елемент | Що описує | Наш огляд | Коментар |
|---|---|---|---|
| **Population** | Обʼєкт дослідження | iOS applications implemented in Swift | Не входять: застосунки виключно на Objective-C; watchOS/macOS-only; крос-платформні фреймворки (Flutter, React Native, Xamarin, KMP) як основний об'єкт. Якщо мова реалізації в роботі не вказана — див. IC1 |
| **Intervention** | Що застосовується | Application-level software architecture patterns: MVC, MVP, MVVM (incl. MVVM-C), VIPER, Clean Architecture (incl. Clean Swift/VIP, Onion, Hexagonal), The Composable Architecture (TCA), and other unidirectional-data-flow patterns (Redux-like, Flux-like, Elm/MVU, MVI); auxiliary patterns (Coordinator, Router, RIBs) — only when discussed as part of app architecture | Список **відкритий**: патерн, знайдений під час скринінгу і такий, що відповідає IC1, додається сюди окремим комітом до протоколу |
| **Comparison** | З чим порівнюється | (a) Another architecture pattern from the list above (pairwise or multi-pattern comparison); (b) no explicit comparator — single-pattern studies are included because RQ1 and RQ3 are descriptive | Компаратор **необов'язковий** для включення |
| **Outcome** | Вимірювані результати | Software quality attributes: maintainability, modifiability, testability, reusability, modularity; structural metrics (coupling, cohesion, complexity, LOC); runtime performance (CPU, memory, launch time, build time); developer-related outcomes (productivity, development effort, learning curve, cognitive load); reported advantages/limitations | Для RQ3 також фіксуємо тип доказу |
| **Context** | Тип досліджень і середовище | Peer-reviewed empirical studies (controlled/quasi-experiments, case studies, surveys, repository mining), analytical comparisons, and experience reports; academic or industrial setting | Вторинні дослідження (SLR/mapping) не включаються, але використовуються для snowballing |

---

## 3. Keywords and synonyms

Позначення в колонці **У рядку?**: **S** — термін входить у пошукові рядки (розд. 4); **V** — лише словник для скринінгу/екстракції (термін надто загальний або шумний для пошуку).

### 3.1. Population — платформа і мова

| Тип | Терміни | У рядку? | Примітка |
|---|---|---|---|
| Основні | iOS, iOS app / application / development / software / platform | S | Омоніми: *IOS* = intraoral scanner, Cisco IOS → див. `AND NOT` у 4.2. «iOS» лишається в рядках, бо більшість Swift-робіт в анотації називають платформу, а не мову; мова перевіряється на скринінгу (IC1) |
| Пристрої | iPhone, iPad | S | iPad також дає освітні/медичні статті — відсіюється на скринінгу |
| Мова | Swift, Swift language, Swift programming, Apple Swift | S (лише як фраза) | Голе `Swift` у Scopus = гамма-обсерваторія Swift, Swift/T, SWIFT (банки), прикметник *swift* → у Scopus лише `"Swift language"`, `"Swift programming"`, `"Apple Swift"`, `SwiftUI`; у GS — лише в полі *Title words* PoP |
| Фреймворки | SwiftUI, UIKit, Cocoa Touch, Combine, Swift Concurrency | S (SwiftUI, UIKit) / V (інші) | SwiftUI важливий маркер сучасних робіт (MV/MVVM, TCA) |
| Виробник | Apple, Apple platform | V | Надто загальні |
| Поза межами (для розпізнавання на скринінгу) | Objective-C, Flutter, React Native, Xamarin, Kotlin Multiplatform, Ionic, .NET MAUI | V | Маркери EC3 |

### 3.2. Intervention — архітектурні патерни

| Тип | Терміни | У рядку? | Примітка |
|---|---|---|---|
| Родові | software architecture, application architecture, app architecture, mobile architecture, architectur\* pattern\* (architecture pattern, architectural pattern), architectural style\*, architectural design, presentation layer, UI architecture | S | Ядро запиту Q2 (розд. 4.2) |
| Суміжні | design pattern\*, structural pattern\*, state management | S (design pattern\*, state management) / V | GoF-патерни не наша тема, але статті design patterns in iOS часто містять MVC/MVVM |
| MVC | MVC, Model-View-Controller, Model View Controller, Massive View Controller | S | |
| MVP | MVP, Model-View-Presenter | S (Scopus) / обережно в GS | Омонім: *MVP* = minimum viable product → у GS лише повна назва або лише в полі *Title words* PoP |
| MVVM | MVVM, Model-View-ViewModel, MVVM-C, ViewModel | S (перші три) / V (ViewModel) | |
| VIPER | VIPER, View-Interactor-Presenter-Entity-Router | S | Омоніми: змії (viper), VIPER-протоколи → безпечно лише з платформним блоком |
| Clean | Clean Architecture, Clean Swift, VIP (View-Interactor-Presenter), Onion Architecture, Hexagonal Architecture, Ports and Adapters, Layered Architecture | S (крім Layered, VIP) / V | «Layered» надто загальне; «VIP» — омонім |
| TCA | The Composable Architecture, Composable Architecture, TCA | S (повна назва) / V (TCA) | Голе *TCA* = tricarboxylic acid; автори завжди наводять повну назву |
| Однонаправлений потік | unidirectional data flow, UDF, Redux, Redux-like, ReSwift, Flux, Flux-like, Elm Architecture, MVU, Model-View-Update, MVI, Model-View-Intent | S (крім UDF, Flux лише як фраза «Flux pattern/architecture») | *Flux* = фізика; *UDF* = user-defined function |
| Допоміжні | Coordinator pattern, Router pattern, RIBs | S (Coordinator) / V | *RIBs* = ребра (медицина) |

### 3.3. Comparison — порівняння

| Тип | Терміни | У рядку? |
|---|---|---|
| Прямі | compar\* (comparison, comparative, comparing), versus, vs | S (compar\*) / V |
| Оцінювання | evaluat\*, assessment, benchmark\*, empirical, controlled experiment | S (evaluat\*, empirical, experiment\*) / V |
| Вибір і компроміси | trade-off\*, architecture selection, architectural decision, decision criteria | V |
| Перехід між патернами | migration, refactoring, architectural refactoring, re-architecting | V |

### 3.4. Outcome — атрибути якості та метрики

| Тип | Терміни | У рядку? |
|---|---|---|
| Родові | software quality, code quality, quality attribute\*, non-functional requirement\*, ISO/IEC 25010 | S (code quality, quality attribute\*) / V |
| Супровід | maintainab\*, modifiability, evolvability | S (maintainab\*) / V |
| Тестованість | testab\*, test coverage, testing effort | S (testab\*) / V |
| Складність | complexity, cyclomatic complexity, cognitive complexity, LOC | V |
| Структурні метрики | coupling, cohesion, modularity, separation of concerns | V |
| Гнучкість | scalability, extensibility, reusability, flexibility | V |
| Розробник | developer productivity, development effort/time, developer experience, learning curve, cognitive load | V |
| Зрозумілість | readability, understandability | V |
| Борг | technical debt, code smell\*, anti-pattern\* | V |
| Runtime | performance, memory usage, CPU usage, app launch time, build time | V |

### 3.5. Context — тип дослідження

| Тип | Терміни | У рядку? |
|---|---|---|
| Емпірика | empirical study/evaluation/evidence | S (empirical) |
| Кейси | case study, industrial case study | S (case study) |
| Експерименти | controlled experiment, quasi-experiment | S (experiment\*) |
| Опитування | survey, questionnaire, interview study, practitioner survey | V |
| Аналіз коду | mining software repositories, MSR, open-source analysis | V |
| Досвід | experience report, lessons learned, industrial report | V |
| Вторинні | systematic review, mapping study, literature review | V (для EC8 і snowballing) |

---

## 4. Search strings per database

### 4.1. Стратегія пошуку (огляд)

| Джерело | Хто | Навіщо | Що експортуємо |
|---|---|---|---|
| **Scopus** | Ментор | Основна індексна база: покриває IEEE Xplore, ACM DL, Springer, Elsevier, MDPI, більшість Scopus-журналів. Підтримує повний булевий синтаксис | RIS (усі поля) → Zotero `01_Scopus/Qn` |
| **Google Scholar** (через Publish or Perish) | Студент | Доповнює Scopus: конференції/журнали поза Scopus, робочі версії. Не підтримує складний синтаксис, ліміт 1000 записів/запит, індексує повний текст | RIS з PoP → Zotero `02_GoogleScholar/Gnn` |
| **Snowballing** (backward + forward) | Студент | Обов'язковий етап після скринінгу: списки літератури та "Cited by" усіх включених робіт + усіх знайдених вторинних досліджень (EC8) | Zotero `06_Snowballing` |

**Чому пошукові рядки не вимагають слова Swift.** Значна частина релевантних робіт в анотації називає лише платформу (iOS app, iPhone application) і не згадує мову реалізації; мову видно лише з повного тексту. Якби рядок вимагав `Swift`, ми втратили б ці роботи. Тому платформний блок рядків побудовано з термінів *iOS / iPhone / iPad / SwiftUI / UIKit / Swift-фрази*, а Swift-обмеження застосовується на скринінгу через IC1 і EC3. Objective-C у рядках не використовується: роботи виключно на Objective-C не є об'єктом огляду, а ті, що порівнюють Objective-C і Swift, усе одно містять терміни платформи.

**Структура групової бібліотеки Zotero** (єдина для всіх issues; номери відповідають порядку етапів):

| Колекція | Що містить | Етап |
|---|---|---|
| `01_Scopus/Q1` … `Q3` | Сирі імпорти Scopus, по одній підколекції на запит | Identification |
| `02_GoogleScholar/G01` … `G23` | Сирі імпорти PoP, по одній підколекції на запит (піддіапазони років — у ту саму підколекцію) | Identification |
| `03_All_Deduplicated` | Об'єднання всіх записів після Zotero *Duplicate Items → Merge* | Dedup |
| `04_Included_TA` | Записи з рішенням *Include* після title/abstract-скринінгу | Screening |
| `05_Included` | Фінальний набір після full-text-скринінгу (+ включені зі snowballing) | Eligibility/Included |
| `06_Snowballing/Backward`, `/Forward`, `/secondary` | Кандидати зі списків літератури, з «Cited by», та знайдені вторинні огляди (EC8) | Snowballing |

Рішення скринінгу фіксуються **тегами** на записах (`included`, `EC1` … `EC10`, `grey-thesis`, `objc-only`, `language-not-reported`), а не переміщенням між колекціями — так один запис може бути одночасно в `01_Scopus/Q1` і `03_All_Deduplicated`, і числа для PRISMA рахуються фільтром за тегом.

**Загальні правила для всіх джерел**

1. Кожен запуск запиту фіксується в **журналі пошуку** (розд. 4.4): дата, база, ID запиту, точний рядок, обмеження, N знайдених, N експортованих, ім'я файлу.
2. Ім'я RIS-файлу: `<DB>_<QueryID>_<YYYY-MM-DD>[_<роки>].ris`, напр. `Scopus_Q1_2026-10-05.ris`, `GS_G02_2026-10-07_2019-2021.ris`. Файли зберігаються в репозиторії у `search/raw/` (RIS текст, добре діфиться).
3. Дата останнього запуску це search date у статті. Якщо між search date і поданням статті > 6 місяців, пошук повторюється (update search) і різниця обліковується окремо.
4. Ніяких ручних дочищень результатів до імпорту в Zotero: усе, що повернула база, імпортується як є. Дедуплікація в Zotero (розд. 8).

### 4.2. Scopus (виконує ментор)

**Синтаксис, що використовується.** `TITLE-ABS-KEY()` — пошук у назві, анотації, ключових словах. Подвійні лапки `" "` — *loose phrase* (слова поруч у заданому порядку, пунктуація ігнорується, wildcards дозволені). `*` — будь-яка кількість символів. `PUBYEAR > 2013 AND PUBYEAR < 2027` = 2014–2026 включно. Жодних `LIMIT-TO` у базовому рядку: мова та тип документа — критерії відбору (IC/EC), а не пошуку, щоб число на етапі *Identification* у PRISMA-діаграмі було «сирим».

**Спільні блоки** (для читабельності; у Scopus вставляється вже зібраний рядок нижче):

```
[P_iOS]  ( "iOS" OR "iPhone" OR "iPad" OR "SwiftUI" OR "UIKit" OR "Swift language" OR "Swift programming" OR "Apple Swift" )

[I_named]  ( "MVC" OR "Model-View-Controller" OR "Model View Controller" OR "MVP" OR "Model-View-Presenter" OR "MVVM" OR "Model-View-ViewModel" OR "MVVM-C" OR "VIPER" OR "View-Interactor-Presenter-Entity-Router" OR "Clean Architecture" OR "Clean Swift" OR "Onion Architecture" OR "Hexagonal Architecture" OR "Ports and Adapters" OR "Composable Architecture" OR "unidirectional data flow" OR "Redux" OR "ReSwift" OR "Flux pattern" OR "Flux architecture" OR "Elm Architecture" OR "Model-View-Update" OR "MVU" OR "MVI" OR "Model-View-Intent" OR "Coordinator pattern" )

[I_generic]  ( "software architecture" OR "application architecture" OR "app architecture" OR "mobile architecture" OR "architectur* pattern*" OR "architectural style*" OR "architectural design" OR "presentation layer" OR "UI architecture" OR "design pattern*" OR "state management" )

[P_mobile]  ( "mobile app*" OR "mobile application*" OR "smartphone app*" OR "mobile software" OR "mobile development" )

[C_eval]  ( compar* OR evaluat* OR empirical OR "case study" OR experiment* OR maintainab* OR testab* OR "code quality" OR "quality attribute*" )

[NOT_homonyms]  AND NOT TITLE-ABS-KEY ( "intraoral" OR "Cisco" OR "gamma-ray" )

[YEARS]  AND PUBYEAR > 2013 AND PUBYEAR < 2027
```

#### Q1 — iOS × названі патерни (precision-ядро)

*Мета:* усі роботи, де iOS-платформа і хоча б один патерн з нашого списку названі явно. Це основне джерело для RQ1/RQ3.

```
TITLE-ABS-KEY ( ( "iOS" OR "iPhone" OR "iPad" OR "SwiftUI" OR "UIKit" OR "Swift language" OR "Swift programming" OR "Apple Swift" ) AND ( "MVC" OR "Model-View-Controller" OR "Model View Controller" OR "MVP" OR "Model-View-Presenter" OR "MVVM" OR "Model-View-ViewModel" OR "MVVM-C" OR "VIPER" OR "View-Interactor-Presenter-Entity-Router" OR "Clean Architecture" OR "Clean Swift" OR "Onion Architecture" OR "Hexagonal Architecture" OR "Ports and Adapters" OR "Composable Architecture" OR "unidirectional data flow" OR "Redux" OR "ReSwift" OR "Flux pattern" OR "Flux architecture" OR "Elm Architecture" OR "Model-View-Update" OR "MVU" OR "MVI" OR "Model-View-Intent" OR "Coordinator pattern" ) ) AND NOT TITLE-ABS-KEY ( "intraoral" OR "Cisco" OR "gamma-ray" ) AND PUBYEAR > 2013 AND PUBYEAR < 2027
```

#### Q2 — iOS × родові архітектурні терміни

*Мета:* роботи про архітектуру iOS-застосунків, де патерн описано словами (напр. layered presentation architecture) або запропоновано власний патерн без відомої назви. Також знаходить огляди/навчальні роботи, які згадують кілька патернів лише в повному тексті.

```
TITLE-ABS-KEY ( ( "iOS" OR "iPhone" OR "iPad" OR "SwiftUI" OR "UIKit" OR "Swift language" OR "Swift programming" OR "Apple Swift" ) AND ( "software architecture" OR "application architecture" OR "app architecture" OR "mobile architecture" OR "architectur* pattern*" OR "architectural style*" OR "architectural design" OR "presentation layer" OR "UI architecture" OR "design pattern*" OR "state management" ) ) AND NOT TITLE-ABS-KEY ( "intraoral" OR "Cisco" OR "gamma-ray" ) AND PUBYEAR > 2013 AND PUBYEAR < 2027
```

#### Q3 — мобільні застосунки загалом × названі патерни × оцінювання (крос-платформні порівняння)

*Мета:* порівняльні/емпіричні роботи, де в назві-анотації сказано "mobile application", а iOS/Swift фігурує лише в тексті (напр. порівняння MVVM на Android та iOS). Без цього запиту такі роботи не будуть знайдені.

```
TITLE-ABS-KEY ( ( "mobile app*" OR "mobile application*" OR "smartphone app*" OR "mobile software" OR "mobile development" ) AND ( "MVC" OR "Model-View-Controller" OR "Model View Controller" OR "MVP" OR "Model-View-Presenter" OR "MVVM" OR "Model-View-ViewModel" OR "MVVM-C" OR "VIPER" OR "View-Interactor-Presenter-Entity-Router" OR "Clean Architecture" OR "Clean Swift" OR "Onion Architecture" OR "Hexagonal Architecture" OR "Ports and Adapters" OR "Composable Architecture" OR "unidirectional data flow" OR "Redux" OR "ReSwift" OR "Flux pattern" OR "Flux architecture" OR "Elm Architecture" OR "Model-View-Update" OR "MVU" OR "MVI" OR "Model-View-Intent" OR "Coordinator pattern" ) AND ( compar* OR evaluat* OR empirical OR "case study" OR experiment* OR maintainab* OR testab* OR "code quality" OR "quality attribute*" ) ) AND PUBYEAR > 2013 AND PUBYEAR < 2027
```

**Порядок виконання у Scopus (для кожного з Q1–Q3):**

1. Scopus → *Documents* → *Advanced document search* → вставити рядок цілком → *Search*.
2. Записати в журнал (4.4): дата, `N_found`.
3. Один раз для Q1 і Q2 додатково запустити рядок **без** блоку `AND NOT …` і записати різницю.
4. *Select all* → *Export* → **RIS** → відмітити всі групи полів (Citation information, Bibliographical information, Abstract & keywords, Funding details, Other information).
5. Зберегти як `search/raw/Scopus_Qn_<дата>.ris`, закомітити.
6. Імпортувати у Zotero → колекція `01_Scopus/Qn`. Записати `N_exported` (кількість записів у RIS) і `N_imported` (кількість у колекції); обидва мають дорівнювати `N_found`; якщо ні — записати причину в «Примітку».

### 4.3. Google Scholar через Publish or Perish (виконує студент)

#### 4.3.1. Що треба знати про Google Scholar, перш ніж щось запускати

- **GS шукає у повному тексті.** Запит `"iOS" "MVVM"` поверне десятки тисяч записів, бо знайде будь-яку статтю, де обидва слова трапляються де завгодно (у списку літератури також). Тому **кожен наш запит має якір у назві** — слово/фраза в полі *Title words* (в самому GS це оператор `intitle:`).
- **GS показує максимум 1000 результатів** на запит, навіть якщо знайдено більше. Publish or Perish (PoP) теж не може отримати більше.
- **Синтаксис, який працює у Google Scholar:** `"точна фраза"`, `OR` (великими літерами), `intitle:слово`, `-слово` (виключення). **Не працює:** `*`, `AND` (і так мається на увазі), дужки для групування, `TITLE-ABS-KEY`, пошук лише в анотації.
- **Publish or Perish не пропускає `intitle:`.** PoP збирає запит через параметри розширеного пошуку GS і екранує вміст поля *Keywords*: `intitle:iOS` там дає 0 результатів, `intitle: iOS` (з пробілом) — ігнорує оператор. Обмеження «в назві» в PoP задається окремим полем **Title words**. Тому кожен запит нижче записано у **два поля**: *Title words* (те, що має бути в назві) і *Keywords* (те, що будь-де в тексті). `OR` і лапки працюють в обох полях.
- **Чому заборонено `-Android`, `-Flutter`, `-Objective-C`:** GS індексує повний текст, і майже кожна стаття про Swift/iOS хоч раз згадує Android або Objective-C (у вступі, у порівнянні). Такі оператори викидають релевантні роботи. Фільтрація платформи і мови лише на скринінгу (EC3).
- **Пріоритет операторів:** `OR` з'єднує лише **сусідні** терміни. Запит з Keywords `MVVM OR "Model-View-ViewModel"` при Title words `iOS` GS читає як `iOS-у-назві AND (MVVM OR "Model-View-ViewModel")`. Тобто: усе, що не з'єднане `OR`, це `AND`.
- **Регістр не важливий**: `iOS` = `ios` = `IOS`.

#### 4.3.2. Перелік запитів

Усі запити виконуються в PoP з такими параметрами: *Source: Google Scholar*; *Years: 2014 – 2026*; *Maximum number of results: 1000*; *Include:* CITATION records ✔, Patents ✘, Only reviews ✘. Поля Authors / Publication name / ISSN — порожні. Запит вводиться у **два поля**: **Title words** і **Keywords** (див. 4.3.1); порожнє поле лишається порожнім.

**A — платформа в назві, патерн будь-де** (найточніші запити)

| ID | Title words | Keywords | Що ловить | Issue |
|---|---|---|---|---|
| G01 | `iOS` | `MVC OR "Model-View-Controller"` | iOS у назві; MVC у тексті | #17 |
| G02 | `iOS` | `MVVM OR "Model-View-ViewModel"` | | #18 |
| G03 | `iOS` | `MVP OR "Model-View-Presenter"` | *MVP* тут безпечний, бо iOS у назві | #19 |
| G04 | `iOS` | `VIPER` | | #19 |
| G05 | `iOS` | `"clean architecture" OR "clean swift" OR "hexagonal architecture" OR "onion architecture"` | | #20 |
| G06 | `iOS` | `"composable architecture" OR "unidirectional data flow" OR Redux OR Flux OR "Elm architecture" OR MVI OR MVU` | | #21 |
| G07 | `iOS architecture` | *(порожньо)* | Обидва слова в назві — ловить роботи без названого патерну | #22 |
| G08 | `SwiftUI` | *(порожньо)* | Уся література про SwiftUI (її мало); архітектурні роботи відсіємо на скринінгу | #22 |
| G09 | `Swift architecture` | *(порожньо)* | Swift + архітектура в назві | #22 |

**B — патерн у назві, платформа/мова будь-де** (ловить роботи типу «Evaluating MVVM for mobile apps», де iOS/Swift лише в тексті)

| ID | Title words | Keywords | Примітка | Issue |
|---|---|---|---|---|
| G10 | `MVC` | `iOS OR iPhone OR Swift` | Буде шум від web-MVC (ASP.NET/Spring), що згадують iOS — це нормально, відсіюється за назвою | #17 |
| G11 | `"Model-View-Controller"` | `iOS OR iPhone OR Swift` | | #17 |
| G12 | `MVVM` | `iOS OR iPhone OR Swift` | | #18 |
| G13 | `"Model-View-ViewModel"` | `iOS OR iPhone OR Swift` | | #18 |
| G14 | `"Model-View-Presenter"` | `iOS OR iPhone OR Swift` | Голе `MVP` у назві **не** використовуємо (minimum viable product) | #19 |
| G15 | `VIPER` | `iOS OR iPhone` | Без `Swift` (прикметник *swift* у статтях про змій) | #19 |
| G16 | `"clean architecture"` | `iOS OR iPhone OR Swift` | | #20 |
| G17 | `"composable architecture"` | *(порожньо)* | Уся література про TCA — її мало, беремо все | #21 |
| G18 | `"unidirectional data flow"` | *(порожньо)* | Те саме | #21 |
| G19 | `Redux` | `iOS OR iPhone OR Swift` | Шум від React/JS — нормально | #21 |
| G20 | `"Elm architecture" OR "Model-View-Update" OR "Model-View-Intent"` | *(порожньо)* | Якщо PoP повертає 0 — запустити три фрази окремо (G20a/b/c) | #21 |

**C — порівняльні/оглядові роботи без прив'язки до одного патерну**

| ID | Title words | Keywords | Примітка | Issue |
|---|---|---|---|---|
| G21 | `architecture mobile` | `MVC OR MVVM OR MVP OR VIPER OR "clean architecture"` | «архітектура» і «mobile» в назві, будь-який патерн у тексті | #22 |
| G22 | `comparison OR comparative` | `MVC OR MVVM OR MVP OR VIPER iOS` | Порівняння патернів, де iOS у тексті | #22 |
| G23 | `"architectural patterns" OR "architecture patterns"` | `iOS OR iPhone OR Swift` | | #22 |

**Контрольна перевірка (один раз, на G01, до експорту).** PoP може обмежувати назвою або лише *Title words* (потрібний нам режим), або обидва поля разом. Відкрити 10 перших результатів G01: якщо є роботи, де «iOS» у назві, а «MVC» лише в тексті — усе гаразд. Якщо в усіх результатах обидва слова в назві — PoP обмежив назвою все; тоді для тирів A і B у *Title words* лишається лише якір (`iOS` / назва патерну), *Keywords* — порожньо, набір ділиться за роками (4.3.3), а патерн відсіюється на скринінгу. Результат перевірки записується тут одним реченням: *«PoP (версія …): режим … »*.

#### 4.3.3. Що робити, якщо запит повертає ≥ 980 результатів

GS «обрізає» видачу на 1000. Щоб не втратити записи, **той самий рядок** запускається кілька разів із різними діапазонами років у полі *Years*:

| Запуск | Years |
|---|---|
| a | 2014 – 2017 |
| b | 2018 – 2020 |
| c | 2021 – 2023 |
| d | 2024 – 2026 |

Якщо і піддіапазон дає ≥ 980 — ділити його далі по одному року. Кожен запуск — окремий рядок у журналі та окремий RIS-файл (`GS_G12_<дата>_2021-2023.ris`). Дублікатів між піддіапазонами майже не буде; ті, що є, зніме Zotero.

**Не робити:** звужувати рядок додатковими словами «щоб стало менше». Це змінює протокол і не відтворюється. Єдиний дозволений спосіб зменшити видачу — поділ за роками.

#### 4.3.4. Порядок виконання одного запиту (чек-лист для студента)

1. Відкрити PoP → *New Google Scholar search*.
2. Заповнити *Title words* і *Keywords* за таблицею 4.3.2; *Years* 2014–2026; *Max results* 1000; прапорці як у 4.3.2.
3. *Search*. Дочекатися, поки лічильник зупиниться.
4. Записати в журнал `N_found` (число, яке PoP показує як «Results»/«Papers»); у колонку «Обмеження» — роки та `PoP: Title words + Keywords`.
5. Якщо `N_found ≥ 980` → виконати 4.3.3 замість кроків 6–8.
6. *File → Save results as… → RIS* → `search/raw/GS_Gnn_<дата>.ris`. Записати `N_exported` (кількість записів у файлі; PoP показує її при збереженні).
7. Імпорт у Zotero → колекція `02_GoogleScholar/Gnn`. Записати `N_imported` (кількість записів у колекції після імпорту; у нормі = `N_exported`; різницю — в «Примітку»).
8. Контрольна перевірка режиму PoP — один раз, для G01 (див. кінець 4.3.2).
9. Закомітити RIS і оновлений журнал.

### 4.4. Журнал пошуку (search log)

Заповнюється по мірі виконання. Це — таблиця для PRISMA-діаграми (блок *Identification*) і для Methods у статті.

| Дата | База | ID | Обмеження (роки / інше) | N_found | N_exported | N_imported | Файл | Хто | Примітка |
|---|---|---|---|---|---|---|---|---|---|
| | Scopus | Q1 | 2014–2026; NOT-блок | | | | | Ментор | |
| | Scopus | Q1 | 2014–2026; **без** NOT-блоку (контроль) | | — | — | — | Ментор | не експортується |
| | Scopus | Q2 | 2014–2026; NOT-блок | | | | | Ментор | |
| | Scopus | Q2 | 2014–2026; без NOT-блоку (контроль) | | — | — | — | Ментор | |
| | Scopus | Q3 | 2014–2026 | | | | | Ментор | |
| | GS/PoP | G01 | 2014–2026; PoP: Title words + Keywords | | | | | Студент | |
| | GS/PoP | G02 | | | | | | Студент | |
| | … | … | | | | | | | |
| | GS/PoP | G23 | | | | | | Студент | |

Підсумки для PRISMA: `N_Scopus = ΣQ1..Q3`, `N_GS = ΣG01..G23`, `N_identified = N_Scopus + N_GS` (до дедуплікації). Після дедуплікації в Zotero `N_after_dedup` (розд. 8).

---

## 5. Inclusion criteria

Публікація **включається**, якщо задовольняє **всі** IC1–IC7. Формулювання англійською; "Як перевіряти" інструкція для скринінгу.

| ID | Criterion (EN) | Як перевіряти (UA) |
|---|---|---|
| **IC1** | The study describes, proposes, applies, evaluates, or compares at least one application-level software architecture pattern (Section 2, Intervention) **for an iOS application implemented in Swift**. iOS/Swift must be a subject of the study, not a passing mention. Studies that do not state the implementation language are included if the application is a native iOS app and nothing indicates an Objective-C-only implementation. | Об'єкт дослідження iOS-застосунок на Swift: є хоча б одна Swift-реалізація, або результати наведені окремо для iOS/Swift, або патерн обговорюється саме в iOS/Swift-контексті. Згадка iOS/Swift лише у вступі/related work → **не** проходить (→ EC3). **Мова не вказана** (часто в анотації): на етапі title/abstract — включити; на етапі full text шукати маркери (Swift, SwiftUI, UIKit-код, Xcode-проєкт, `.swift`, `@objc`, `.m/.h`-файли). Явно лише Objective-C → EC3. Не визначається навіть з повного тексту, але це нативний iOS-застосунок 2014+ → включити і записати в екстракції `language: not reported`. Список патернів відкритий: якщо патерн новий, але це архітектура рівня застосунку — проходить, патерн додається в розд. 2 окремим комітом. |
| **IC2** | The publication is peer-reviewed: a journal article, a conference or workshop paper, or a peer-reviewed book chapter. | Перевірити за сайтом видання/конференції. Springer LNCS/CCIS, IEEE/ACM proceedings рецензовані. Препринт (arXiv) лише якщо знайдено опубліковану версію (тоді включаємо **її**). |
| **IC3** | The study is a primary study of at least one of the following types: (a) empirical study (controlled/quasi-experiment, case study, survey/interview study, repository mining); (b) analytical/structured comparison of patterns; (c) proposal of a pattern or architecture with at least an illustrative evaluation; (d) experience report from practice. | Тип фіксується в екстракції (RQ2). Роботи, де патерн лише згадано як фон іншої теми (напр. стаття про ML-модель у iOS-застосунку) — **не** проходять (→ EC9). |
| **IC4** | Written in English or Ukrainian. | Інша мова → EC10. |
| **IC5** | Published (or first available online) between **2014** and the search date (2026). | 2014 — рік появи Swift (розд. 7). Рік за метаданими бази; для «early access» — рік першої онлайн-публікації. |
| **IC6** | Full text is accessible to the team (open access, institutional access, author's copy on ResearchGate/personal page, or obtained by a request to the authors within 14 days). | Запит авторам надсилається один раз; якщо через 14 днів тексту немає → EC7. Ментор має підтвердити, що повної версії дійсно немає в доступі. |
| **IC7** | The publication is a full paper with substantive content (**≥ 4 pages** in the venue's format). | Short/position papers, posters, extended abstracts, doctoral-symposium papers → EC5. |

---

## 6. Exclusion criteria

Публікація **виключається**, якщо задовольняє **хоча б один** EC. Критерії застосовуються **в порядку EC1 → EC10**, і для кожного виключеного запису фіксується **перша** спрацьована причина — тегом `EC1`…`EC10` у Zotero (так рахуються причини виключення для PRISMA-діаграми). Включені записи отримують тег `included`.

| ID | Criterion (EN) | Пояснення / приклади (UA) |
|---|---|---|
| **EC1** | Theses and dissertations (bachelor's, master's, PhD) and other academic works without independent peer review. | Багато робіт про iOS-архітектури це бакалаврські/магістерські роботи (Theseus.fi, DiVA тощо). Вони **не** включаються, але позначаються тегом `grey-thesis` у Zotero: їх кількість буде згадана в Discussion як ознака практичного інтересу, і вони можуть стати джерелом для snowballing. |
| **EC2** | Non-scientific sources: blog posts, tutorials, vendor documentation, books without peer review, slides, webinars, podcasts, patents, standards. | Medium/Habr/Hacking with Swift тощо. Книги (Apress, O'Reilly) виключаються, але корисні для Introduction. |
| **EC3** | Studies that address only Android, only cross-platform frameworks (Flutter, React Native, Xamarin, Kotlin Multiplatform, Ionic, .NET MAUI), or iOS applications implemented **exclusively in Objective-C**; or studies that mention iOS/Swift only in passing (introduction, related work, a single sentence). | Порівняння Android **та** iOS (Swift) з окремими результатами для iOS — **включається**. Порівняння Objective-C **та** Swift — включається (Swift-частина є об'єктом). Роботи лише про Objective-C → виключаються. |
| **EC4** | Studies in which the iOS application is not the object of study (e.g., it is only a client of a proposed IoT/backend/cloud system, or a vehicle for another topic such as ML, security, UX), and the application's architecture pattern is not analysed. | Приклад: «система моніторингу IoT з мобільним клієнтом на iOS (MVVM)» без аналізу самого MVVM. |
| **EC5** | Short papers (< 4 pages), position papers, posters, extended abstracts, doctoral-symposium papers, editorials, keynotes. | Див. IC7. Сторінки — за форматом видання. |
| **EC6** | Duplicate or redundant publications of the same study (e.g., a conference paper later extended into a journal article). | Залишається **найповніша** версія (зазвичай журнальна); решта позначаються `duplicate-of:<key>`. Це не те саме, що дедуплікація записів (одна й та сама стаття з двох баз). |
| **EC7** | Full text not available after all steps in IC6. | Фіксується як «not retrieved» у PRISMA-діаграмі (окремий блок *Reports not retrieved*). |
| **EC8** | Secondary and tertiary studies (systematic literature reviews, mapping studies, narrative literature surveys, meta-analyses). | Не включаються до синтезу (щоб не рахувати первинні дані двічі), але **обов'язково** зберігаються в колекції `06_Snowballing/secondary` і використовуються для backward snowballing та в Related Work. |
| **EC9** | Out of scope: the architecture discussed is not at the application/presentation level (e.g., backend microservices, network architecture, hardware/system architecture, Cisco IOS, intraoral scanners, the Swift observatory, SWIFT banking), or the paper concerns only GoF design patterns / code idioms without an application-level architecture pattern. | Омоніми iOS/Swift і роботи, де «architecture» означає інше. |
| **EC10** | Language other than English or Ukrainian. | |

**Правила скринінгу за критеріями (короткий витяг; повна процедура — розд. 8):**
- На етапі *title/abstract* застосовуються EC1, EC2, EC3 (лише платформа: Android-only / крос-платформа; Objective-C-only на цьому етапі **не** відсіюється, бо мова рідко видна з анотації), EC5, EC8, EC9, EC10 і IC1 (наскільки видно з анотації). Сумнів → **включити**.
- На етапі *full text* застосовуються всі IC/EC, включно з перевіркою мови реалізації (IC1/EC3); тут ухвалюється остаточне рішення і фіксується одна причина.

---

## 7. Time range and language

| Параметр | Значення | Обґрунтування |
|---|---|---|
| Початок діапазону | **1 січня 2014** | Swift представлено на WWDC у червні 2014, тож раніший початок не має сенсу для огляду про Swift. |
| Кінець діапазону | **дата пошуку** (жовтень 2026, за журналом 4.4) | У Scopus: `PUBYEAR < 2027`; у PoP: Years до 2026. Записи 2027 року (early access) виключаються. |
| Оновлення пошуку | Якщо від search date до подання статті минає > 6 місяців — повторний запуск усіх рядків з фільтром «з search date» і окремий облік | Вимога PRISMA 2020, item 6 |
| Мови публікацій | **English, Ukrainian** | Англійська — мова публікацій у галузі; українська — доступна команді без перекладу. Інші мови → EC10; їх кількість обліковується (очікувано < 2 %). |
| Реалізація в рядках | Scopus: лише `PUBYEAR`; мова публікації **не** обмежується в запиті. GS/PoP: поле Years 2014–2026; мова не обмежується | Мова публікації застосовується як критерій на скринінгу, щоб число *Identification* було «сирим» |

---

## 8. Screening procedure

*(заготовка)*

## 9. Quality assessment checklist

*(заготовка)*

## 10. Data extraction form

*(заготовка)*

## 11. Synthesis approach

*(заготовка)*

---