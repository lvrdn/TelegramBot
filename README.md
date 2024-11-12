# 10.TelegramBot

Цель задания - сздание менеджера задач в телеграм-боте.
Особенности проекта:
1. Код программы разделен на несколько слоев: в первом слое осуществляется взаимодействие с серверами телеграмма. На втором слое осщуствляется роутинг запросов. На третьем слое описаны сами хендлеры, обрабатывающие соответствующие запросы. Последний слой - слой хранения данных в памяти.
2. Для запуска тестов имитируется сервер телеграмма путем использования отредактированной библиотеки telegram-bot-api (приложена вместе с условиями задания).
3. Запуск приложения для работы с реальными серверами телеграмма осуществлялся через открытия порта локальной машины в VS code.
4. В хендлерах обращение к хранению информацию осуществляется через интерфейс, соответственно изменение логики хранения информации (например в БД) не потребует изменений в остальном коде.
5. Для пользователя реализована возможность просмотреть список всех активных задач, список задач, которые создал пользователь, создать новую задачу, назначить задачу на себя или другого пользователя, снимать задачу с пользователя, завершать задачу. Другие пользователи, которые могут быть назначены на выполнение задач, или когда с их задачами происходят изменения, получают об этом уведомления в чате с ботом.

Перечень основных файлов проекта:
1. taskbot.go - старт бота, слой взаимодействия с телеграммом и передача данных в следующий слой.
2. taskbotT.go - тот же файл, но для запуска тестов (с подменой пакета библиотеки telegram-bot-api).
3. router.go - слой роутинга запросов, вызов соответствующего обработчика.
4. handlers.go - слой с обработчиками.
5. repositiry.go - слой хранения информации.
6. HW_readme.md - описание условий задания.
7. taskbot_test.go - приложенные к условиям задания тесты.
8. /local - папка с измененной библиотекой telegram-bot-api для прохождения тестов.
