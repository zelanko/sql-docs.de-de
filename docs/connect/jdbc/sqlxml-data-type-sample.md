---
title: SQLXML-Datentyp Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8f2ff25b-71fd-46d7-b6de-d656095d2aad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f0cc8e3e48024e6d5af789919173454d0ee05e56
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027648"
---
# <a name="sqlxml-data-type-sample"></a>Beispiel für den SQLXML-Datentyp

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] veranschaulicht das Speichern von XML-Daten in einer relationalen Datenbank, das Abrufen von XML-Daten aus einer Datenbank sowie das Analysieren von XML-Daten mit dem Java-Datentyp **SQLXML**.

In den Codebeispielen in diesem Abschnitt wird ein SAX (Simple API for XML)-Parser verwendet. SAX ist ein öffentlich entwickelter Standard für die ereignisbasierte Analyse von XML-Dokumenten. Es stellt außerdem eine Anwendungsprogrammierschnittstelle für die Arbeit mit XML-Daten bereit. Beachten Sie, dass in den Anwendungen ebenso jeder andere XML-Parser wie DOM (Document Object Model) oder StAX (Streaming API for XML) usw. verwendet werden kann.

DOM (Document Object Model) stellt eine programmgesteuerte Darstellung der XML-Dokumente, -Fragmente, -Knoten oder -Knotensätze bereit. Es stellt außerdem eine Anwendungsprogrammierschnittstelle für die Arbeit mit XML-Daten bereit. Entsprechend handelt es sich bei StAX (Streaming API for XML) um eine Java-basierte API für die Pullanalyse von XML.

> [!IMPORTANT]  
> Um die SAX-Parser-API verwenden zu können, müssen Sie die SAX-Standardimplementierung aus dem Paket "javax.xml" importieren.

Die Codedatei für dieses Beispiel heißt „SqlXmlDataType.java“ und befindet sich im folgenden Pfad:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes
```

## <a name="requirements"></a>Anforderungen

Wenn Sie diese Beispielanwendung ausführen möchten, müssen Sie die Datei "sqljdbc4.jar" in den Klassenpfad aufnehmen. Wenn im Klassenpfad kein Eintrag für „sqljdbc4.jar“ vorhanden ist, löst die Beispielanwendung die Ausnahme „ClassNotFound“ aus. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../connect/jdbc/using-the-jdbc-driver.md).

Außerdem benötigen Sie zum Ausführen dieser Beispielanwendung Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank.

## <a name="example"></a>Beispiel

Der folgende Beispielcode stellt eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Datenbank her und ruft dann die createSampleTables-Methode auf.

Mit der createSampleTables-Methode werden die Testtabellen „TestTable1“ und „TestTable2“ gelöscht, sofern diese vorhanden sind. Dann werden zwei Zeilen in TestTable1 eingefügt.

Darüber hinaus enthält das Codebeispiel die folgenden drei Methoden und eine zusätzliche Klasse mit dem Namen "ExampleContentHandler".

Die ExampleContentHandler-Klasse implementiert einen benutzerdefinierten Inhaltshandler, der Methoden für Parserereignisse definiert.

Die showGetters-Methode veranschaulicht das Analysieren der Daten im SQLXML-Objekt mit SAX, ContentHandler und XMLReader. Zunächst erstellt das Codebeispiel eine Instanz eines benutzerdefinierten Inhaltshandlers, dem ExampleContentHandler. Dann wird eine SQL-Anweisung erstellt und ausgeführt, die einen Datensatz aus TestTable1 zurückgibt. Anschließend werden im Codebeispiel ein SAX-Parser abgerufen und die XML-Daten analysiert.

Die showSetters-Methode veranschaulicht das Festlegen der **XML**-Spalte mit SAX, ContentHandler und ResultSet. Zunächst wird mit der [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)-Methode der Connection-Klasse ein leeres SQLXML-Objekt erstellt. Dann wird eine Instanz eines Inhaltshandlers abgerufen, um die Daten in das SQLXML-Objekt zu schreiben. Anschließend werden die Daten im Codebeispiel in TestTable1 geschrieben. Schließlich durchläuft der Beispielcode die Datenzeilen im Resultset und liest die XML-Daten mithilfe der [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)-Methode.

Die showTransformer-Methode veranschaulicht das Abrufen von XML-Daten aus der einen Tabelle, die dann mit SAX und Transformer in eine andere Tabelle eingefügt werden. Zunächst wird das SQLXML-Quellobjekt aus TestTable1 abgerufen. Dann wird mit der [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)-Methode der Connection-Klasse ein leeres SQLXML-Zielobjekt erstellt. Daraufhin wird das SQLXML-Zielobjekt aktualisiert, und die XML-Daten werden in TestTable2 geschrieben. Schließlich durchläuft der Beispielcode die Datenzeilen im Resultset und liest die XML-Daten in TestTable2 mithilfe der [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)-Methode.

[!code[JDBC#UsingSQLXML1](../../connect/jdbc/codesnippet/Java/sqlxml-data-type-sample_1.java)]

## <a name="see-also"></a>Siehe auch

[Arbeiten mit Datentypen &#40;JDBC&#41;](../../connect/jdbc/working-with-data-types-jdbc.md)
