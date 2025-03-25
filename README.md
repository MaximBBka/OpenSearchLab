Это лаба, предназначенная для тренировки работы с OpenSearch в кластере Kubernetes.

Как запустить:
1) Нужно поднять OpenSearch. Ссылка на репозиторий OpenSearch:
https://github.com/opensearch-project/helm-charts/tree/main (все описано у них в Readme)
2) Когда OpenSearch заработал, нужно тип у объекта Service opensearch-dashboard и master-opensearch поменять на NodePort, что бы обращаться к приложениям извне.
3) Поднимаем тестовое приложение nginx и агент fluent-bit который будет собирать логи из приложения и отпровлять в back OpensSearch:
docker-compose up -d
Логи с приложения nginx будут находиться в файлах my-error, my-acces.
НЕ ЗАБУДЬ В КОНФИГУРАЦИИ fluent-bit ПОМЕНЯТЬ HOST И ПОРТ НА СВОЙ.

Как тестировать:
1) Заходим в dashboard OpenSearch:
В разделе Index Manager создаем новый Index Patterns по названию который указан в конфигурации fluent-bit.
2) Заходим в раздел Discavery, выбираем созданный наш Patterns и смотрим логи с приложения.
Что бы логи появлялись сделай запросы в приложении nginx.

Если не работает:
1) Проверяй логи контейнера fluent-bit если у него свзяь c master-opensearch.
2) Проверяй работает ли сам OpenSearch
Гайд как поднять OpenSearch:
https://www.youtube.com/watch?v=xVf1dy2uiL0
 
Лаба готова!
