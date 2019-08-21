---
title: Loopback Verbindung zum SQL Server aus einem Python-oder R-Skript
description: Erfahren Sie, wie Sie eine Loopback Verbindung zum Herstellen einer Verbindung mit SQL Server über ODBC verwenden, um Daten aus einem aus sp_execute_external_script ausgeführten python-oder R-Skript zu lesen oder zu schreiben. Sie können diese Option verwenden, wenn Sie die Argumente Input DataSet und outputdataset von sp_execute_external_script nicht verwenden können.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2019
ms.topic: conceptual
author: Aniruddh25
ms.author: anmunde
ms.reviewer: dphansen
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 62b4ce483df2d38e5e2549d054c02b6c797837f3
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69657487"
---
# <a name="loopback-connection-to-sql-server-from-a-python-or-r-script"></a>Loopback Verbindung zum SQL Server aus einem Python-oder R-Skript
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Erfahren Sie, wie Sie eine Loopback Verbindung zum Herstellen einer Verbindung mit SQL Server über [ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md) verwenden, um Daten aus einem von `sp_execute_external_script`ausgeführten python-oder R-Skript zu lesen oder zu schreiben. Diese Option kann verwendet werden, wenn das **Input DataSet** -Argument und das **outputdataset** -Argument von `sp_execute_external_script` nicht verwendet werden.

## <a name="connection-string"></a>Verbindungszeichenfolge

Zum Herstellen einer Loopback Verbindung müssen Sie eine korrekte Verbindungs Zeichenfolge verwenden. Die häufigsten obligatorischen Argumente sind der Name des [ODBC-Treibers](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md), der Server Adresse und der Name der Datenbank.

### <a name="connection-string-on-windows"></a>Verbindungs Zeichenfolge unter Windows

Für die Authentifizierung auf SQL Server unter Windows kann das Python-oder R-Skript das **Trusted_Connection** -Verbindungs Zeichenfolgen-Attribut verwenden, um sich als derselbe Benutzer zu authentifizieren, der die sp_execute_external_script ausgeführt hat.

Im folgenden finden Sie ein Beispiel für die Loopback-Verbindungs Zeichenfolge unter Windows:

``` 
"Driver=SQL Server;Server=.;Database=nameOfDatabase;Trusted_Connection=Yes;"
```

### <a name="connection-string-on-linux"></a>Verbindungs Zeichenfolge unter Linux

Für die Authentifizierung auf SQL Server für Linux muss das Python-oder R-Skript die Attribute **ClientCertificate** und **clientkey** des ODBC-Treibers verwenden, um sich als derselbe Benutzer `sp_execute_external_script`zu authentifizieren, der ausgeführt hat. Hierfür ist die Verwendung der [neuesten Version des ODBC-Treibers](../../connect/odbc/download-odbc-driver-for-sql-server.md) 17.4.1.1 erforderlich.

Im folgenden finden Sie ein Beispiel für die Loopback-Verbindungs Zeichenfolge unter Linux:

```
"Driver=ODBC Driver 17 for SQL Server;Server=fe80::8012:3df5:0:5db1%eth0;Database=nameOfDatabase;ClientCertificate=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitecert.pem;ClientKey=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitekey.pem;TrustServerCertificate=Yes;Trusted_Connection=no;Encrypt=Yes"
```

Die Server Adresse, der Speicherort der Client Zertifikat Datei und der Speicherort der Client Schlüssel `sp_execute_external_script` Datei sind für jeden eindeutig und können durch die Verwendung der API- **rx_get_sql_loopback_connection_string ()** für python oder  **rxgezqlloopbackconnectionstring ()** für R.

Weitere Informationen zu den Attributen der Verbindungs Zeichenfolge finden Sie in den [Schlüsselwörtern und Attributen der DSN und Verbindungs Zeichenfolge](https://docs.microsoft.com/sql/connect/odbc/dsn-connection-string-attribute?view=sql-server-linux-ver15#new-connection-string-keywords-and-connection-attributes) für Microsoft ODBC Driver for SQL Server.

## <a name="generate-connection-string-with-revoscalepy-for-python"></a>Generieren der Verbindungs Zeichenfolge mit revoscalepy für python

Sie können die API- **rx_get_sql_loopback_connection_string ()** in [revoscalepy](../python/ref-py-revoscalepy.md) verwenden, um eine korrekte Verbindungs Zeichenfolge für eine Loopback Verbindung in einem Python-Skript zu generieren.

Die folgenden Argumente werden akzeptiert:

| Argument | Beschreibung |
|-|-|
| name_of_database | Der Name der Datenbank, mit der die Verbindung hergestellt werden soll. |
| odbc_driver | Name des ODBC-Treibers |

### <a name="examples"></a>Beispiele

Beispiel für SQL Server unter Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="SQL Server", name_of_database="DBName")
print("Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Beispiel für SQL Server für Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="ODBC Driver 17 for SQL Server",
                                                                   name_of_database="DBName")
print("Loopback Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="generate-connection-string-with-revoscaler-for-r"></a>Generieren der Verbindungs Zeichenfolge mit revoscaler für R

Sie können die API **rxgetionqlloopbackconnectionstring ()** in [revoscaler](../r/ref-r-revoscaler.md) verwenden, um eine korrekte Verbindungs Zeichenfolge für eine Loopback Verbindung in einem R-Skript zu generieren.

Die folgenden Argumente werden akzeptiert:

| Argument | Beschreibung |
|-|-|
| nameof-Datenbank | Der Name der Datenbank, mit der die Verbindung hergestellt werden soll. |
| odbcdriver | Name des ODBC-Treibers |

### <a name="examples"></a>Beispiele

Beispiel für SQL Server unter Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <- rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", odbcDriver ="SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName",
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Beispiel für SQL Server für Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <-  rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", 
                                                                  odbcDriver ="ODBC Driver 17 for SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName", 
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="next-steps"></a>Nächste Schritte

+ [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)
+ [revoscalepy](../python/ref-py-revoscalepy.md)
+ [RevoScaleR](../r/ref-r-revoscaler.md)
