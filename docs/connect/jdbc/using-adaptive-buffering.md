---
title: Verwenden der adaptiven Pufferung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 92d4e3be-c3e9-4732-9a60-b57f4d0f7cb7
caps.latest.revision: 53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0a4d3409d9d87bfaca810405e542130a90a471b
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787020"
---
# <a name="using-adaptive-buffering"></a>Verwenden der adaptiven Pufferung

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Mit der adaptiven Pufferung können Daten mit großen Werten ohne den Aufwand von Servercursorn abgerufen werden. In Anwendungen kann die Funktion der adaptiven Pufferung mit allen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden, die vom Treiber unterstützt werden.

Wenn [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] eine Abfrage ausführt, ruft der Treiber normalerweise alle Ergebnisse vom Server in einen Anwendungsspeicher ab. Obwohl bei diesem Ansatz die Ressourcenauslastung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reduziert wird, kann ein OutOfMemoryError in der JDBC-Anwendung für die Abfragen ausgelöst werden, bei denen sehr große Ergebnisse zurückgegeben werden.

Damit Anwendungen sehr große Ergebnisse behandeln können, stellt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die adaptive Pufferung bereit. Mithilfe der adaptiven Pufferung ruft der Treiber Ergebnisse der Anweisungsausführung erst dann von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab, wenn sie in der Anwendung benötigt werden, statt alle Ergebnisse auf einmal abzurufen. Der Treiber verwirft außerdem die Ergebnisse, sobald die Anwendung nicht mehr auf sie zugreifen kann. Im Folgenden werden einige Szenarien beschrieben, in denen die Verwendung der adaptiven Pufferung sinnvoll sein kann:

- **Die Abfrage erzeugt ein sehr umfangreiches Resultset:** die Anwendung kann eine SELECT-Anweisung, die mehr Zeilen als die Anwendung im Arbeitsspeicher speichern kann erzeugt ausführen. In vorherigen Releases musste die Anwendung einen Servercursor verwenden, um einen OutOfMemoryError zu vermeiden. Die adaptive Pufferung stellt die Möglichkeit bereit, ein beliebig großes Resultset mit Vorwärtscursor und schreibgeschützt zu übergeben, ohne dass ein Servercursor erforderlich ist.

- **Die Abfrage erzeugt sehr umfangreiche** [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) **Spalten oder** [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) **OUT-Parameterwerte:** Die Anwendung kann einen einzelnen Wert abrufen (Spalte oder OUT-Parameter) ist zu groß, um vollständig im Anwendungsspeicher gespeichert. Adaptive Pufferung kann die Clientanwendung solche Werte als Datenstrom abrufen, indem Sie mit der GetAsciiStream, die GetBinaryStream- oder die GetCharacterStream-Methoden. Die Anwendung ruft den Wert beim Lesen des Datenstroms von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab.

> [!NOTE]  
> Mit adaptiver Pufferung puffert der JDBC-Treiber nur die benötigte Datenmenge. Der Treiber stellt keine öffentliche Methode zum Steuern oder Beschränken der Puffergröße bereit.

## <a name="setting-adaptive-buffering"></a>Festlegen der adaptiven Pufferung

Ab Version 2.0 des JDBC-Treibers ist das Standardverhalten des Treibers **adaptiv**. Dies bedeutet, um das Verhalten der adaptiven Pufferung zu verwenden, muss das Verhalten der adaptiven Pufferung in der Anwendung nicht explizit angefordert werden. In Release 1.2 lautete der Puffermodus jedoch standardmäßig **vollständig**, und die Anwendung musste den Modus für die adaptive Pufferung explizit anfordern.

Es gibt drei Möglichkeiten, mit denen eine Anwendung die Verwendung der adaptiven Pufferung für die Anweisungsausführung anfordern kann:

- Die Anwendung kann die Verbindungseigenschaft festlegen **ResponseBuffering** auf "adaptive". Weitere Informationen zum Festlegen der Verbindungseigenschaften finden Sie unter [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).

- Die Anwendung kann die [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)-Methode des [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekts zum Festlegen des Antwortpufferungsmodus für alle Verbindungen verwenden, die mit diesem [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt erstellt wurden.

- Die Anwendung kann die [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse verwenden, um den Antwortpuffermodus für ein bestimmtes Anweisungsobjekt festzulegen.

Bei Verwendung von JDBC Driver, Version 1.2, mussten Anwendungen das Anweisungsobjekt in [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) umwandeln, um die [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode zu verwenden. Die Codebeispiele in der [lesen großer Data Sample](../../connect/jdbc/reading-large-data-sample.md) und [lesen großer Datenmengen mit gespeicherten Prozeduren Beispiel](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md) veranschaulichen diese frühere Verwendungsweise.

Mit Version 2.0 des JDBC-Treibers können Anwendungen jedoch die [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)-Methode und die [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)-Methode verwenden, um auf die herstellerspezifischen Funktionen zuzugreifen, ohne Vermutungen über die Klassenhierarchie der Implementierung anstellen zu müssen. Beispielcode, finden Sie unter den [Aktualisieren großer Datenbeispiel](../../connect/jdbc/updating-large-data-sample.md) Thema.

## <a name="retrieving-large-data-with-adaptive-buffering"></a>Abrufen umfangreicher Daten mit adaptiver Pufferung

Wenn große Werte einmal mithilfe der get\<Typ>Stream-Methoden gelesen werden und auf die ResultSet-Spalten und die CallableStatement-OUT-Parameter in der Reihenfolge zugegriffen wird, in der sie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegeben werden, minimiert die adaptive Pufferung die Anwendungsspeicherauslastung beim Verarbeiten der Ergebnisse. Beim Verwenden der adaptiven Pufferung:

- Die in der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse und der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse definierten get\<Type>Stream-Methoden geben schreibgeschützte Datenströme zurück, die zurückgesetzt werden können, wenn sie von der Anwendung gekennzeichnet werden. Wenn in der Anwendung `reset` für den Datenstrom ausgeführt werden soll, muss zunächst die `mark`-Methode für diesen Datenstrom aufgerufen werden.

- Die in der [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md)-Klasse und der [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md)-Klasse definierten get\<Type>Stream-Methoden geben Datenströme zurück, die immer wieder an der Anfangsposition des Datenstroms positioniert werden können, ohne die `mark`-Methode aufzurufen.

Wenn die Anwendung adaptive Pufferung verwendet, können die von den get\<Type>Stream-Methoden abgerufenen Werte nur einmal abgerufen werden. Wenn Sie versuchen, eine get\<Type>-Methode für die gleiche Spalte oder den gleichen Parameter aufzurufen, nachdem die get\<Type>Stream-Methode des gleichen Objekts aufgerufen wurde, wird eine Ausnahme mit der folgenden Meldung ausgelöst: „Auf die Daten wurde zugegriffen; sie sind für diese Spalte oder diesen Parameter nicht verfügbar.“

> [!NOTE]
> Ein Aufruf von ResultSet.close() während der Verarbeitung ein ResultSet benötigt den Microsoft JDBC-Treiber für SQL Server zu lesen und alle übrigen Pakete verworfen. Dies kann einige Zeit dauern, wenn die Abfrage ein großes Dataset zurückgegeben, und insbesondere dann, wenn die Netzwerkverbindung langsam ist.

## <a name="guidelines-for-using-adaptive-buffering"></a>Richtlinien für die Verwendung der adaptiven Pufferung

Entwickler sollten sich an diese wichtigen Richtlinien halten, um die Speicherauslastung durch die Anwendung zu minimieren:

- Vermeiden Sie die Verwendung der Verbindungszeichenfolgeneigenschaft **selectMethod=cursor**, damit die Anwendung ein sehr großes Resultset verarbeiten kann. Die adaptive Pufferung ermöglicht Anwendungen, sehr große, schreibgeschützte Vorwärtsresultsets ohne die Verwendung eines Servercursors zu verarbeiten. Beachten Sie, dass das Festlegen von **selectMethod=cursor** sich auf alle schreibgeschützten Resultsets mit Vorwärtscursor auswirkt, die über diese Verbindung generiert werden. Das heißt, wenn die Anwendung wiederholt kleine Resultsets mit wenigen Zeilen verarbeitet, werden zum Erstellen, Lesen und Schließen eines Servercursors für jedes Resultset sowohl auf Clientseite als auch auf Serverseite mehr Ressourcen verwendet als bei der **selectMethod**, die auf einen anderen Wert als **cursor** festgelegt ist.

- Lesen Sie große Text- oder Binärwerte als Datenströme mithilfe von die GetAsciiStream, die GetBinaryStream oder die GetCharacterStream-Methoden anstelle der GetBlob oder die GetClob Methoden. Ab Release 1.2 stellt die [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse neue get\<Type>Stream-Methoden hierfür bereit.

- Stellen Sie sicher, dass Spalten mit potenziell großen Werten in der Liste der Spalten in einer SELECT-Anweisung am Ende platziert werden und dass die get\<Type>Stream-Methoden von [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) verwendet werden, um in der Reihenfolge auf die Spalten zuzugreifen, in der sie ausgewählt werden.

- Stellen Sie sicher, dass OUT-Parameter mit potenziell großen Werten in der Liste der Parameter im SQL zum Erstellen von [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) zuletzt deklariert werden. Stellen Sie außerdem sicher, dass die get\<Type>Stream-Methoden von [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) verwendet werden, um auf die OUT-Parameter in der Reihenfolge zuzugreifen, in der sie deklariert wurden.

- Vermeiden Sie, gleichzeitig mehrere Anweisungen über die gleiche Verbindung auszuführen. Das Ausführen einer weiteren Anweisung vor dem Verarbeiten der Ergebnisse der vorhergehenden Anweisung kann dazu führen, dass nicht verarbeitete Ergebnisse im Anwendungsspeicher gepuffert werden.

- Es gibt einige Fälle, das bei Verwendung **SelectMethod = Cursor** anstelle von **ResponseBuffering = adaptive** Vorteile, z. B.:

  - Wenn Ihre Anwendung eine vorwärts gerichtete verarbeitet, nur-Lese Resultset langsam, z. B. beim Lesen jeder Zeile nach einer Benutzereingabe, mithilfe von **SelectMethod = Cursor** anstelle von **ResponseBuffering = adaptive** möglicherweise Verringern der Nutzung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

  - Wenn die Anwendung zwei oder mehr schreibgeschützte Resultsets mit Vorwärtscursor gleichzeitig für die gleiche Verbindung verarbeitet, lässt sich der vom Treiber bei der Verarbeitung dieser Resultsets benötigte Speicher durch **selectMethod=cursor** anstelle von **responseBuffering=adaptive** möglicherweise verringern.

  In beiden Fällen müssen Sie den zusätzlichen Aufwand des Erstellens, Lesens und Schließens der Servercursor berücksichtigen.

Darüber hinaus enthält die folgende Liste einige Empfehlungen für scrollfähige Resultsets und aktualisierbare Resultsets mit Vorwärtscursor:

- Bei scrollfähigen Resultsets liest der Treiber beim Abrufen eines Zeilenblocks immer die von der [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)-Methode des [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts angegebene Anzahl von Zeilen in den Speicher ein, auch bei aktivierter adaptiver Pufferung. Wenn das Scrolling einen OutOfMemoryError verursacht, können Sie die Anzahl der abgerufenen Zeilen verringern, indem Sie die [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)-Methode des [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts aufrufen, um die Abrufgröße auf eine kleinere Zeilenanzahl festzulegen und ggf. sogar auf eine Zeile verringern. Führt dies immer noch zu einem OutOfMemoryError, vermeiden Sie das Einschließen sehr großer Spalten in scrollfähigen Resultsets.

- Bei aktualisierbaren Resultsets mit Vorwärtscursor liest der Treiber beim Abrufen eines Zeilenblocks normalerweise die von der [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)-Methode des [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts angegebene Anzahl von Zeilen in den Speicher ein, auch wenn die adaptive Pufferung für die Verbindung aktiviert ist. Wenn das Aufrufen der [next](../../connect/jdbc/reference/next-method-sqlserverresultset.md)-Methode des [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts einen OutOfMemoryError verursacht, können Sie die Anzahl der abgerufenen Zeilen verringern, indem Sie die [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)-Methode des [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts aufrufen, um die Abrufgröße auf eine kleinere Zeilenanzahl festzulegen und ggf. sogar auf eine Zeile verringern. Sie können auch erzwingen, dass der Treiber keine Zeilen puffert, indem Sie vor dem Ausführen der Anweisung die [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode des [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts mit dem Parameter **adaptiv** aufrufen. Da das Resultset nicht scrollfähig ist, verwirft der Treiber einen großen Spaltenwert, auf den die Anwendung mit einer der get\<Type>Stream-Methoden zugreift, wie bei schreibgeschützten Resultsets mit Vorwärtscursor, sobald er von der Anwendung gelesen wurde.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
