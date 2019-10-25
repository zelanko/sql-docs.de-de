---
title: Momentaufnahmenisolation in SQL Server
description: Beschreibt die Unterstützung für die Momentaufnahme Isolation, einen Mechanismus zur Zeilen Versionsverwaltung, der zum Reduzieren der Blockierung in Transaktions Anwendungen entworfen wurde.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 8ef462246d35694ba9bf38954ca8c58635e44e7f
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452080"
---
# <a name="snapshot-isolation-in-sql-server"></a>Momentaufnahmenisolation in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Die Momentaufnahme Isolation verbessert die Parallelität für OLTP-Anwendungen.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Grundlegendes zur Snapshot-Isolation und Zeilen Versionsverwaltung  
Nach dem Aktivieren der Snapshot-Isolation werden aktuelle Zeilenversionen für jede Transaktion in **tempdb** beibehalten. Jede Transaktion wird durch eine eindeutige Transaktions Sequenznummer identifiziert, und diese eindeutigen Zahlen werden für jede Zeilen Version aufgezeichnet. Die Transaktion funktioniert mit den neuesten Zeilen Versionen mit einer Sequenznummer vor der Sequenznummer der Transaktion. Neuere Zeilen Versionen, die nach Beginn der Transaktion erstellt wurden, werden von der Transaktion ignoriert.  
  
Der Begriff "Momentaufnahme" gibt die Tatsache wieder, dass alle Abfragen in der Transaktion auf der Grundlage des Zustands der Datenbank zu dem Zeitpunkt, zu dem die Transaktion beginnt, dieselbe Version bzw. Momentaufnahme der Datenbank sehen. Es werden keine Sperren für die zugrunde liegenden Daten Zeilen oder Datenseiten in einer Momentaufnahme Transaktion abgerufen, sodass andere Transaktionen ausgeführt werden können, ohne dass eine vorherige inabgeschlossene Transaktion blockiert wird. Transaktionen, die Daten ändern, blockieren keine Transaktionen, die Daten lesen, und Transaktionen, die Daten lesen, blockieren keine Transaktionen, die Daten schreiben, da Sie normalerweise unter der standardmäßigen Read-Commit-Isolationsstufe in SQL Server. Dieses nicht blockierende Verhalten verringert auch beträchtlich die Wahrscheinlichkeit für Deadlocks bei komplexen Transaktionen.  
  
Die Momentaufnahme Isolation verwendet ein optimistisches Parallelitäts Modell. Wenn eine Momentaufnahme Transaktion versucht, Änderungen an Daten zu übertragen, die seit Beginn der Transaktion geändert wurden, wird für die Transaktion ein Rollback ausgeführt, und es wird ein Fehler ausgelöst. Sie können dies vermeiden, indem Sie UPDLOCK-Hinweise für SELECT-Anweisungen verwenden, die auf zu ändernde Daten zugreifen. Weitere Informationen finden Sie unter "Sperr Hinweise" in SQL Server-Onlinedokumentation.  
  
Die Momentaufnahme Isolation muss aktiviert werden, indem die ALLOW_SNAPSHOT_ISOLATION on Database-Option festgelegt wird, bevor Sie in Transaktionen verwendet wird. Dadurch wird der Mechanismus zum Speichern von Zeilenversionen in der temporären Datenbank (**tempdb**) aktiviert. Sie müssen die Momentaufnahme Isolation in jeder Datenbank aktivieren, die Sie mit der Transact-SQL-Anweisung ALTER DATABASE verwendet. In dieser Hinsicht unterscheidet sich die Momentaufnahmenisolation von den herkömmlichen Isolations Stufen Read Commit, Repeatable Read, serialisierbar und Read uncommit, die keine Konfiguration erfordern. Mit den folgenden Anweisungen wird die Momentaufnahme Isolation aktiviert und das Standardverhalten für Lesevorgänge durch die Momentaufnahme ersetzt:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
Wenn Sie die Option READ_COMMITTED_SNAPSHOT on festlegen, wird der Zugriff auf versionierte Zeilen unter der Standard Isolationsstufe Read zugesichert ermöglicht. Wenn die READ_COMMITTED_SNAPSHOT-Option auf OFF festgelegt ist, müssen Sie die Momentaufnahme Isolationsstufe für jede Sitzung explizit festlegen, um auf versionierte Zeilen zugreifen zu können.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Verwalten von Parallelität mit Isolations Stufen  
Die Isolationsstufe, unter der eine Transact-SQL-Anweisung ausgeführt wird, bestimmt das Sperr-und Zeilen Versions Verwaltungsverhalten. Eine Isolationsstufe weist einen Verbindungs weiten Bereich auf, und sobald Sie für eine Verbindung mit der SET TRANSACTION ISOLATION LEVEL-Anweisung festgelegt wurde, bleibt Sie so lange in Kraft, bis die Verbindung geschlossen oder eine andere Isolationsstufe festgelegt ist. Wenn eine Verbindung geschlossen und an den Pool zurückgegeben wird, wird die Isolationsstufe der letzten SET TRANSACTION ISOLATION LEVEL-Anweisung beibehalten. Bei nachfolgenden Verbindungen, die eine gepoolte Verbindung wieder verwenden, wird die Isolationsstufe verwendet, die zum Zeitpunkt der Verbindungs Herstellung der Verbindung wirksam war.  
  
Einzelne Abfragen, die innerhalb einer Verbindung ausgegeben werden, können Sperr Hinweise enthalten, die die Isolation für eine einzelne Anweisung oder Transaktion ändern, aber nicht die Isolationsstufe der Verbindung beeinflussen. Isolations Stufen oder Sperr Hinweise, die in gespeicherten Prozeduren oder Funktionen festgelegt wurden, ändern nicht die Isolationsstufe der Verbindung, die diese aufruft und nur für die Dauer der gespeicherten Prozedur oder des Funktionsaufrufs wirksam sind.  
  
In frühen Versionen von SQL Server wurden vier Isolations Stufen unterstützt, die im SQL-92-Standard definiert sind:  
  
- Read uncommit ist die am wenigsten einschränkende Isolationsstufe, da Sie von anderen Transaktionen belegte Sperren ignoriert. Transaktionen, die unter Read nicht Commit ausgeführt werden, können geänderte Datenwerte lesen, die noch nicht von anderen Transaktionen committet wurden. Diese werden als "Dirty"-Lesevorgänge bezeichnet.  
  
- Die Standardisolationsstufe für SQL Server ist READ COMMITTED. Er verhindert Dirty Reads, indem er angibt, dass-Anweisungen keine Datenwerte lesen können, die geändert wurden, für die jedoch noch kein Commit von anderen Transaktionen ausgeführt wurde Andere Transaktionen können weiterhin Daten zwischen Ausführungen einzelner Anweisungen innerhalb der aktuellen Transaktion ändern, einfügen oder löschen, was zu nicht wiederholbaren Lesevorgängen oder "Phantom"-Daten führt.  
  
- Wiederholbarer Lesevorgang ist eine restriktivere Isolationsstufe als Lese Commit. Er umfasst den Lese Commit und gibt zusätzlich an, dass keine anderen Transaktionen Daten ändern oder löschen können, die von der aktuellen Transaktion gelesen wurden, bis die aktuelle Transaktion einen Commit ausführt. Die Parallelität ist geringer als bei einem Lese Commit, da freigegebene Sperren für Lesedaten für die Dauer der Transaktion aufrechterhalten werden, anstatt am Ende jeder Anweisung freigegeben zu werden.  
  
- SERIALIZABLE ist die restriktivste Isolationsstufe, da gesamte Schlüsselbereiche gesperrt werden, und die Sperren bis zum Abschluss der Transaktion aufrechterhalten werden. Er umfasst wiederholbare Lesevorgänge und fügt die Einschränkung hinzu, dass andere Transaktionen keine neuen Zeilen in Bereiche einfügen können, die von der Transaktion gelesen wurden, bis die Transaktion abgeschlossen ist.  
  
Weitere Informationen finden Sie im [Handbuch zu Transaktionssperren und Zeilenversionsverwaltung](../../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md).  
  
### <a name="snapshot-isolation-level-extensions"></a>Erweiterungen für Snapshot-Isolations Stufen  
SQL Server hat Erweiterungen für die SQL-92-Isolationsgrade eingeführt, zu denen der SNAPSHOT-Isolationsgrad und eine zusätzliche Implementierung von READ COMMITTED gehört. Der READ_COMMITTED_SNAPSHOT-Isolationsgrad kann auf transparente Weise READ COMMITTED für alle Transaktionen ersetzen.  
  
- Die Momentaufnahme Isolation gibt an, dass in einer Transaktion gelesene Daten niemals von anderen gleichzeitigen Transaktionen vorgenommene Änderungen widerspiegeln. Die Transaktion verwendet die Daten Zeilen Versionen, die beim Beginn der Transaktion vorhanden sind. Wenn Sie gelesen werden, werden keine Sperren für die Daten platziert, sodass keine Daten vom Schreiben von Daten durch andere Transaktionen blockiert werden. Transaktionen, die Daten schreiben, halten SNAPSHOT-Transaktionen nicht vom Lesen von Daten ab. Sie müssen die Momentaufnahme Isolation aktivieren, indem Sie die ALLOW_SNAPSHOT_ISOLATION-Datenbankoption festlegen, um Sie zu verwenden.  
  
- Die READ_COMMITTED_SNAPSHOT-Datenbankoption bestimmt das Verhalten der Standard Isolationsstufe "Read-Commit", wenn die Momentaufnahme Isolation in einer Datenbank aktiviert ist. Wenn Sie READ_COMMITTED_SNAPSHOT on nicht explizit angeben, wird Read Commit auf alle impliziten Transaktionen angewendet. Dies führt zum gleichen Verhalten wie das Festlegen von READ_COMMITTED_SNAPSHOT Off (Standard). Wenn READ_COMMITTED_SNAPSHOT OFF aktiviert ist, verwendet die Datenbank-Engine freigegebene Sperren, um die Standard Isolationsstufe zu erzwingen. Wenn Sie die READ_COMMITTED_SNAPSHOT-Datenbankoption auf on festlegen, verwendet die Datenbank-Engine die Zeilen Versionsverwaltung und die Momentaufnahme Isolation als Standard, anstatt Sperren zum Schutz der Daten zu verwenden.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Funktionsweise der Momentaufnahme Isolation und der Zeilen Versionsverwaltung  
Wenn die SNAPSHOT-Isolationsstufe aktiviert ist, speichert die SQL Server-Datenbank-Engine bei jedem Aktualisieren einer Zeile eine Kopie der Ursprungszeile in **tempdb** und fügt der Zeile eine Transaktionsfolgenummer hinzu. Im folgenden wird die Abfolge der Ereignisse aufgeführt, die auftreten:  
  
1. Eine neue Transaktion wird initiiert, und ihr wird eine Transaktions Sequenznummer zugewiesen.  
  
2. Die Datenbank-Engine liest eine Zeile innerhalb der Transaktion und ruft die Zeilenversion von **tempdb** ab, deren Nummer kleiner ist als die Transaktionsfolgenummer und gleichzeitig am nächsten bei dieser liegt.  
  
3. Der Datenbank-Engine überprüft, ob die Transaktions Sequenznummer nicht in der Liste der Transaktions Sequenznummern der Transaktionen enthalten ist, für die kein Commit ausgeführt wurde, die beim Starten der Momentaufnahme Transaktion aktiv waren.  
  
4. Die Transaktion liest in **tempdb** die Version der Zeile, die beim Start der Transaktion aktuell war. Es werden keine neuen Zeilen angezeigt, die nach dem Start der Transaktion eingefügt wurden, da diese Werte der Sequenznummer höher als der Wert der Transaktions Sequenznummer sein werden.  
  
5. Die aktuelle Transaktion erfasst Zeilen, die nach dem Start der Transaktion gelöscht wurden, weil in **tempdb** eine Zeilenversion mit niedrigerem Folgenummernwert vorhanden ist.  
  
Der Effekt der Snapshot-Isolation besteht darin, dass die Transaktion alle Daten so sieht, wie Sie zu Beginn der Transaktion vorhanden waren, ohne dass die zugrunde liegenden Tabellen gesperrt werden. Dies kann zu Leistungsverbesserungen in Situationen führen, in denen Konflikte auftreten.  
  
Eine Momentaufnahme Transaktion verwendet immer die Steuerung der vollständigen Parallelität und sperrt alle Sperren, die verhindern, dass andere Transaktionen Zeilen aktualisieren. Wenn eine Momentaufnahme Transaktion versucht, ein Update für eine Zeile zu committen, die nach Beginn der Transaktion geändert wurde, wird ein Rollback für die Transaktion ausgeführt, und es wird ein Fehler ausgelöst.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Arbeiten mit der Momentaufnahme Isolation in ADO.net  
Die Momentaufnahme Isolation wird in ADO.net von der <xref:Microsoft.Data.SqlClient.SqlTransaction>-Klasse unterstützt. Wenn eine Datenbank für die Snapshot-Isolation aktiviert, aber nicht für READ_COMMITTED_SNAPSHOT ON konfiguriert wurde, müssen Sie eine <xref:Microsoft.Data.SqlClient.SqlTransaction> mit dem **IsolationLevel.Snapshot**-Enumerationswert initiieren, wenn Sie die <xref:Microsoft.Data.SqlClient.SqlConnection.BeginTransaction%2A>-Methode aufrufen. Dieses Code Fragment geht davon aus, dass die Verbindung ein offenes <xref:Microsoft.Data.SqlClient.SqlConnection> Objekt ist.  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Beispiel  
Im folgenden Beispiel wird veranschaulicht, wie sich die verschiedenen Isolations Stufen Verhalten, indem versucht wird, auf gesperrte Daten zuzugreifen, und nicht für die Verwendung im Produktionscode vorgesehen ist.  
  
Der Code stellt eine Verbindung mit der **AdventureWorks**-Beispieldatenbank in SQL Server her, erstellt die Tabelle **TestSnapshot** und fügt eine Datenzeile ein. Der Code verwendet die ALTER DATABASE-Transact-SQL-Anweisung, um die Momentaufnahme Isolation für die Datenbank zu aktivieren, aber die READ_COMMITTED_SNAPSHOT-Option wird nicht festgelegt, sodass das Standardverhalten von Read-Commit auf Isolations Ebene wirksam wird. Der Code führt dann die folgenden Aktionen aus:  
  
1. Es beginnt, aber nicht abgeschlossen, sqlTransaction1, das die serialisierbare Isolationsstufe verwendet, um eine Update Transaktion zu starten. Dies hat Auswirkungen auf das Sperren der Tabelle.  
  
2. Der Code öffnet eine zweite Verbindung und initiiert eine zweite Transaktion mit der SNAPSHOT-Isolationsstufe zum Lesen der Daten in der **TestSnapshot**-Tabelle. Da die Momentaufnahme Isolation aktiviert ist, kann diese Transaktion die Daten lesen, die vor dem Start von sqlTransaction1 vorhanden waren.  
  
3. Er öffnet eine dritte Verbindung und initiiert eine Transaktion mithilfe der Isolationsstufe Read Commit, um zu versuchen, die Daten in der Tabelle zu lesen. In diesem Fall kann der Code die Daten nicht lesen, weil er nicht über die Sperren hinweg lesen kann, die in der ersten Transaktion für die Tabelle platziert wurden, und löst eine Zeitüberschreitung aus. Das gleiche Ergebnis tritt auch bei den Isolationsstufen REPEATABLE READ und SERIALIZABLE auf, weil diese Isolationsstufen ebenfalls nicht über die in der ersten Transaktion platzierten Sperren hinweg lesen können.  
  
4. Er öffnet eine vierte Verbindung und initiiert eine Transaktion mit der Isolationsstufe Read ohne Commit, bei der eine Dirty Read des Werts ohne Commit in sqlTransaction1 ausgeführt wird. Dieser Wert ist möglicherweise nie tatsächlich in der Datenbank vorhanden, wenn für die erste Transaktion kein Commit ausgeführt wird.  
  
5. Der Code nimmt die erste Transaktion zurück und führt eine Bereinigung durch, indem er die **TestSnapshot**-Tabelle löscht und die Snapshot-Isolation für die **AdventureWorks**-Datenbank deaktiviert.  
  
> [!NOTE]
>  In den folgenden Beispielen wird dieselbe Verbindungs Zeichenfolge verwendet, bei der das Verbindungspooling deaktiviert wurde. Wenn eine Verbindung in einem Pool zusammengefasst wird, wird die Isolationsstufe beim Zurücksetzen der Isolationsstufe auf dem Server nicht zurückgesetzt. Folglich beginnen nachfolgende Verbindungen, die dieselbe in einem Pool zusammengefasste innere Verbindung verwenden, mit den Isolations Stufen, die auf die der gepoolten Verbindung festgelegt sind. Eine Alternative zum Ausschalten des Verbindungspooling besteht darin, die Isolationsstufe für jede Verbindung explizit festzulegen.  
  
[!code-csharp[DataWorks Isolation_Snapshot.Demo#1](~/../sqlclient/doc/samples/Isolation_Snapshot.cs#1)]
  
### <a name="example"></a>Beispiel  
Im folgenden Beispiel wird das Verhalten der Snapshot-Isolation bei der Änderung von Daten veranschaulicht. Der Code führt die folgenden Aktionen aus:  
  
1. Herstellen einer Verbindung mit der **AdventureWorks**-Beispieldatenbank und Aktivieren der SNAPSHOT-Isolation.  
  
2. Erstellen der Tabelle **TestSnapshotUpdate** und Einfügen von drei Zeilen mit Beispieldaten.  
  
3. "SqlTransaction1" wird mit der Momentaufnahme Isolation gestartet, aber nicht vervollständigt. In der Transaktion sind drei Daten Zeilen ausgewählt.  
  
4. Erstellt eine zweite **SqlConnection** mit **AdventureWorks** und erstellt eine zweite Transaktion mit der READ COMMITTED-Isolationsstufe, die einen Wert in einer der in sqlTransaction1 ausgewählten Zeilen aktualisiert.  
  
5. Commits sqlTransaction2.  
  
6. Kehrt zu sqlTransaction1 zurück und versucht, dieselbe Zeile zu aktualisieren, für die sqlTransaction1 bereits ein Commit ausgeführt wurde. Der Fehler 3960 wird ausgelöst, und für sqlTransaction1 wird automatisch ein Rollback ausgeführt. Im Konsolenfenster werden die **SqlException.Number** und die **SqlException.Message** angezeigt.  
  
7. Führt Bereinigungscode aus, um die Snapshot-Isolation in **AdventureWorks** zu deaktivieren und die **TestSnapshotUpdate**-Tabelle zu löschen.  
  
    [!code-csharp[DataWorks Isolation_Snapshot1#1](~/../sqlclient/doc/samples/Isolation_Snapshot1.cs#1)]
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Verwenden von Sperr hinweisen mit Snapshot-Isolation  
Im vorherigen Beispiel wählt die erste Transaktion Daten aus, und eine zweite Transaktion aktualisiert die Daten, bevor die erste Transaktion abgeschlossen werden kann. Dies führt zu einem Update Konflikt, wenn die erste Transaktion versucht, dieselbe Zeile zu aktualisieren. Sie können die Wahrscheinlichkeit von Update Konflikten in Momentaufnahme Transaktionen mit langer Ausführungszeit verringern, indem Sie am Anfang der Transaktion Sperr Hinweise bereitstellen. Die folgende SELECT-Anweisung verwendet den UPDLOCK-Hinweis zum Sperren der ausgewählten Zeilen:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
Mithilfe des UPDLOCK-Sperr Hinweises werden alle Zeilen blockiert, die versuchen, die Zeilen zu aktualisieren, bevor die erste Transaktion abgeschlossen ist. Dadurch wird sichergestellt, dass die ausgewählten Zeilen keine Konflikte aufweisen, wenn Sie später in der Transaktion aktualisiert werden. Weitere Informationen finden Sie unter "Sperr Hinweise" in SQL Server-Onlinedokumentation.  
  
Wenn Ihre Anwendung viele Konflikte aufweist, ist die Momentaufnahme Isolation möglicherweise nicht die beste Wahl. Hinweise sollten nur verwendet werden, wenn Sie tatsächlich benötigt werden. Die Anwendung sollte nicht so entworfen werden, dass Sie ständig Sperr Hinweise für Ihren Vorgang stützt.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
- [Handbuch zu Transaktionssperren und Zeilenversionsverwaltung](../../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md)
