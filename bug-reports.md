# Bug report — stavkinasport.com

Исполнитель: **Пугин Максим Витальевич**  
Дата: **11 сентября 2026**  
Полный интервал: **10:19:40–15:28:41 МСК (5 часов 9 минут 1 секунда)**  
Активное время выполнения: **1 час 16 минут 33 секунды** (10:19:40–10:30:56 и 14:23:24–15:28:41 МСК; перерыв исключён)

## QA-001 — Поиск не показывает результаты по существующему запросу

- Environment: Chromium, macOS 26.5.2; 1440×900 и 390×844
- Preconditions: на сайте существуют многочисленные материалы со словом «футбол»
- Steps: открыть главную; нажать поиск; ввести `футбол`; нажать Enter
- Actual: открывается `/search/?search=футбол`, но между шапкой и футером нет результатов, сообщения о пустой выдаче или повторного поля поиска
- Expected: показываются релевантные материалы либо понятное сообщение об отсутствии результатов
- Severity: High
- Priority: High
- Evidence: [desktop](evidence/search-desktop.png), [mobile](evidence/search-mobile.png)

## QA-002 — Кнопка «Вход» не открывает форму авторизации

- Environment: Chromium, macOS 26.5.2; 1440×900 и 390×844
- Preconditions: пользователь не авторизован
- Steps: открыть главную или страницу контактов; нажать «Вход»
- Actual: URL и содержимое страницы не меняются; форма/диалог авторизации не появляется
- Expected: открывается форма входа или страница авторизации
- Severity: High
- Priority: High
- Evidence: [desktop](evidence/login-desktop-confirmed.png), [mobile](evidence/login-mobile-confirmed.png)

## QA-003 — Выбранные букмекеры отсутствуют на странице сравнения

- Environment: Chromium, macOS 26.5.2; 1440×900 и 390×844
- Preconditions: открыта страница рейтинга букмекеров
- Steps: добавить одну или несколько карточек кнопкой сравнения; убедиться, что счётчик стал больше нуля; нажать «Сравнить» или «Перейти к сравнению»
- Actual: `/bookmakers-compare/` показывает «Список сравнения пуст»; выбранные карточки потеряны
- Expected: страница показывает выбранные карточки и их характеристики
- Severity: High
- Priority: High
- Evidence: [desktop — выбранные](evidence/compare-desktop-selected-confirmed.png), [desktop — результат](evidence/compare-desktop-result-confirmed.png), [mobile — выбранные](evidence/compare-mobile-selected-final.png), [mobile — результат](evidence/compare-mobile-result-final.png)

## QA-004 — В ленте новостей отображается необработанный shortcode

- Environment: Chromium, macOS 26.5.2; 1440×900 и 390×844
- Steps: открыть `/novosti/`; просмотреть записи между второй и третьей новостями
- Actual: пользователю виден служебный текст `[wp_revive_banner zone_id="news"]`
- Expected: отображается рекламный блок или ничего; служебный shortcode пользователю не виден
- Severity: Medium
- Priority: Medium
- Evidence: [desktop](evidence/news-shortcode-desktop.png), [mobile](evidence/news-shortcode-mobile.png)

## QA-005 — Поля контактной формы не имеют программно связанных подписей

- Environment: Chromium, macOS 26.5.2; 1440×900 и 390×844
- Preconditions: открыта `/kontakty/`
- Steps: нажать видимую подпись «Ваш E-mail»; проверить доступное имя полей имени, email и вопроса
- Actual: нажатие подписи не фокусирует поле; у полей отсутствуют `label`, `aria-label` и `aria-labelledby`
- Expected: каждая видимая подпись связана с соответствующим полем; нажатие переводит фокус, а вспомогательные технологии объявляют название поля
- Severity: Medium
- Priority: Medium
- Evidence: [mobile](evidence/contact-label-mobile.png), [техническая фиксация](evidence/contact-accessibility.txt)
