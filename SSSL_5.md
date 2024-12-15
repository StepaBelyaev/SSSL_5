# Практика 3
## Беляев Степан Константинович
## ББМО-02-23


### Начало
#### 2 ВМ
Работа была выполнена на 3 виртуальных машинах на базе ОС Ubuntu и Kali, 2 client и 1 server
![1](https://github.com/user-attachments/assets/0af6f18d-546f-4ada-add9-29abf6fb572d)

#### Сетевой обмен
На виртуальных машинах был настроен сетевой мост
![2](https://github.com/user-attachments/assets/ad22a9f9-4a02-421b-bcb4-99b7213ed873)

Также ВМ на базе linux была подключена к Wazuh
![3](https://github.com/user-attachments/assets/34888cf7-1110-45b9-b0c7-582c23c8c9b9)
![4](https://github.com/user-attachments/assets/b9ebe0f3-2346-42a5-9fcb-0bdfb9435b31)

#### Работа Wazuh
ПРоведем ряд операций по попытке авторизоваться под пользователем root и иным пользователем, сознательно собирая ошибки в логине и пароле
![5](https://github.com/user-attachments/assets/1b5f30fd-029c-4f5f-9228-dcd1130fc79b)

В результате Wazuh выдает предупрждение о наших попытках с подробной информацией
![6](https://github.com/user-attachments/assets/ad889bec-c0a8-4f2f-971e-3507a7a761e8)
![7](https://github.com/user-attachments/assets/50161b01-f2e8-403a-b331-1fbe4d561dde)

#### Suricata
Скачиваем Suricata
![9](https://github.com/user-attachments/assets/95cd8697-1323-479f-b053-7ba3c5d41570)
![10](https://github.com/user-attachments/assets/b459a96e-bf22-4b0d-8e05-ec93508820fb)

Установим ряд правил для Suricata
![14](https://github.com/user-attachments/assets/d32147d8-8852-4235-a5a4-f92bf53a6d55)

Пропингуем нашего агента для работы suricata
![13](https://github.com/user-attachments/assets/ac9014ee-9a80-4e2e-b09d-464a8e613230)

И видиим предупреждения, подвтерждающие работу системы
![16](https://github.com/user-attachments/assets/98639d6a-ba42-4afc-94f3-b4563c6b2e9b)

#### Openvas
Ставим на систему докер для дальнейшей работы
![17](https://github.com/user-attachments/assets/86ac2cc4-4050-4b62-9412-175ecca1c37c)

Ставить openvas будем как раз через докер
![18](https://github.com/user-attachments/assets/1f8d4126-b19d-4335-b149-764bb157b2bf)
![19](https://github.com/user-attachments/assets/01c907a2-bf1f-49ce-b34c-482cf8211f20)
![20](https://github.com/user-attachments/assets/7c0c7bfa-8b0a-4771-8ce1-a0db1996bd80)

В ходе работы выяснилось, что данный докер не функционирует и нужен иной на новой ВМ (на прежней не было выделено достаточной памяти)
![22](https://github.com/user-attachments/assets/1323e266-0810-4146-97c1-3dff9c7ba80a)
![23](https://github.com/user-attachments/assets/e927af8a-ad8b-4c9a-8a35-b2d5359bb511)
![24](https://github.com/user-attachments/assets/e2a12367-87c3-4dae-8a69-9c8af684b370)
![25](https://github.com/user-attachments/assets/02e60c79-70d7-4981-8445-804ff0595566)
![26](https://github.com/user-attachments/assets/ee42f80e-8cd2-4cf6-b0e5-b504f6550a1c)

Проверим, работает ли нас openvas на агенте
![27](https://github.com/user-attachments/assets/c20642d1-1030-4168-a91d-9780b3122a0b)

Закончим установку Openvas
![29](https://github.com/user-attachments/assets/dd3a487c-efd9-4e9c-8fa2-dc419ddf3dcb)
![31](https://github.com/user-attachments/assets/325fc36b-dacc-4bf6-aaf6-fbb9fabc320a)

Теперь, из соотвествующего меню запустим сканирование и посмотрим на результаты
![32](https://github.com/user-attachments/assets/1ff1d5a9-edd5-44d1-9b0c-278703f1b69e)
![33](https://github.com/user-attachments/assets/6b3ff2ae-498e-4d81-ae71-70b4018d820d)

#### Yara

Схема взаимодействия Yara и Wazuh выглядит следующим образом
![49](https://github.com/user-attachments/assets/7985adfd-159b-4cb2-a147-4f57521a3a5e)

Загрузим и уставновим Yara
![34](https://github.com/user-attachments/assets/cd63b09f-7b74-432c-a507-1cf4d359831a)
![35](https://github.com/user-attachments/assets/8df3c355-018d-4085-98d1-c02e1c837031)

Проверим работает ли Yara после установки
![36](https://github.com/user-attachments/assets/63b4b86a-ebb1-4d6b-8e3a-9c5e01e9cb6b)

Теперь займемся правилами для Yara
![37](https://github.com/user-attachments/assets/8a145465-7dfd-4105-b0ed-249edea4cecf)
![38](https://github.com/user-attachments/assets/fb88036a-9b51-4492-85c0-e1cf4a64d991)

Создадим для Yara скрипт работы
![39](https://github.com/user-attachments/assets/d8e3c9d3-e70d-4120-af9d-a5dbc399618a)
![40](https://github.com/user-attachments/assets/fc0d9441-c92c-4bf8-99a6-526f1fd5fe10)

Выдадим для скрипта нужные права доступа
![41](https://github.com/user-attachments/assets/3e2c15c8-2edf-44ef-97e3-a55a38146283)

Установим jq утилиту для обработки данных JSON из оповещений FIM
![42](https://github.com/user-attachments/assets/f2a0463b-d357-4749-8260-7b50f89ccabf)

Добавим следующее в блок <syscheck> файла конфигурации агента Wazuh /var/ossec/etc/ossec.conf для мониторинга каталога /root/
![43](https://github.com/user-attachments/assets/b638b22e-ebf5-45da-a639-3830b558f422)
Не забываем про перезапуск WAzuh
![44](https://github.com/user-attachments/assets/67288157-abc3-4afe-9d1d-92f7ff153f49)

Добавим следующие пользовательские декодеры в файл /var/ossec/etc/decoders/local_decoder.xml: Это позволяет извлекать информацию из результатов сканирования YARA:
![45](https://github.com/user-attachments/assets/d72d331b-4a65-41d4-916e-fab62bf2f086)

Добавим следующие пользовательские правила в /var/ossec/etc/rules/local_rules.xml
![46](https://github.com/user-attachments/assets/d3afe081-9d4f-4499-bd88-fa97a1b7cfee)

Настроим выполнение сценария YARA при добавлении или изменении файлов в отслеживаемом каталоге
![47](https://github.com/user-attachments/assets/2d31b782-9ab8-4ee3-bb41-0416033b8034)

Загрузим образцы вредоносных программ и поместите их в каталог /root/ на отслеживаемой конечной точке для проверки работы Yara
![48](https://github.com/user-attachments/assets/9a42bd17-4517-4878-b555-bf3f28911f60)

Yara успешно отработала.

На выполнение практики ушло несколько полных дней с перебором различных варинтов инустрментов т.к. что-то не работало на текущих весриях ВМ. Где-то, как в случае Nessus, уставновка инструмента приводила к тмоу, что он максимально нагружал ВМ и приводил к преждеврменному прекращению работы. 










