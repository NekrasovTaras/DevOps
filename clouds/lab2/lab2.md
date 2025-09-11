# Лабораторная работа 2  
**Сравнение сервисов Amazon Web Services и Microsoft Azure. Создание единой кросс-провайдерной сервисной модели**

---

##  Цель работы
- Получение навыков аналитики и понимания спектра публичных облачных сервисов **без привязки к вендору**.  
- Формирование у студентов комплексного видения **Облака**.  

---

## Дано
- Данные **Лабораторной работы 1**.  
- Слепок данных биллинга от провайдера после небольшой обработки в виде **SQL-параметров**.  
  Символ `%` в начале/конце означает, что перед/после него может стоять **любой набор символов**.  
- Образец итогового соответствия, которое желательно получить в конце (содержится в этом же документе).  

---

## Необходимо
1. **Импортировать** файл `.csv` в Excel или любую другую программу работы с таблицами.  
   - Для Excel: вкладка **Данные → Из текстового/CSV файла → выбрать файл → разделитель – точка с запятой**.  
2. **Распределить потребление сервисов по иерархии**, чтобы можно было провести анализ от большего к меньшему.  
   - Пример: от всех вычислительных ресурсов **Compute** → до конкретного использования **Dedicated host usage**.  
   - При этом сохранять логическую концепцию, выработанную в **Лабораторной работе 1**.  
3. Сохранить файл и **загрузить в соответствующую папку на Google Drive**.  

---

##  Алгоритм работы
1. Сопоставить входящие данные от провайдера с его документацией.  
2. В колонках справа написать соответствующие значения 5 колонок слева, которые бы **однозначно классифицировали тип сервиса**.  
3. Для столбцов **IT Tower** и **Service Family** можно использовать значения из образца.  
4. В ходе выполнения работы придерживаться принципов классификации из **Лабораторной работы 1**.  


---

From the very beginning, разберемся с сервисами и с тем, что каждый из них значит, как его можно классифицировать. Будем использовать для этого документацию сервисов Azure

| Ресурс                           | Сервис Azure                        | Краткое описание                                                                 |
|----------------------------------|--------------------------------------|----------------------------------------------------------------------------------|
| Microsoft.ContainerInstance      | Azure Container Instances            | Запуск контейнеров в управляемом окружении без развёртывания сложной оркестрации. |
| Microsoft.ContainerRegistry      | Azure Container Registry             | Хранилище для Docker-образов с возможностью их сборки прямо в Azure.              |
| Microsoft.CustomerInsights       | Dynamics 365 Customer Insights       | Анализ данных о клиентах для персонализации и оптимизации бизнес-процессов.       |
| Microsoft.DataBox                | Azure Data Box                       | Оффлайн-перенос больших объёмов данных (десятки терабайт) между локальной средой и Azure. |
| Microsoft.DataLakeAnalytics      | Azure Data Lake Analytics            | Аналитика больших данных с динамическим масштабированием и оплатой за вычисления. |
| Microsoft.DataLakeStore          | Azure Data Lake Storage              | Дополнение к Blob Storage с улучшенной безопасностью и поддержкой анализа данных. |
| Microsoft.sql                    | Azure SQL (DB, Managed Instance, VM) | Набор сервисов для работы с SQL: база данных, управляемый экземпляр и SQL Server на ВМ. |
| Microsoft.MachineLearningServices| Azure Machine Learning               | Платформа для создания, обучения и публикации моделей машинного обучения.         |
| Microsoft.Search                 | Azure AI Search                      | Поисковая система с ИИ для индексирования и интеллектуального поиска данных.      |
| Microsoft.Network                | Azure Networking (разные сервисы)    | Сетевые сервисы (DNS, Firewall, DDoS, Load Balancer и др.); в биллинге — App Gateway и Network Watcher. |
| —                                | Azure Network Watcher                | Мониторинг и диагностика облачной сетевой инфраструктуры (ВМ, сети, балансировщики). |
| —                                | Azure Application Gateway            | Балансировщик уровня приложений для распределения запросов к веб-сервисам.        |
| microsoft.operationalinsights    | Azure Monitor (Operational Insights) | Мониторинг и диагностика состояния облачных ресурсов и сетевой инфраструктуры.   |


Теперь легко можем восстановить пропуски в табличке!

<img width="1374" height="622" alt="image" src="https://github.com/user-attachments/assets/d589d658-187e-4a56-a5e8-3afd76a06841" />

#№# Выводы
В качестве вывода к работе привожу таблицу со схожестями из миров AWS и Azure. Понимание этих схожестей облегчает анализ и построение кросс-облачных архитектур.

## Таблица соответствий сервисов AWS и Azure

| Категория      | AWS Service              | Azure Service                  |
|----------------|--------------------------|--------------------------------|
| Compute        | EC2                      | Virtual Machines               |
| Compute        | Lambda                   | Functions                      |
| Compute        | SageMaker                | Machine Learning               |
| Storage        | S3                       | Blob Storage / Data Lake Store |
| Storage        | EFS                      | File Storage                   |
| Storage        | Snowball                 | Data Box                       |
| Database       | RDS                      | SQL Database / Managed Instance|
| Database       | DynamoDB                 | Cosmos DB                      |
| Containers     | ECS / Fargate            | Container Instances            |
| Containers     | ECR                      | Container Registry             |
| Analytics      | EMR / Athena             | Data Lake Analytics            |
| Networking     | VPC                      | Virtual Network                |
| Networking     | ELB                      | Application Gateway / Load Balancer |
| Networking     | CloudWatch Logs          | Network Watcher / Operational Insights |
| AI / Search    | Kendra                   | AI Search                      |
| CRM / Insights | —                        | Customer Insights              |
