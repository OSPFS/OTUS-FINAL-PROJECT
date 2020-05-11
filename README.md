## Проектная работа
***
В данный проект описывает реализацию WEB-сервиса высокой доступности. Для обеспечеения отказоустойчивости, кроме самого WEB-сервиса так-же продублированы маршрутизаторы, балансировщики нагрузки, база данных кластеризавана. Осуществляется мониторинг серверов с помощью Zabbix и сбор логов балансировщиков в Elasticsearch. Резервное копирование серверов WEB приложений осуществляется с помощью borgbackup, кластера PostgreSQL при помощи pg_probackup.
*** 

![](/MainDiagram.jpg)

