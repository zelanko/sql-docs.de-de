---
title: Programmieren mit SQLXML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4d2cc57c-7293-4d92-b8b1-525e2b35f591
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 399100d6e718138012453e47fdfe8d11386f8cbd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47754898"
---
# <a name="programming-with-sqlxml"></a>Programmieren mit SQLXML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In diesem Abschnitt wird beschrieben, wie Sie die API-Methoden von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] zum Speichern und Abrufen eines XML-Dokuments in bzw. aus einer relationalen Datenbank mit **SQLXML**-Objekten verwenden.  
  
 Außerdem enthält dieser Abschnitt Informationen über die Typen von SQLXML-Objekten und eine Liste wichtiger Richtlinien und Einschränkungen für die Verwendung von SQLXML-Objekten.  
  
## <a name="reading-and-writing-xml-data-with-sqlxml-objects"></a>Lesen und Schreiben von XML-Daten mit SQLXML-Objekten  
 In der folgenden Liste ist aufgeführt, wie Sie die API-Methoden von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] zum Lesen und Schreiben von XML-Daten mit SQLXML-Objekten verwenden:  
  
-   Zum Erstellen eines SQLXML-Objekts verwenden Sie die [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse. Beachten Sie, dass mit dieser Methode ein SQLXML-Objekt ohne Daten erstellt wird. Hinzuzufügende **Xml** Daten in SQLXML-Objekt, rufen Sie eine der folgenden Methoden, die in der SQLXML-Schnittstelle angegeben werden: z. B. SetResult, SetCharacterStream, SetBinaryStream, oder SetString.  
  
-   Zum Abrufen des eigentlichen SQLXML-Objekts verwenden Sie die getSQLXML-Methoden der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse oder der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse.  
  
-   Zum Abrufen der **Xml** Daten aus einem SQLXML-Objekt, verwenden Sie eine der folgenden Methoden, die in der SQLXML-Schnittstelle angegeben werden: GetSource, GetCharacterStream, GetBinaryStream, oder GetString.  
  
-   Zum Aktualisieren der **xml**-Daten in einem SQLXML-Objekt verwenden Sie die [updateSQLXML](../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)-Methode der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse.  
  
-   Zum Speichern eines SQLXML-Objekts in einer Datenbank-Tabellenspalte vom Typ **xml** verwenden Sie die setSQLXML-Methoden der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse oder der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse.  
  
 Der Beispielcode im [Beispiel für den SQLXML-Datentyp](../../connect/jdbc/sqlxml-data-type-sample.md) veranschaulicht die Ausführung dieser allgemeinen API-Aufgaben.  
  
## <a name="readable-and-writable-sqlxml-objects"></a>Lesbare und schreibbare SQLXML-Objekte  
 In der folgenden Tabelle sind die Typen von SQLXML-Objekten aufgeführt, die von den von der JDBC-API bereitgestellten Methoden zum Festlegen, Abrufen und Aktualisieren unterstützt werden. Die Spalten der Tabelle haben die folgende Bedeutung:  
  
-   In der Spalte **Methodenname** werden die unterstützten Methoden zum Abrufen, Festlegen und Aktualisieren in der JDBC-API aufgeführt.  
  
-   Die Spalte **SQLXML-Abrufobjekt** stellt ein SQLXML-Objekt dar, das entweder mit der [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)-Methode der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse oder der [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)-Methode der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse erstellt wird.  
  
-   Die Spalte **SQLXML-Festlegungsobjekt** stellt ein SQLXML-Objekt dar, das von der [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse erstellt wird. Beachten Sie, dass die unten aufgeführten Festlegungsmethoden nur ein von der [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)-Methode erstelltes SQLXML-Objekt akzeptieren.  
  
|Methodenname|SQLXML-Abrufobjekt<br /><br /> (Lesbar)|SQLXML-Festlegungsobjekt<br /><br /> (Schreibbar)|  
|-----------------|-------------------------------------------|-------------------------------------------|  
|CallableStatement.setSQLXML()|Nicht unterstützt|Supported|  
|CallableStatement.setObject()|Nicht unterstützt|Supported|  
|PreparedStatement.setSQLXML()|Nicht unterstützt|Supported|  
|PreparedStatement.setObject()|Nicht unterstützt|Supported|  
|ResultSet.updateSQLXML()|Nicht unterstützt|Supported|  
|ResultSet.updateObject()|Nicht unterstützt|Supported|  
|ResultSet.getSQLXML()|Supported|Nicht unterstützt|  
|CallableStatement.getSQLXML()|Supported|Nicht unterstützt|  
  
 Wie in der Tabelle oben angegeben ist, können die SQLXML-Festlegungsmethoden nicht mit den lesbaren SQLXML-Objekten verwendet werden. Entsprechend können die Abrufmethoden nicht mit den schreibbaren SQLXML-Objekten verwendet werden.  
  
 Wenn die setObject-Methode von der Anwendung durch Angeben eines Skalierungs- oder Längenparameters mit einem SQLXML-Objekt aufgerufen wird, wird der Skalierungs- oder Längenparameter ignoriert.  
  
## <a name="guidelines-and-limitations-when-using-sqlxml-objects"></a>Richtlinien und Einschränkungen für die Verwendung von SQLXML-Objekten  
 Anwendungen können mit SQLXML-Objekten XML-Daten aus einer Datenbank lesen oder in diese schreiben. Die folgende Liste enthält Informationen über bestimmte Einschränkungen und Richtlinien für die Verwendung von SQLXML-Objekten.  
  
-   Ein SQLXML-Objekt kann nur für die Dauer der Transaktion gültig sein, für die es erstellt wurde.  
  
-   Ein von einer Abrufmethode empfangenes SQLXML-Objekt kann nur zum Lesen von Daten verwendet werden.  
  
-   Ein vom Verbindungsobjekt erstelltes SQLXML-Objekt kann nur zum Schreiben von Daten verwendet werden.  
  
-   Die Anwendung kann zum Lesen von Daten nur eine Abrufmethode für ein lesbares SQLXML-Objekt aufrufen. Nach dem Aufruf der Abrufmethode führen alle weiteren Abruf- oder Festlegungsmethoden für das gleiche SQLXML-Objekt zu einem Fehler.  
  
-   Die Anwendung kann nur die free-Methode für das SQLXML-Objekt aufrufen, nachdem für dieses ein Lese- oder Schreibvorgang ausgeführt wurde. Es ist jedoch weiterhin möglich, den zurückgegebenen Datenstrom oder die zurückgegebene Quelle zu verarbeiten, solange die zugrunde liegende Spalte oder der zugrunde liegende Parameter aktiv ist. Wenn die zugrunde liegende Spalte oder der zugrunde liegende Parameter nicht mehr aktiv ist, wird der Datenstrom oder die Quelle geschlossen, der bzw. die dem SQLXML-Objekt zugeordnet ist. Wenn die zugrunde liegende Spalte oder der zugrunde liegende Parameter nicht mehr gültig ist, stehen die zugrunde liegenden Daten den Abrufmethoden des Datenstroms, der SAX (Simple API for XML) und der StAX (Streaming API for XML) nicht zur Verfügung.  
  
-   Die Anwendung kann nur eine Festlegungsmethode für ein schreibbares SQLXML-Objekt aufrufen. Nach dem Aufruf der Festlegungsmethode führen alle weiteren Abruf- oder Festlegungsmethoden für das gleiche SQLXML-Objekt zu einem Fehler.  
  
-   Damit Daten für das SQLXML-Objekt festgelegt werden können, muss die Anwendung die entsprechende Festlegungsmethode und die Funktionen im zurückgegebenen Objekt verwenden.  
  
-   Die getSQLXML-Methoden der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse und der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse geben **null**-Daten zurück, wenn die zugrunde liegende Spalte **null** ist.  
  
-   Die Festlegungsobjekte können für die Dauer der Verbindung gültig sein, in der sie erstellt wurden.  
  
-   Es ist nicht zulässig, dass Anwendungen mithilfe der von der SQLXML-Schnittstelle bereitgestellten Festlegungsmethoden einen **null**-Wert festlegen. Die Anwendungen können mithilfe der von der SQLXML-Schnittstelle bereitgestellten Festlegungsmethoden eine leere Zeichenfolge ("") festlegen. Zum Festlegen eines **null**-Werts müssen die Anwendungen eine der folgenden Methoden aufrufen:  
  
    -   Die setNull-Methoden der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse und der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse.  
  
    -   Die setObject-Methoden der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse und der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse.  
  
    -   Die setSQLXML-Methoden der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse und der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse mit einem **null**-Parameterwert.  
  
-   Für die Arbeit mit XML-Dokumenten wird aus Leistungsgründen die Verwendung der SAX (Simple API for XML)- und StAX (Streaming API for XML)-Parser anstelle von DOM (Document Object Model)-Parsern empfohlen.  
  
 XML-Parser können leere Werte nicht behandeln. SQL Server erlaubt Anwendungen jedoch das Abrufen und Speichern leerer Werte aus bzw. in Datenbankspalten mit dem XML-Datentyp. Dies bedeutet, dass beim Analysieren der XML-Daten vom Parser eine Ausnahme ausgelöst wird, wenn der zugrunde liegende Wert leer ist. Bei DOM-Ausgaben fängt der JDBC-Treiber die Ausnahme ab und löst einen Fehler aus. Bei SAX- und StAX-Ausgaben stammt der Fehler direkt vom Parser.  
  
## <a name="adaptive-buffering-and-sqlxml-support"></a>Adaptive Pufferung und SQLXML-Unterstützung  
 Die vom SQLXML-Objekt zurückgegebenen Binär- und Zeichendatenströme richten sich nach den Modi für die adaptive oder vollständige Pufferung. Wenn die XML-Parser hingegen keine Datenströme sind, berücksichtigen sie die Einstellungen für adaptive oder vollständige Pufferung nicht. Weitere Informationen zur adaptiven Pufferung finden Sie unter [Using Adaptive Buffering](../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Unterstützen von XML-Daten](../../connect/jdbc/supporting-xml-data.md)  
  
  
