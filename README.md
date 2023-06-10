# make_C4_6_1
Разверните на Server2 Elasticsearch+Kibana. Настройте визуализацию логов Kibana на ней самой. Log shipper используйте любой на ваш выбор.

Для реализации задачи выбрал Log shipper filebeat
Конфигура ция не сильно изменена, определил отправку в elasticsearch:
https://github.com/vinkin56/make_C4_6_1/blob/main/filebeat.conf

Для мониторинга событий операционной системы установил auditd:
https://github.com/vinkin56/make_C4_6_1/blob/main/elastic_auditd.jpg

На скриншотах можно видеть Dashboard программы

Результат работы:
https://github.com/vinkin56/make_C4_6_1/blob/main/elastic_filebeat_08062023.jpg

Дополнительно установил Kibana sample data log:
https://github.com/vinkin56/make_C4_6_1/blob/main/kibana_sample.jpg

Были определённые трудности в стабильности работы filebeat следующего типа:
× filebeat.service - Filebeat sends log files to Logstash or directly to Elasticsearch.
     Loaded: loaded (/lib/systemd/system/filebeat.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Sat 2023-06-10 13:41:47 UTC; 23min ago
       Docs: https://www.elastic.co/products/beats/filebeat
    Process: 1214 ExecStart=/usr/share/filebeat/bin/filebeat --environment systemd $BEAT_LOG_OPTS $BEAT_CONFIG_OPTS $BEAT_PATH_OPTS (code=exited, status=2)
   Main PID: 1214 (code=exited, status=2)
        CPU: 143ms

Jun 10 13:41:47 server2 filebeat[1214]: rip    0x7f40937dfa7c
Jun 10 13:41:47 server2 filebeat[1214]: rflags 0x246
Jun 10 13:41:47 server2 filebeat[1214]: cs     0x33
Jun 10 13:41:47 server2 filebeat[1214]: fs     0x0
Jun 10 13:41:47 server2 filebeat[1214]: gs     0x0
Jun 10 13:41:47 server2 systemd[1]: filebeat.service: Scheduled restart job, restart counter is at 6.
Jun 10 13:41:47 server2 systemd[1]: Stopped Filebeat sends log files to Logstash or directly to Elasticsearch..
Jun 10 13:41:47 server2 systemd[1]: filebeat.service: Start request repeated too quickly.
Jun 10 13:41:47 server2 systemd[1]: filebeat.service: Failed with result 'exit-code'.
Jun 10 13:41:47 server2 systemd[1]: Failed to start Filebeat sends log files to Logstash or directly to Elasticsearch..
