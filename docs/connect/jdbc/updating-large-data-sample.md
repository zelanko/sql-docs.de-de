---
title: Beispiel zum Aktualisieren großer Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c410e119ccc544901ea6734eff97f847429045fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760898"
---
# <a name="updating-large-data-sample"></a>Beispiel zum Aktualisieren umfangreicher Daten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] veranschaulicht, wie eine umfangreiche Spalte in einer Datenbank aktualisiert wird.

Die Codedatei für dieses Beispiel heißt „UpdateLargeData.java“ und befindet sich unter folgendem Pfad:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Anforderungen

Zum Ausführen dieser Beispielanwendung benötigen Sie Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Außerdem müssen Sie die Datei "sqljdbc4.jar" in den Klassenpfad aufnehmen. Wenn im Klassenpfad kein Eintrag für "sqljdbc4.jar" vorhanden ist, löst die Beispielanwendung die allgemeine Ausnahme "Klasse nicht gefunden" aus. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] stellt die Klassenbibliotheksdatei „sqljdbc.jar“, „sqljdbc4.jar“, „sqljdbc41.jar“ oder „sqljdbc42.jar“ für die jeweilige Verwendung mit den bevorzugten JRE-Einstellungen (Java Runtime Environment) bereit. In diesem Beispiel werden die in der JDBC 4.0-API neu eingeführten Methoden [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) und [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) für den Zugriff auf die treiberspezifischen Antwortpuffermethoden verwendet. Zum Kompilieren und Ausführen dieses Beispiels benötigen Sie die "sqljdbc4.jar"-Klassenbibliothek, die die Unterstützung für JDBC 4.0 bereitstellt. Weitere Informationen zu der JAR-Datei auswählen, finden Sie unter [Systemanforderungen für JDBC Driver](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Beispiel

Im folgenden Beispielcode wird eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Datenbank hergestellt. Danach wird ein Statement-Objekt erstellt und mithilfe der [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)-Methode überprüft, ob das Statement-Objekt ein Wrapper für die angegebene [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse ist. Die [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)-Methode wird für den Zugriff auf treiberspezifische Antwortpuffermethoden verwendet.

Dann wird der Antwortpuffermodus mithilfe der [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse auf **Adaptiv** festgelegt und veranschaulicht, wie der Modus für die adaptive Pufferung abgerufen wird.

Anschließend wird die SQL-Anweisung ausgeführt, und die zurückgegebenen Daten werden in ein aktualisierbares [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt eingefügt.

Schließlich werden die Datenzeilen im Resultset durchlaufen. Wenn eine leere Dokumentzusammenfassung erkannt wird, wird die Datenzeile mit einer Kombination aus [updateString](../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)-Methode und [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)-Methode aktualisiert und erneut in der Datenbank gespeichert. Wenn bereits Daten vorhanden sind, werden einige der Daten mithilfe der [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)-Methode angezeigt.

Das Verhalten des Treibers ist standardmäßig auf **Adaptiv** festgelegt. Für das aktualisierbare Resultset mit Vorwärtscursor und bei Daten, deren Größe die des Anwendungsspeichers übersteigt, muss der Modus für die adaptive Pufferung von der Anwendung jedoch explizit mithilfe der [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse festgelegt werden.

[!code[JDBC#UsingAdaptiveBuffering3](../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Arbeiten mit umfangreichen Daten](../../connect/jdbc/working-with-large-data.md)
