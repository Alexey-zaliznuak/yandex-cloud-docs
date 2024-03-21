#### Что такое {{ mrd-short-name }}? {#what-is}

{{ mrd-short-name }} — это сервис, который помогает вам создавать, эксплуатировать и масштабировать базы данных {{ RD }} в облачной инфраструктуре.

С {{ mrd-short-name }} вы можете:
- создавать базы данных с необходимыми параметрами производительности;
- масштабировать вычислительные мощности и выделенный размер хранилища для баз данных по мере необходимости;
- получать журналы работы баз данных.

{{ mrd-short-name }} берет на себя трудоемкие задачи администрирования инфраструктуры {{ RD }}:
- предоставляет мониторинг потребляемых ресурсов;
- автоматически создает резервные копии баз данных;
- обеспечивает отказоустойчивость за счет автоматического переключения на резервные реплики;
- своевременно обновляет программное обеспечение СУБД.

Вы взаимодействуете с кластером БД в {{ mrd-short-name }} как с обычной базой данных в вашей локальной инфраструктуре. Благодаря этому вы можете управлять внутренними настройками БД в соответствии с требованиями вашего приложения.


#### Какую часть работы по управлению и сопровождению баз данных берет на себя {{ mrd-short-name }}? {#services}

При создании кластеров {{ mrd-short-name }} выделяет ресурсы, устанавливает СУБД и создает базы данных.

Для созданных и запущенных баз данных {{ mrd-short-name }} автоматически создает резервные копии, а также устанавливает исправления и обновления СУБД.

Также {{ mrd-short-name }} обеспечивает репликацию данных между хостами БД (как внутри, так и между зонами доступности) и автоматически переключает нагрузку на резервную реплику в случае аварии.

#### Для каких задач стоит использовать {{ mrd-short-name }}, а для каких — виртуальные машины с базами данных? {#mdb-advantage}

{{ yandex-cloud }} предлагает два варианта работы с базами данных:

- {{ mrd-short-name }} позволяет вам эксплуатировать шаблонные базы данных, не заботясь об администрировании.
- Виртуальные машины {{ compute-full-name }} позволяют вам создавать и настраивать собственные базы данных. Такой подход позволяет использовать любые СУБД, подключаться к базам данных по [SSH](../../glossary/ssh-keygen.md) и так далее.


#### Что такое хост базы данных и кластер базы данных? {#what-is-cluster}

_Хост БД_ — это изолированная среда базы данных в облачной инфраструктуре с выделенными вычислительными ресурсами и зарезервированным размером хранилища данных.

_Кластер БД_ — это один или более хостов БД, между которыми можно настроить репликацию.


#### Как начать работу с {{ mrd-short-name }}? {#quickstart}

{{ mrd-short-name }} доступен всем зарегистрированным пользователям {{ yandex-cloud }}.

Чтобы создать кластер базы данных в {{ mrd-short-name }}, необходимо определиться с его характеристиками:

- [Класс хостов](../../managed-redis/concepts/instance-types.md) (характеристики производительности — процессоры, память и т. п.).
- [Тип диска](../../managed-redis/concepts/storage.md) и его размер (резервируется в полном объеме при создании кластера).
- Сеть, к которой будет подключен ваш кластер.
- Количество хостов для кластера и зона доступности для каждого хоста вы можете выбрать зону доступности.

Подробные инструкции см. в разделе [{#T}](../../managed-redis/quickstart.md).

#### Сколько хостов БД может содержать кластер? {#how-many-hosts}

Минимальное количество хостов в кластере зависит от:
* выбранных [платформы и класса хостов](../../managed-redis/concepts/instance-types.md);
* выбранного [типа диска](../../managed-redis/concepts/storage.md);
* включенного или выключенного при [создании](../../managed-redis/operations/cluster-create.md) кластера [шардирования](../../managed-redis/concepts/sharding.md).

Максимальное количество хостов в кластере ограничено только запрошенными вычислительными ресурсами и размером хранилища для кластера.

Подробнее см. в разделе [{#T}](../../managed-redis/concepts/limits.md).

#### Как получить доступ к запущенному хосту базы данных? {#db-access}

Вы можете подключаться к базам данных {{ mrd-short-name }} способами, стандартными для СУБД, с одним ограничением: хосты {{ mrd-short-name }} доступны только с виртуальных машин {{ yandex-cloud }}, подключенных к той же сети.


#### Сколько кластеров можно создать в рамках одного облака? {#db-limit}

Технические и организационные ограничения MDB приведены в разделе [{#T}](../../managed-redis/concepts/limits.md).


#### Как происходит обслуживание кластеров БД? {#service-window}

Под обслуживанием в {{ mrd-short-name }} понимается:

- автоматическая установка обновлений и исправлений СУБД для хостов БД (в т. ч. для выключенных кластеров);
- изменение класса хостов и размера хранилища;
- другие сервисные работы {{ mrd-short-name }}.

Подробнее в разделе [{#T}](../../managed-redis/concepts/maintenance.md).

#### Какую версию {{ RD }} использует {{ mrd-short-name }}? {#dbms-version}

{{ mrd-short-name }} поддерживает {{ RD }} версии {{ versions.console.str }}.


#### Что происходит, когда выпускается новая версия СУБД? {#new-version}

Программное обеспечение баз данных обновляется при выходе новых минорных версий. Владельцы затронутых кластеров БД получают предварительное оповещение о сроках проведения работ и доступности баз данных.


#### Что происходит, когда версия СУБД становится неподдерживаемой (deprecated)? {#dbms-deprecated}

Через месяц после того, как версия СУБД становится неподдерживаемой, {{ mrd-short-name }} автоматически оповещает владельцев кластеров БД, созданных с этой версией, по электронной почте.

Создание новых хостов с СУБД неподдерживаемых версий становится невозможным. Через 7 дней после оповещения для минорных версий и через 1 месяц для мажорных версий проводится автоматическое обновление кластеров БД до следующей поддерживаемой версии. Обновление неподдерживаемых мажорных версий происходит даже если у вас отключено автоматическое обновление.


#### Как рассчитывается стоимость потребления для хоста базы данных? {#db-cost}

В {{ mrd-short-name }} стоимость потребления рассчитывается исходя из следующих параметров:

- Выбранный класс хостов.
- Размер хранилища, зарезервированного для хоста БД.
- Объем резервных копий кластера БД. Объем резервных копий, равный объему хранилища, не тарифицируется. Хранение резервных копий сверх этого объема оплачивается по [тарифам](../../managed-redis/pricing.md).
- Количество часов работы хоста БД. Неполные часы округляются до целого значения. Стоимость часа работы для каждого класса хостов приведена в разделе [{#T}](../../managed-redis/pricing.md).

#### Как изменить вычислительные ресурсы и размер хранилища для кластера БД? {#resources-change}

Вы можете изменять вычислительные ресурсы и размер хранилища в консоли управления — просто выберите другой класс хостов для нужного кластера.

Характеристики кластера изменяются в течение 30 минут. В этот период также могут быть включены другие сервисные работы по кластеру, например, установка обновлений.


#### Включено ли резервное копирование хостов БД по умолчанию? {#default-backup}

Да, по умолчанию резервное копирование включено. Для {{ RD }} выполняется полное резервное копирование один раз в сутки, и сохраняются все журналы транзакций кластера БД. Это позволяет восстановить состояние кластера на любой момент времени в пределах периода хранения резервных копий, за исключением последних 30 секунд.

По умолчанию резервные копии хранятся 7 дней.

#### Когда выполняется резервное копирование? Доступен ли кластер БД во время резервного копирования? {#backup-window}

Окно резервного копирования — это интервал времени, в течение которого выполняется ежедневное полное резервное копирование кластера БД. Окно резервного копирования — 01:00−05:00 по московскому времени.

Во время окна резервного копирования кластеры остаются полностью доступными.

#### За какими метриками и процессами можно следить с помощью мониторинга? {#monitoring}

Для всех типов СУБД можно отслеживать:

- загрузку процессора, памяти, сети, дисков в абсолютных величинах;
- загрузку памяти, сети, дисков в процентах от установленных лимитов для класса хостов соответствующего кластера;
- объем данных кластера БД и остаток свободного места в хранилище данных.

Для всех хостов БД можно отслеживать метрики, специфические для типа соответствующей СУБД. Например для {{ RD }} можно отслеживать:
- среднее время выполнения запроса;
- количество запросов в секунду;
- количество ошибок в журналах и т. д.

Мониторинг можно осуществлять с минимальной гранулярностью в 5 секунд.

#### Как настроить алерт, который срабатывает при заполнении определенного процента дискового пространства? {#disk-space-percentage}

[Создайте алерт](../../managed-redis/operations/monitoring.md#monitoring-integration) с метрикой `disk.used_bytes` в сервисе {{ monitoring-full-name }}. Метрика показывает размер использованного дискового пространства в кластере {{ mrd-name }}.

Для `disk.used_bytes` используются пороги для оповещения. Их рекомендуемые значения:

* `Alarm` — 90% дискового пространства.
* `Warning` — 80% дискового пространства.

Значения порогов задаются только в байтах. Например, рекомендуемые значения для диска размером в 100 ГБ:

* `Alarm` — `96636764160` байтов (90%).
* `Warning` — `85899345920` байтов (80%).


{% include [fz-152.md](../fz-152.md) %}


{% include [logs](../logs.md) %}

{% include [log-duration](../../_includes/mdb/log-duration-qa.md) %}

#### Почему кластер работает медленно, хотя вычислительные ресурсы использованы не до предела? {#throttling}

Вероятно, максимальные значения [IOPS и пропускной способности (bandwidth)](../../compute/concepts/storage-read-write.md) хранилища недостаточны для обработки текущего количества запросов. В этом случае срабатывает [троттлинг](../../compute/concepts/storage-read-write.md#throttling) и быстродействие всего кластера падает.

Максимальные IOPS и bandwidth прирастают на фиксированную величину при увеличении размера хранилища на определенный шаг. Шаг и прирост зависят от типа дисков:

| Тип дисков                  | Шаг, ГБ | Прирост макс. IOPS (чтение/запись) | Прирост макс. bandwidth (чтение/запись), МБ/с |
|-----------------------------|---------|------------------------------------|-----------------------------------------------|
| `network-ssd`               | 32      | 1000/1000                          | 15/15                                         |
| `network-ssd-nonreplicated` | 93      | 28000/5600                         | 110/82                                        |

Чтобы увеличить максимальные значения IOPS и bandwidth и снизить вероятность троттлинга, расширьте размер хранилища при [изменении кластера](../../managed-redis/operations/update.md#change-disk-size).

Рассмотрите возможность перехода на более быстрый тип дисков путем [восстановления кластера](../../managed-redis/operations/cluster-backups.md#restore) из резервной копии.