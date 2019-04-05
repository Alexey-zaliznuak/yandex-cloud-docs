# Остановить сетевой балансировщик

---

**[!TAB Консоль управления]**

Чтобы остановить [сетевой балансировщик](../concepts/index.md):
1. Откройте раздел **Yandex Load Balancer** в каталоге, где требуется остановить балансировщик.
1. Нажмите значок ![image](../../_assets/vertical-ellipsis.svg) в строке балансировщика, который требуется остановить, или откройте страницу нужного балансировщика. 
1. Нажмите кнопку **Остановить**.
1. В открывшемся окне нажмите кнопку **Остановить**.

**[!TAB CLI]**

Если у вас еще нет интерфейса командной строки Яндекс.Облака, [установите его](https://cloud.yandex.ru/docs/cli/quickstart#install).

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

1. Посмотрите описание команды CLI для остановки сетевого балансировщика:

   ```
   $ yc load-balancer network-load-balancer stop --help
   ```

1. Получите список всех балансировщиков:

   ```
   $ yc load-balancer network-load-balancer list
   +----------------------+--------------------+-------------+----------+----------------+------------------------+----------+
   |          ID          |        NAME        |  REGION ID  |   TYPE   | LISTENER COUNT | ATTACHED TARGET GROUPS |  STATUS  |
   +----------------------+--------------------+-------------+----------+----------------+------------------------+----------+
   ...
   | b7r97ah2jn5rmo6k1dsk | test-load-balancer | ru-central1 | EXTERNAL |              1 | c58n3vh8saud47rj1cuk   |  ACTIVE  |
   ...
   +----------------------+--------------------+-------------+----------+----------------+------------------------+----------+
   ```

1. Выберите `ID` или `NAME` нужного балансировщика, находящегося в состоянии `ACTIVE`.
1. Остановите балансировщик:
   
   ```
   $ yc load-balancer network-load-balancer stop b7r97ah2jn5rmo6k1dsk
   ```

**[!TAB API]**

Остановить балансировщик можно с помощью метода API [stop](../api-ref/NetworkLoadBalancer/stop.md).

---