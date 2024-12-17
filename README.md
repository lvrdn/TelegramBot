# TelegramBot

Телеграм бот - менеджер задач.

Для запуска бота необходимо создать бота в @BotFather и получить токен. В настройках бота (в @BotFather) можно указать перечень команд, чтобы они отображались у пользователей при использовании бота.
Для вебхука необходимо пробросить порт, сделать это можно в VS Code (для порта необходимо установить параметр Port Visibility = public). VS Code сформирует url.
Сформированный токен и url необходимо вписать в конфиг файл app.env. В нем же указать номер порта, который указывался при проброске.

Текстовые команды:
1. /tasks - выводит список всех незавершенных задач, для каждого пользователя список задач будет выглядеть по-разному:

    <details>
      
    <summary>для пользователя user1</summary>
    
    ```
    1. task1 by @user1
    assignee: @user2
    /assign_1
    
    2. task2 by @user2
    /assign_2
    ```
    
    </details>
    
    <details>
      
    <summary>для пользователя user2</summary>
    
    ```
    1. task1 by @user1
    assignee: я
    /unassign_1 /resolve_1
    
    2. task2 by @user2
    /assign_2
    ```
    
    </details>

2. /new some_task - создание новой задачи "some_task" пользователем user1:

    <details>
      
    <summary>для пользователя user1</summary>
    
    ```
    Задача "some_task" создана, id=3
    ```
    
    </details>

3. /assign 3 (или assign_3) - взять задачу с id=3 себе, взявшему задачу и создателю задачи отправляются уведомления. Можно взять задачу, которую уже взял другой пользователь.

    сценарий: user2 берет задачу "some_task" (id=3), созданную user1:

    <details>
      
    <summary>для пользователя user1</summary>
    
    ```
    Задача "some_task" назначена на @user2
    ```
    
    </details>
    
    <details>
      
    <summary>для пользователя user2</summary>
    
    ```
    Задача "some_task" назначена на вас
    ```
    
    </details>

4. /unassign 3 (или unassign_3) - отказаться от задачи с id=3, отказаться можно только от конкретной задачи может только пользователь, который ее взял (в противном случае будет получено сообщение "Задача не на вас"). Пользователю и создателю задачи отправляются уведомления.

    сценарий: user2 отказывается от задачи "some_task" (id=3), созданной user1:

    <details>
      
    <summary>для пользователя user1</summary>
    
    ```
    Задача "some_task" осталась без исполнителя
    ```
    
    </details>
    
    <details>
      
    <summary>для пользователя user2</summary>
    
    ```
    Принято
    ```
    
    </details>

5. /resolve 3 (или resolve_3) - отметить задачу с id=3 выполненной, выполнить конкретную задачу может только пользователь, который ее взял (в противном случае будет получено сообщение "Задача не на вас"). Пользователю и создателю задачи отправляются уведомления. После выполнения данной команды задача перестает отображаться при просмотре списка задач.

    сценарий: user2 выполняет задачу "some_task" (id=3), созданную user1:

    <details>
      
    <summary>для пользователя user1</summary>
    
    ```
    Задача "some_task" выполнена @user2
    ```
    
    </details>
    
    <details>
      
    <summary>для пользователя user2</summary>
    
    ```
    Задача "some_task" выполнена
    ```
    
    </details>

6. /my - выводит список задач, которые пользователь взял себе на выполнение, формат вывода аналогичен пункту 1.

7. /owner - выводит список задач, кототорые пользователь создал, формат вывода аналогичен пункту 1.
