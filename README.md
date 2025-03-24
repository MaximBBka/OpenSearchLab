Шаги:
1) Поднмиаем OpenSearch от сюда - https://github.com/opensearch-project/helm-charts/tree/main (все описано у них в Readme)
2) Поменяйте тип service у opensearch-dashboard и master-opensearch на NodePort
3) docker-compose up -d (Запуститься приложение nginx и fluent-bit)
4) Все логи от приложения будут грузиться в файлы my-error, my-acces. Конфиг fluent-bit будет смотреть в эти файлы и отдавать их в master-opensearch.
5) Заходим в dashboard выбираем index patterns который указывали в конфиге для fluent-bit. В разделе discavery будут наши логи. Победа!
