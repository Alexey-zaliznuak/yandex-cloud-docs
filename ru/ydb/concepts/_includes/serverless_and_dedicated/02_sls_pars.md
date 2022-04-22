---
sourcePath: ru/ydb/ydb-docs-core/ru/core/concepts/_includes/serverless_and_dedicated/02_sls_pars.md
---

## Параметры Serverless базы данных {#serverless-options}

### Ограничения — пропускная способность, RU/с {#capacity}

При исполнении запроса к Serverless базе данных вычисляется показатель, отражающий величину ресурсов разного вида, затраченных на исполнение этого запроса. Данный показатель измеряется в специальных единицах — Request Units (RU). От суммарного потребления RU зависит стоимость использования Serverless базы данных.

Так как ресурсы Serverless базы данных неопределенно большие, то и максимальное потребление Request Units за промежуток времени также может составить любое значение, приведя к нежелательным начислениям. Например, такое может произойти в результате ошибки в коде, приводящей к запросам в бесконечном цикле.

При облачном развертывании {{ ydb-short-name }} на уровне облачных квот существует ограничение на общее количество Request Units в секунду. Но данное ограничение носит технический характер, и достаточно велико, чтобы возможная сумма счета оказалась заметно выше ожиданий. Изменение этого параметра возможно только в сторону увеличения через обращение в техническую поддержку.

Ограничение **Пропускная способность** на Serverless базе данных позволяет вам установить максимальную скорость потребления RU в секунду. С учетом 5 минутного накопления неиспользованных RU, небольшие величины этого ограничения (10 RU/с — значение по умолчанию при создании БД) позволяют успешно осуществлять широкий круг задач разработки и тестирования, а также эксплуатировать приложения с небольшой нагрузкой. При этом величина возможных начислений будет ограничена верхней границей в 2572000 секунд в месяц (30 дней), умноженной на цену за 1 миллион RU. По тарифу, актуальному на момент написания этой документации (13.36 ₽), максимально возможная сумма начислений в месяц составит около 340 ₽.

Ограничение **Пропускная способность** может быть изменено в интерактивном режиме в любой момент, как в сторону увеличения, так и в сторону уменьшения, без ограничений. Это позволяет вам оперативно менять его по мере надобности, например для прогона нагрузочного теста. Интерактивность означает, что изменение применяется с минимальной технологической задержкой, необходимой для распространения информации о новом значении по узлам {{ ydb-short-name }}.

Ограничение **Пропускная способность** может быть установлено в ноль, что приведет к возникновении исключений превышения нагрузки на любом запросе. Это может быть полезно для тестирования реакции вашего приложения на такое исключение, а также аварийному предотвращению продолжения потребления каких-либо ресурсов, если ваше приложение вышло из-под контроля.

Ограничение **Пропускная способность** может быть включено или отключено. Мы рекомендуем всегда держать его включенным, однако его отключение может оказаться полезным, если вам необходимо временно получить от базы данных максимально возможную производительность, например для обработки пакета запросов.

**Особенности применения ограничения на пропускную способность, RU/с**

При превышении ограничения запрос не принимается к исполнению, возвращается ошибка `Throughput limit exceeded`. Получение такой ошибки означает, что запрос можно безопасно повторить позже. При повторе рекомендуется использовать конструкции, поставляемые в составе {{ ydb-short-name }} SDK. В предлагаемых конструкциях реализованы алгоритмы повторов, которые в зависимости от типа и кода ошибки используют разные стратегии повторов: без задержки, с экспоненциальным увеличением задержки, быстрый или медленный повтор и другие.

Ограничение срабатывает с некоторой задержкой, поэтому ошибка `Throughput limit exceeded` возвращается не на запросе, который привел к превышению ограничения, а одном из следующих. После срабатывания ограничения запросы не будут приниматься к исполнению в течение времени, приблизительно равного отношению перерасхода к величине ограничения. Например, если на исполнение единичного запроса потрачено 1000 RU при ограничении в 100 RU/с, то новые запросы не будут приниматься в течение 10 секунд.

Для снижения риска получения отказов при неравномерной нагрузке {{ ydb-short-name }} гибко применяет ограничения, используя механизм резервирования пропускной способности (`burst capacity`). Пока на обработку запросов тратится меньше RU, чем указано в ограничении, неиспользованная пропускная способность резервируется. Во время пика потребления за счет накопленного резерва может быть временно предоставлена большая пропускная способность, чем указано в ограничении.

В {{ ydb-short-name }} резервируется около 5 минут пропускной способности. Резерв позволяет выполнить, например, единичный запрос со стоимостью около `5 мин × 60 с × квота RU/с` без отказа в исполнении следующих запросов. Политика предоставления `burst capacity` может быть изменена.

Квота на количество запросов в бессерверном режиме также является инструментом защиты от оплаты перерасхода ресурсов при сбоях в приложении или атаках на сервис. Наличие механизма `burst capacity` позволяет выставлять в квоте наименьшее значение, при котором ваше приложение работает без получения ошибок `Throughput limit exceeded`, с некоторым запасом на непредвиденный рост нагрузки.

### Ограничения — максимальный объем данных {#volume}

При использовании Serverless базы данных сумма оплаты зависит от объема хранимых данных.

Так как объем хранилища в Serverless базе данных неопределенно большой, то и максимальный объем данных, которые в нем можно разместить, также может составить любое значение, приведя к нежелательным начислениям. Например, такое может произойти в результате ошибки в коде, приводящей к вставке данных в бесконечном цикле, или случайном импорте не того бэкапа.

Ограничение **Максимальный объем данных** на Serverless базе данных позволяет вам ограничить объем данных, который {{ ydb-short-name }} позволит разместить в этой базе данных. По умолчанию для новых баз данных устанавливается ограничение в 50 ГБ, что ограничивает сумму ваших ежемесячных начислений за объем хранимых данных суммой около 650 ₽, по действующему на дату написания этой документации тарифу (13.41 ₽ за 1ГБ, 1ГБ бесплатно).

Ограничение **Максимальный объем данных** может быть изменено в интерактивном режиме в любой момент, как через графическую консоль, так и через CLI, как в сторону увеличения, так и в сторону уменьшения, без ограничений. Это позволяет вам оперативно менять его по мере надобности.

Не рекомендуется устанавливать ограничение **Максимальный объем данных** ниже текущего фактического объема данных, так как в таком состоянии станут недоступны все операции изменения данных, включая DELETE. Уменьшить объем данных можно будет только командами DROP TABLE или DROP INDEX. При случайной установке ограничения ниже фактического объема рекомендуется вернуть его к рабочему значению, превышающему фактический объем с некоторым запасом.