`Open Web Application Security Project® (OWASP)`– открытый проект по обеспечению безопасности приложений

OWASP Top 10 – это отчет или информационный документ, в котором перечислены основные проблемы, связанные с безопасностью
веб-приложений. Он регулярно обновляется, чтобы постоянно отображать 10 наиболее серьезных рисков, с которыми
сталкиваются организации. OWASP рекомендует всем компаниям учитывать выводы документа при построении корпоративных
процессов, чтобы минимизировать и смягчить актуальные риски безопасности.

В последнем отчете OWASP перечислены 10 основных уязвимостей:

* Инъекции (**Injections**).
* Нарушенная аутентификация (**Broken Authentication**).
* Раскрытие критически важных данных (**Sensitive Data Exposure**).
* Внешние объекты XML (**XXE**) (**XML External Entities (XXE)**).
* Нарушенный контроль доступа (**Broken Access control**).
* Неправильная конфигурация безопасности (**Security misconfigurations**).
* Межсайтовый скриптинг (**XSS**) (**Cross Site Scripting (XSS)**).
* Небезопасная десериализация (**Insecure Deserialization**).
* Использование компонентов с известными уязвимостями (**Using Components with known vulnerabilities**).
* Недостаточно подробные журналы и слабый мониторинг (**Insufficient logging and monitoring**).

## 1. Инъекции

:::note

Инъекционные атаки происходят, когда ненадежные данные передаются интерпретатору кода через ввод формы или с помощью
другого способа отправки информации в веб-приложение. Например, злоумышленник может ввести код на SQL в форму, которая
ожидает имени пользователя. Если ввод данных не защищен должным образом, это приведет к выполнению кода – такие атаки
известны как SQL-инъекции.

:::

Инъекционные атаки можно предотвратить путем проверки и/или очистки отправленных пользователем данных. В первом случае
подозрительные данные отклоняются полностью, а во втором производится очистка только их подозрительной части. Кроме
того, администратор базы данных может установить специальные элементы управления, чтобы минимизировать объем информации,
которую может раскрыть атака с использованием SQL-инъекций.

## 2. Нарушенная аутентификация

:::note

Уязвимости аутентификации могут позволить злоумышленникам получить доступ к учетным записям пользователей, включая
привилегированные, которые затем можно использовать для получения контроля над корпоративными информационными системами.

:::

Веб-сайты часто имеют проблемы с механизмами аутентификации. Прежде всего связаны они с некорректным управлением
сеансами, что может быть использовано злоумышленниками для получения доступа к учетным записям пользователей и учетным
данным для входа.

OWASP Top 10 содержит целый список подобных уязвимостей:

* Возможность автоматизированного заполнения учетных данных и/или подбора пароля.
* Возможность использования стандартных, слабых и известных паролей.
* Неэффективные процессы восстановления учетных данных.
* Отсутствие многофакторной аутентификации (MFA) или ее неэффективная реализация.
* Предоставление идентификаторов сеансов в унифицированном указателе ресурсов (URL), отсутствие чередования
  идентификаторов сеансов и неправильное аннулирование идентификаторов сеансов и токенов аутентификации при выходе
  пользователя из системы или после периода бездействия.

:::danger

Такие уязвимости часто возникают из-за недостатка у разработчиков опыта, из-за проблем с тестированием, а также из-за
слишком поспешных выпусков программного обеспечения.

:::

Количество уязвимостей можно уменьшить путем внедрения многофакторной аутентификации, а также внедрения ограничений,
делающих невозможности автоматизированные атаки грубой силы (например, путем перебора). Не менее важно отсутствие спешки
и наличие у разработчиков времени на проверку изменений перед запуском в продакшен, а также внедрение процедур
тестирования кода на безопасность. Также необходимо внедрить жесткую парольную политику и использовать безопасные
диспетчеры сеансов.

## 3. Раскрытие критически важных данных

Основная причина риска раскрытия критически важных данных связана с отсутствием шифрования или с использованием
ненадежных методов генерации и управления ключами, слабых алгоритмов шифрования, ненадежных способов хранения паролей и
т.д. Кроме того, разработчики веб-приложений часто хранят конфиденциальные данные, даже если в этом нет необходимости.

## 4. Внешние объекты XML (XXE)

Атаки XXE нацелены на веб-приложения, которые анализируют расширяемый язык разметки (XML). Они возникают, когда ввод
содержащего ссылку на внешний объект кода XML обрабатывается синтаксическим анализатором со слабой конфигурацией.
Анализаторы XML часто по умолчанию уязвимы для XXE, а значит разработчики должны удалить уязвимость вручную.

:::danger

В Топ-10 OWASP указано, что атаки XXE обычно нацелены на уязвимые процессоры XML, уязвимый код, зависимости и
интеграции.

:::

Атаки XXE можно избежать, если веб-приложения принимают менее сложные формы данных (например, веб-токены JavaScript
Object Notation (JSON)), исправляя синтаксические анализаторы XML или отключая использование внешних сущностей.
Защититься от атак XXE можно, развернув шлюзы безопасности интерфейса прикладного программирования (API), виртуальные
исправления и брандмауэры веб-приложений (WAF).

## 5. Нарушенный контроль доступа

:::note

Проблемы с контролем доступа позволяют злоумышленникам обойти заданные ограничения и получить несанкционированный доступ
к системам и конфиденциальным данным, а также потенциально получить доступ к учетным записям администраторов и
привилегированных пользователей.

:::

Риск нарушения контроля доступа можно снизить, развернув концепцию наименее привилегированного доступа, регулярно
проверяя серверы и веб-сайты, применяя MFA и удаляя с серверов неактивных пользователей и ненужные службы. Можно также
защитить элементы управления доступом, используя токены авторизации при входе пользователей в веб-приложение и делая их
недействительными после выхода из системы. Другие рекомендации включают регистрацию и отчеты об ошибках доступа, а также
использование ограничения скорости для минимизации причиняемого автоматическими атаками ущерба.

## 6. Неправильная конфигурация безопасности

:::note

Ошибки настройки безопасности считаются наиболее распространенной уязвимостью в рейтинге OWASP Top 10. Чаще всего они
связаны с использованием стандартных настроек веб-сайтов или системы управления контентом (CMS). К распространенным
ошибкам конфигурации также относятся неспособность исправить недостатки программного обеспечения, неиспользуемые
веб-страницы, незащищенные каталоги и файлы, разрешения на совместное использование по умолчанию для служб облачного
хранения, а также неиспользуемые или ненужные службы.

:::

Неправильная конфигурация безопасности может быть где угодно: в приложениях и веб-серверах, базах данных, сетевых
службах, пользовательском коде, фреймворках, предустановленных виртуальных машинах и контейнерах.

Конфигурацию безопасности можно исправить, изменив настройки веб-сервера или CMS по умолчанию, удалив неиспользуемые
функции кода и контролируя данные пользователей и видимость пользовательской информации. Разработчики также должны
удалить ненужную документацию, функции, структуры и образцы, сегментировать архитектуру приложений и автоматизировать
проверку эффективности конфигураций и настроек веб-среды.

## 7. Межсайтовый скриптинг (XSS)

:::note

Уязвимости XSS позволяют киберпреступникам внедрять скрипты на веб-сайт и использовать его для распространения
выполняющегося в браузере пользователя вредоносного кода. Как правило это нужно для перехвата пользовательских сеансов,
кражи конфиденциальных данных или перенаправления пользователя на вредоносные сайты.

:::

Предотвратить эксплуатацию уязвимостей XSS можно с помощью брандмауэров веб-приложений (WAF), в то время как
разработчики могут снизить вероятность XSS-атак, отделяя ненадежные данные от активных браузеров. Это включает в себя
использование фреймворков, которые избегают XSS по своей конструкции, использование очистки и проверки данных, избегание
ненадежных данных запроса протокола передачи гипертекста (HTTP) и развертывание политики безопасности контента (CSP).

## 8. Небезопасная десериализация

:::note

В терминах хранения данных и информатики сериализация означает преобразование объектов или структур данных в байтовые
строки. Десериализация означает преобразование этих байтовых строк в объекты. Небезопасная десериализация предполагает,
что злоумышленники изменяют данные до того, как они будут десериализованы.

:::

Рекомендации OWASP по защите в отношении небезопасной десериализации касаются супер-файлов cookie, которые содержат
сериализованную информацию о пользователях. Если злоумышленники могут успешно десериализовать объект, они могут
предоставит себе роль администратора, сериализовать данные и поставить под угрозу все веб-приложения.

:::tip

Этого можно избежать, запретив сериализованные объекты и запретив десериализацию данных, поступающих из ненадежных
источников. OWASP также рекомендует отслеживать деятельность по десериализации, внедрять проверки целостности любых
сериализованных объектов для предотвращения подделки данных, изолировать десериализованный код от сред с низким уровнем
привилегий, обеспечивать регистрацию всех исключений и сбоев десериализации, а также ограничивать и отслеживать сетевое
подключение из контейнеров и серверов, десериализирующих данные.

:::

## 9. Использование компонентов с известными уязвимостями

:::note

Программные компоненты, такие как фреймворки и библиотеки, часто используются в веб-приложениях для обеспечения
определенных функций. Однако эти компоненты могут содержать уязвимости, позволяющие злоумышленнику начать кибератаку.

:::

:::danger

Часто разработчики не обновляют сторонние компоненты, поскольку их устаревший код не работает со свежими версиями ПО, а
веб-мастера либо обеспокоены тем, что обновления нарушают работу сайтов, либо не имеют опыта для применения обновлений.
К тому же злоумышленники постоянно ищут потенциальные уязвимости, которые еще не были обнаружены разработчиками (
известные как уязвимости нулевого дня) и которые они могут использовать.

:::

Этого можно избежать с помощью виртуального исправления, которое защищает устаревшие веб-сайты от эксплуатации
уязвимостей с помощью брандмауэров, систем обнаружения вторжений (IDS) и WAF. Эксплуатацию уязвимостей также можно
предотвратить, сохранив только реально необходимые компоненты и удалив все неиспользуемые или не обслуживаемые. Лучшим
методом будет установка компонентов из надежных источников и постоянное их обновление.

## 10. Недостаточно подробные журналы и слабый мониторинг

Успешную хакерскую атаку или утечку данных удается обнаружить далеко не всегда. Часто злоумышленники не только получают
несанкционированный доступ к информационным системам, но хозяйничают в них месяцами или годами, оставаясь невидимыми.
Чтобы этого не произошло, необходимо регистрировать и отслеживать поведение веб-приложения, чтобы своевременно
распознать подозрительную активность и либо предотвратить атаку, любо минимизировать ее последствия.

:::tip

Необходимо вести журналы аудита, которые позволяют отслеживать любые подозрительные изменения, регистрировать аномальную
активность и отслеживать несанкционированный доступ или, скажем, компрометацию учетной записи.

:::