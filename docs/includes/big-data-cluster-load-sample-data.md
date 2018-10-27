### <a id="sampledata"></a> Laden von Beispieldaten

Tutorials für SQL Server big Data-Cluster verwenden einen gemeinsamen Satz von Beispieldaten. Verwenden Sie die folgenden Schritte aus, um die Beispieldaten für Ihre big Data-Cluster zu konfigurieren:

1. Wenn Sie nicht über die SQL Server-Befehlszeilentools verfügen (**Sqlcmd** und **Bcp**) installiert ist, zunächst diese Tools mit einer der Links installieren:

   * **Windows**: [Installieren von SQL Server-Befehlszeilentools für Windows](https://www.microsoft.com/download/details.aspx?id=53591)
   * **Linux**: [Installieren von SQL Server-Befehlszeilentools für Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-tools)

1. Herunterladen die Beispiel-Sicherungsdatei [tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) auf Ihrem Computer.

1. Navigieren Sie zu der SQL Server-2019 big Data-Cluster [Verzeichnis "Samples"](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster).

1. Herunterladen der [Bootstrap-Beispiel-db.sql](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql) Transact-SQL-Skript.

1. Herunterladen Sie, und führen Sie einen der folgenden zwei Beispielskripts von der Befehlszeile aus:

   * **Windows**: [Bootstrap-Beispiel-db.cmd](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd)
   * **Linux**: [Bootstrap-Beispiel-db.sh](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh)

   > [!TIP]
   > Anweisungen zur Verwendung erhalten Sie durch Ausführen des Skripts ohne Parameter.

Das Skript stellt die-Beispieldatenbank master SQL Server-Instanz wieder her und lädt auch die Daten in HDFS im Speicherpool.