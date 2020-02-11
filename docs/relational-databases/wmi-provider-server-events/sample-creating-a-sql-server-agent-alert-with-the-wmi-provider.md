---
title: Erstellen einer SQL Server-Agent Warnung mit dem WMI-Anbieter
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SQL Server Agent [WMI]
- WMI Provider for Server Events, samples
- sample applications [WMI]
ms.assetid: d44811c7-cd46-4017-b284-c863ca088e8f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b9ceab4fd40174a68bd512fedf2c1b6d5b159b99
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660529"
---
# <a name="sample-creating-a-sql-server-agent-alert-with-the-wmi-provider"></a>Beispiel: Erstellen einer SQL Server-Agent-Warnung mit dem WMI-Anbieter
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Eine gebräuchliche Möglichkeit zum Verwenden des WMI-Ereignisanbieters ist die Erstellung von SQL Server-Agent-Warnungen, die auf bestimmte Ereignisse antworten. Das folgende Beispiel stellt eine einfache Warnung dar, die XML-Deadlockdiagrammereignisse in einer Tabelle zur späteren Analyse speichert. SQL Server-Agent übermittelt eine WQL-Anforderung, empfängt WMI-Ereignisse und führt als Antwort auf das Ereignis einen Auftrag aus. Beachten Sie, dass der WMI-Ereignisanbieter die Details bei der Erstellung und Verwaltung von Service Broker-Objekten behandelt, obwohl mehrere dieser Objekte an der Verarbeitung der Benachrichtigungsmeldung beteiligt sind.  
  
## <a name="example"></a>Beispiel  
 Zuerst wird in der `AdventureWorks`-Datenbank eine Tabelle erstellt, in der das Deadlockdiagrammereignis gespeichert werden soll. Die Tabelle enthält zwei Spalten: Die `AlertTime`-Spalte enthält die Uhrzeit, zu der die Warnung ausgeführt wird, und die `DeadlockGraph`-Spalte enthält das XML-Dokument mit dem Deadlockdiagramm.  
  
 Anschließend wird die Warnung erstellt. Das Skript erstellt zunächst den Auftrag zur Ausführung der Warnung, fügt dem Auftrag einen Auftragsschritt hinzu und weist den Auftrag der aktuellen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu. Das Skript erstellt dann die Warnung.  
  
 Der Auftrags Schritt ruft die **TextData** -Eigenschaft der WMI-Ereignis Instanz ab und fügt diesen Wert in die **DeadlockGraph** -Spalte der **DeadlockEvents** -Tabelle ein. Beachten Sie, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diese Zeichenfolge implizit in das XML-Format konvertiert. Da der Auftragsschritt das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Subsystem verwendet, gibt der Auftragsschritt keinen Proxy an.  
  
 Die Warnung führt den Auftrag immer dann aus, wenn ein Deadlockdiagrammablaufverfolgungsereignis protokolliert werden würde. Für eine WMI-Warnung erstellt SQL Server-Agent mittels angegebenem Namespace und WQL-Anweisung eine Abfragebenachrichtigung. Für diese Warnung überwacht SQL Server-Agent die Standardinstanz auf dem lokalen Computer. Die WQL-Anweisung fordert ein beliebiges `DEADLOCK_GRAPH`-Ereignis in der Standardinstanz an. Zum Ändern der Instanz, das von der Warnung überwacht wird, ersetzen Sie den Instanznamen durch `MSSQLSERVER` im `@wmi_namespace` für die Warnung.  
  
> [!NOTE]  
>  Damit SQL Server-Agent WMI-Ereignisse empfangen kann [!INCLUDE[ssSB](../../includes/sssb-md.md)] , muss in **msdb** und [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]aktiviert werden.  
  
```  
USE AdventureWorks ;  
GO  
  
IF OBJECT_ID('DeadlockEvents', 'U') IS NOT NULL  
BEGIN  
    DROP TABLE DeadlockEvents ;  
END ;  
GO  
  
CREATE TABLE DeadlockEvents  
    (AlertTime DATETIME, DeadlockGraph XML) ;  
GO  
-- Add a job for the alert to run.  
  
EXEC  msdb.dbo.sp_add_job @job_name=N'Capture Deadlock Graph',   
    @enabled=1,   
    @description=N'Job for responding to DEADLOCK_GRAPH events' ;  
GO  
  
-- Add a jobstep that inserts the current time and the deadlock graph into  
-- the DeadlockEvents table.  
  
EXEC msdb.dbo.sp_add_jobstep  
    @job_name = N'Capture Deadlock Graph',  
    @step_name=N'Insert graph into LogEvents',  
    @step_id=1,   
    @on_success_action=1,   
    @on_fail_action=2,   
    @subsystem=N'TSQL',   
    @command= N'INSERT INTO DeadlockEvents  
                (AlertTime, DeadlockGraph)  
                VALUES (getdate(), N''$(ESCAPE_SQUOTE(WMI(TextData)))'')',  
    @database_name=N'AdventureWorks' ;  
GO  
  
-- Set the job server for the job to the current instance of SQL Server.  
  
EXEC msdb.dbo.sp_add_jobserver @job_name = N'Capture Deadlock Graph' ;  
GO  
  
-- Add an alert that responds to all DEADLOCK_GRAPH events for  
-- the default instance. To monitor deadlocks for a different instance,  
-- change MSSQLSERVER to the name of the instance.  
  
EXEC msdb.dbo.sp_add_alert @name=N'Respond to DEADLOCK_GRAPH',   
@wmi_namespace=N'\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER',   
    @wmi_query=N'SELECT * FROM DEADLOCK_GRAPH',   
    @job_name='Capture Deadlock Graph' ;  
GO  
```  
  
## <a name="testing-the-sample"></a>Testen des Beispiels  
 Um zu sehen, dass der Auftrag ausgeführt wird, provozieren Sie einen Deadlock. Öffnen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Sie in zwei **SQL-Abfrage** Registerkarten, und verbinden Sie beide Abfragen mit derselben Instanz. Führen Sie auf einer der Abfrageregisterkarten das folgende Skript aus. Dieses Skript erzeugt ein Resultset und endet.  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 Führen Sie das folgende Skript auf der zweiten Abfrage Registerkarte aus. Dieses Skript erzeugt ein Resultset und dann einen Block, der darauf wartet, `Production.Product`eine Sperre zu erhalten.  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 Führen Sie das folgende Skript auf der ersten Abfrage Registerkarte aus. Dieses Skript wird blockiert und wartet darauf, eine Sperre `Production.Location`für zu erhalten. Nach einem kurzen Timeout wählt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dieses Skript oder das Skript aus dem Beispiel als Deadlockopfer aus und beendet die Transaktion.  
  
```  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
```  
  
 Warten Sie nach dem Provozieren des Deadlocks einen Moment, damit SQL Server-Agent die Warnung aktivieren und den Auftrag ausführen kann. Untersuchen Sie den Inhalt der Tabelle `DeadlockEvents`, indem Sie das folgende Skript ausführen:  
  
```  
SELECT * FROM DeadlockEvents ;  
GO  
```  
  
 Die `DeadlockGraph`-Spalte sollte ein XML-Dokument enthalten, das alle Eigenschaften des Deadlockdiagrammereignisses enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte des WMI-Anbieters für Serverereignisse](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
  
  
