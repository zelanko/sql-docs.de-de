---
title: Task „SQL ausführen“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- batches [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6be23e1a45f2b2ed0cc055c5032a72ffe2387399
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62831768"
---
# <a name="execute-sql-task"></a>SQL ausführen (Task)
  Mit dem Task SQL ausführen werden SQL-Anweisungen oder gespeicherte Prozeduren aus einem Paket ausgeführt. Dieser Task kann eine oder mehrere SQL-Anweisungen enthalten, die sequenziell ausgeführt werden. Der Task SQL ausführen kann für folgende Zwecke verwendet werden:  
  
-   Abschneiden einer Tabelle oder Sicht, um das Einfügen von Daten vorzubereiten.  
  
-   Erstellen, Ändern und Löschen von Datenbankobjekten, wie z. B. Tabellen und Sichten.  
  
-   Neuerstellen von Fakten- und Dimensionstabellen vor dem Laden von Daten.  
  
-   Ausführen gespeicherter Prozeduren. Wenn Sie mithilfe einer SQL-Anweisung eine gespeicherte Prozedur aufrufen, die Ergebnisse von einer temporären Tabelle zurückgibt, verwenden Sie die WITH RESULT SETS-Option, um Metadaten für das Resultset zu definieren.  
  
-   Speichern des Rowsets, das von einer Abfrage zurückgegeben wird, in einer Variablen.  
  
 Der Task SQL ausführen kann in Kombination mit dem Foreach-Schleifencontainer und dem For-Schleifencontainer verwendet werden, um mehrere SQL-Anweisungen auszuführen. Diese Container implementieren das Wiederholen von Ablaufsteuerungen in einem Paket und können den Task SQL ausführen wiederholt ausführen. Beispielsweise kann ein Paket mithilfe des Foreach-Schleifencontainers Dateien in einem Ordner aufzählen und einen Task SQL ausführen wiederholt ausführen, um die in jeder Datei gespeicherte SQL-Anweisung auszuführen.  
  
## <a name="connecting-to-a-data-source"></a>Herstellen einer Verbindung mit einer Datenquelle  
 Der Task SQL ausführen kann verschiedene Arten von Verbindungs-Managern für die Verbindung mit der Datenquelle verwenden, in der die SQL-Anweisung oder die gespeicherte Prozedur ausgeführt wird. Der Task kann die in der folgenden Tabelle aufgeführten Verbindungstypen verwenden.  
  
|Verbindungstyp|Ziel-Editor für Dimensionsverarbeitung|  
|---------------------|------------------------|  
|EXCEL|[Excel-Verbindungs-Manager](../connection-manager/excel-connection-manager.md)|  
|OLE DB|[OLE DB-Verbindungs-Manager](../connection-manager/ole-db-connection-manager.md)|  
|ODBC|[ODBC-Verbindungs-Manager](../connection-manager/odbc-connection-manager.md)|  
|ADO|[ADO-Verbindungs-Manager](../connection-manager/ado-connection-manager.md)|  
|ADO.NET|[ADO.NET-Verbindungs-Manager](../connection-manager/ado-net-connection-manager.md)|  
|SQLMOBILE|[SQL Server Compact Edition-Verbindungs-Manager](../connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## <a name="creating-sql-statements"></a>Erstellen von SQL-Anweisungen  
 Die Quelle für die SQL-Anweisungen, die von diesem Task verwendet werden, kann eine Taskeigenschaft mit einer Anweisung, eine Verbindung mit einer Datei mit mindestens einer Anweisung oder der Name einer Variablen sein, die eine Anweisung enthält. Die SQL-Anweisungen müssen in dem Dialekt des Quelldatenbank-Managementsystems (DBMS, Database Management System) erstellt werden. Weitere Informationen finden Sie unter [Integration Services-Abfragen &#40;SSIS&#41;](../integration-services-ssis-queries.md).  
  
 Wenn die SQL-Anweisungen in einer Datei gespeichert sind, stellt der Task mithilfe eines Verbindungs-Managers eine Verbindung mit der Datei her. Weitere Informationen finden Sie unter [File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 Im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer können Sie zum Eingeben von SQL-Anweisungen das Dialogfeld **Editor für den Task SQL ausführen** oder den **Abfrage-Generator**verwenden. Dabei handelt es sich um eine grafische Benutzeroberfläche zum Erstellen von SQL-Abfragen. Weitere Informationen finden Sie unter [Editor für den Task „SQL ausführen“ &#40;Seite „Allgemein“&#41;](../execute-sql-task-editor-general-page.md) und [Abfrage-Generator](../query-builder.md).  
  
> [!NOTE]  
>  Gültige SQL-Anweisungen, die außerhalb des Tasks "SQL ausführen" erstellt wurden, werden vom Task "SQL ausführen" möglicherweise nicht erfolgreich analysiert.  
  
> [!NOTE]  
>  Der Task "SQL ausführen" verwendet den `RecognizeAll` ParseMode-Enumerationswert. Weitere Informationen finden Sie unter [ManagedBatchParser-Namespace](https://go.microsoft.com/fwlink/?LinkId=223617).  
  
## <a name="sending-multiple-statements-in-a-batch"></a>Senden mehrerer Anweisungen in einem Batch  
 Wenn Sie für den Task "SQL ausführen" mehrere Anweisungen einschließen, können Sie diese gruppieren und als Batch ausführen. Verwenden Sie den GO-Befehl, um das Ende eines Batches zu signalisieren. Alle SQL-Anweisungen zwischen zwei GO-Befehlen werden als Batch an den OLE DB-Anbieter zum Ausführen gesendet. Der SQL-Befehl kann mehrere durch GO-Befehle getrennte Batches einschließen.  
  
 Bezüglich der SQL-Anweisungen, die als Batch gruppiert werden können, sind Einschränkungen vorhanden. Weitere Informationen finden Sie unter [Batches of Statements](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md).  
  
 Falls der Task SQL ausführen einen Batch mit SQL-Anweisungen ausführt, gelten für den Batch die folgenden Regeln:  
  
-   Nur eine Anweisung kann ein Resultset zurückgeben. Sie muss außerdem die erste Anweisung im Batch sein.  
  
-   Falls das Resultset Ergebnisbindungen verwendet, müssen die Abfragen die gleiche Anzahl von Spalten zurückgeben. Falls die Abfragen eine andere Anzahl von Spalten zurückgeben, wird für den Task ein Fehler gemeldet. Bei einem Fehler des Tasks werden jedoch die von dem Task ausgeführten Abfragen, wie z. B. DELETE- oder INSERT-Abfragen, möglicherweise erfolgreich ausgeführt.  
  
-   Falls für die Ergebnisbindungen Spaltennamen verwendet werden, muss die Abfrage Spalten zurückgeben, die die gleichen Namen wie die vom Task verwendeten Resultsetnamen besitzen. Wenn die Spalten fehlen, wird für den Task ein Fehler gemeldet.  
  
-   Falls für den Task die Parameterbindung verwendet wird, müssen alle Abfragen im Batch die gleiche Anzahl und Art von Parametern aufweisen.  
  
## <a name="running-parameterized-sql-commands"></a>Ausführen parametrisierter SQL-Befehle  
 SQL-Anweisungen und gespeicherte Prozeduren verwenden häufig Eingabeparameter, Ausgabeparameter und Rückgabecodes. Der Task SQL ausführen unterstützt die `Input`-, `Output`- und `ReturnValue`-Parametertypen. Sie können den `Input`-Typ für Eingabeparameter, den `Output`-Typ für Ausgabeparameter und den `ReturnValue`-Typ für Rückgabecodes verwenden.  
  
> [!NOTE]  
>  Parameter können in einem Task SQL ausführen nur verwendet werden, wenn dies vom Datenanbieter unterstützt wird.  
  
 Informationen über die Verwendung von Parametern und Rückgabecodes im Task „SQL ausführen“ finden Sie unter [Parameter und Rückgabecodes im Task „SQL ausführen“](execute-sql-task.md).  
  
## <a name="specifying-a-result-set-type"></a>Angeben eines Resultsettyps  
 Der Typ des SQL-Befehls bestimmt, ob für den Task SQL ausführen ein Resultset zurückgegeben wird. Beispielsweise gibt eine SELECT-Anweisung in der Regel ein Resultset zurück, eine INSERT-Anweisung jedoch nicht. Das Resultset einer SELECT-Anweisung kann keine Zeilen, eine Zeile oder viele Zeilen enthalten. Gespeicherte Prozeduren können außerdem einen ganzzahligen Wert, der als Rückgabecode bezeichnet wird, zurückgeben, um den Ausführungsstatus der Prozedur anzuzeigen. In diesem Fall besteht das Resultset aus einer einzelnen Zeile.  
  
 Informationen über das Abrufen von Resultsets aus SQL-Befehlen im Task „SQL ausführen“ finden Sie unter [Resultsets im Task „SQL ausführen“](../result-sets-in-the-execute-sql-task.md).  
  
## <a name="troubleshooting-the-execute-sql-task"></a>Problembehandlung des Tasks SQL ausführen  
 Sie können die vom Task SQL ausführen an externe Datenanbieter gerichteten Aufrufe protokollieren. Mithilfe dieser Protokollierungsfunktionen können Sie Probleme bei SQL-Befehlen behandeln, die vom Task SQL ausführen ausgeführt werden. Aktivieren Sie zum Protokollieren der vom Task SQL ausführen an externe Datenanbieter gerichteten Aufrufe die Paketprotokollierung, und wählen Sie das **Diagnostic** -Ereignis auf Paketebene aus. Weitere Informationen finden Sie unter [Behandlung von Problemen mit Paketausführungstools](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 Gelegentlich gibt ein SQL-Befehl oder eine gespeicherte Prozedur mehrere Resultsets zurück. Zu diesen Resultsets gehören nicht nur Rowsets, die das Ergebnis von `SELECT`-Abfragen sind, sondern auch einzelne Werte als Ergebnis von Fehlern in der `RAISERROR`-Anweisung oder `PRINT`-Anweisung. Ob der Task Fehler in Resultsets nach dem ersten Resultset ignoriert, hängt vom verwendeten Typ des Verbindungs-Managers ab:  
  
-   Wenn Sie OLE DB- und ADO-Verbindungs-Manager verwenden, ignoriert der Task die Resultsets, die nach dem ersten Resultset auftreten. Das bedeutet, dass der Task bei diesen Verbindungs-Managern einen von einem SQL-Befehl oder einer gespeicherten Prozedur zurückgegebenen Fehler ignoriert, wenn der Fehler nicht Teil des ersten Resultsets ist.  
  
-   Wenn Sie ODBC- und ADO.NET-Verbindungs-Manager verwenden, werden die Resultsets, die nach dem ersten Resultset auftreten, vom Task nicht ignoriert. Bei diesen Verbindungs-Managern erzeugt der Task einen Fehler, wenn ein anderes Resultset als das erste Resultset einen Fehler aufweist.  
  
### <a name="custom-log-entries"></a>Benutzerdefinierte Protokolleinträge  
 In der folgenden Tabelle wird der benutzerdefinierte Protokolleintrag für den Task <legacyBold>SQL ausführen</legacyBold> beschrieben. Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) und [Benutzerdefinierte Meldungen für die Protokollierung](../custom-messages-for-logging.md).  
  
|Protokolleintrag|Description|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|Enthält Informationen zu den Ausführungsphasen der SQL-Anweisung. Protokolleinträge werden geschrieben, wenn der Task eine Verbindung mit der Datenbank erhält, wenn der Task beginnt, die SQL-Anweisung vorzubereiten, und nachdem die Ausführung der SQL-Anweisung abgeschlossen wurde. Der Protokolleintrag für die Vorbereitungsphase schließt die vom Task verwendete SQL-Anweisung ein.|  
  
## <a name="configuring-the-execute-sql-task"></a>Konfigurieren des Tasks SQL ausführen  
 Es gibt folgende Möglichkeiten, um den Task SQL ausführen zu konfigurieren:  
  
-   Geben Sie den Verbindungs-Manager an, der zum Verbinden mit einer Datenbank verwendet werden soll.  
  
-   Geben Sie den Resultsettyp an, der von der SQL-Anweisung zurückgegeben wird.  
  
-   Geben Sie ein Timeout für die SQL-Anweisungen an.  
  
-   Geben Sie die Quelle der SQL-Anweisung an.  
  
-   Geben Sie an, ob der Task die Vorbereitungsphase für die SQL-Anweisung auslässt.  
  
-   Wenn Sie den ADO-Verbindungstyp verwenden, müssen Sie angeben, ob es sich bei der SQL-Anweisung um eine gespeicherte Prozedur handelt. Für andere Verbindungstypen ist diese Eigenschaft schreibgeschützt und weist immer den Wert `false` auf.  
  
 Eigenschaften können Sie programmgesteuert oder mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Editor für den Task SQL ausführen &#40;Seite "Allgemein"&#41;](../execute-sql-task-editor-general-page.md)  
  
-   [Editor für den Task SQL ausführen &#40;Seite Parameterzuordnung&#41;](../execute-sql-task-editor-parameter-mapping-page.md)  
  
-   [Editor für den Task SQL ausführen &#40;Seite Resultset&#41;](../execute-sql-task-editor-result-set-page.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="configuring-the-execute-sql-task-programmatically"></a>Programmgesteuertes Konfigurieren des Tasks SQL ausführen  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften anzuzeigen:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Zuordnen von Abfrageparametern zu Variablen in einem „SQL ausführen“-Task ](../map-query-parameters-to-variables-in-an-execute-sql-task.md)  
  
-   [Zuordnen von Resultsets zu Variablen in einem „SQL ausführen“-Task ](../map-result-sets-to-variables-in-an-execute-sql-task.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Parameter und Rückgabecodes im Task „SQL ausführen“](execute-sql-task.md)  
  
-   [Resultsets im Task „SQL ausführen“](../result-sets-in-the-execute-sql-task.md)  
  
-   [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference)  
  
-   Blogeintrag [Neue Datums- und Uhrzeitfunktionen in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=239783)auf mssqltips.com.  
  
  
