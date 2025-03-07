Функциональность приложения:
Управление отоплением:
  Пользователи могут удалённо включать/выключать отопление в своих домах.
     post(/api/heating/{id}/turn-on)
     post(/api/heating/{id}/turn-off)
  Пользователи могут устанавливать желаемую температуру.
     post(/api/heating/{id}/set-temperature)
  Система автоматически поддерживает заданную температуру, регулируя подачу тепла.

Мониторинг температуры:
  Система получает данные о температуре с датчиков, установленных в домах.
  Пользователи могут просматривать текущую температуру в своих домах через веб-интерфейс.
     get(/api/heating/{id}/current-temperature)
     get(/api/heating/{id})

Архитектуру монолитного приложения:
 Язык программирования: Java
 База данных: PostgreSQL
 Архитектура: Монолитная, все компоненты системы (обработка запросов, бизнес-логика, работа с данными) находятся в рамках одного приложения.
 Взаимодействие: Синхронное, запросы обрабатываются последовательно.
 Масштабируемость: Ограничена, так как монолит сложно масштабировать по частям.
 Развертывание: Требует остановки всего приложения.

Домены и границы контекстов: 
  Domen "Удалённое управление отоплением в доме"
      Контекст "Управление отоплением"  
        Сущность: "Система отопления"
        Объекты-значения: температура целевая, температура текушая,  режим работы
        Агрегаты: "Система отопления"
        Репозитории: репозиторий систем отопления
        Сервисы: Cервис работы с системой отопления
      Контекст "Мониторинг температуры датчиков"
        Сущность: Датчик температуры
        Объекты-значения: температура текущая, время последнего обновления данных о температуре 
        Агрегаты: Датчик температуры 
        Репозитории: репозиторий датчиков температуры;
        Сервисы: -



Задание 2. Визуализируйте архитектуру, которая у вас получилась
  Файл System_Context_diagram.puml
  Файл component_diagram_v1.puml
 
Задание 3. Разработка ER-диаграммы
  Файл erd_diagram.puml