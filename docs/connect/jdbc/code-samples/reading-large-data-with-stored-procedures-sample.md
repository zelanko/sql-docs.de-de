---
title: Beispiel zum Lesen umfangreicher Daten mit gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 924bcf388ddf74f3be3f4bb13f83e00789fb8777
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028299"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>Beispiel zum Lesen umfangreicher Daten mit gespeicherten Prozeduren

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

In dieser Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] wird das Abrufen eines großen OUT-Parameters aus einer gespeicherten Prozedur veranschaulicht.

Die Codedatei für dieses Beispiel heißt „ExecuteStoredProcedure.java“ und befindet sich unter folgendem Pfad:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Anforderungen

Zum Ausführen dieser Beispielanwendung benötigen Sie Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Nehmen Sie außerdem die Datei „mssql-jdbc.jar“ in den Klassenpfad auf. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [Verwenden des JDBC-Treibers](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zum Auswählen der richtigen JAR-Datei finden Sie unter [Systemanforderungen für den JDBC-Treiber](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

Erstellen Sie die folgende gespeicherte Prozedur in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank:

```sql
CREATE PROCEDURE GetLargeDataValue
  (@Document_ID int,
   @Document_ID_out int OUTPUT,
   @Document_Title varchar(50) OUTPUT,  
   @Document_Summary nvarchar(max) OUTPUT)  

AS
BEGIN
   SELECT @Document_ID_out = DocumentID,
          @Document_Title = Title,  
          @Document_Summary = DocumentSummary
    FROM  Production.Document  
    WHERE DocumentID = @Document_ID  
END  
```

## <a name="example"></a>Beispiel

Im folgenden Beispielcode wird eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Datenbank hergestellt. Im Beispielcode werden anschließend Beispieldaten erstellt, und die Tabelle Production.Document wird mithilfe einer parametrisierten Abfrage aktualisiert. Dann wird der Modus für die adaptive Pufferung mithilfe der Methode [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) der Klasse [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) abgerufen und die gespeicherte Prozedur „GetLargeDataValue“ wird ausgeführt. Beachten Sie, dass ab Version 2.0 des JDBC-Treibers die responseBuffering-Verbindungseigenschaft standardmäßig auf "adaptive" festgelegt ist.

Schließlich zeigt der Beispielcode die mit den OUT-Parametern zurückgegebenen Daten an. Darüber hinaus wird die Verwendung der Methoden `mark` und `reset` im Datenstrom zum erneuten Lesen eines beliebigen Teils der Daten veranschaulicht.

[!code[JDBC#UsingAdaptiveBuffering2](../../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>Siehe auch

[Arbeiten mit umfangreichen Daten](../../../connect/jdbc/code-samples/working-with-large-data.md)
