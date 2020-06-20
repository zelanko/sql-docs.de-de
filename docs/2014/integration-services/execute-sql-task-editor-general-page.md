---
title: Editor für den Task ' SQL ausführen ' (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.general.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: beb39086-28ce-46af-b6d8-f7b4fb8d9069
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 294836625075a70b8e101afef2bb9221a177ca47
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966777"
---
# <a name="execute-sql-task-editor-general-page"></a>Editor für den Task 'SQL ausführen' (Seite Allgemein)
  Mithilfe der Seite **Allgemein** im Dialogfeld **Editor für den Task „SQL ausführen“** können Sie den Task „SQL ausführen“ konfigurieren und die SQL-Anweisung bereitstellen, die vom Task ausgeführt wird.  
  
 Weitere Informationen zu diesem Task finden Sie unter [SQL ausführen (Task)](control-flow/execute-sql-task.md), [Parameter und Rückgabecodes im Task „SQL ausführen“](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) und [Resultsets im Task „SQL ausführen“](../../2014/integration-services/result-sets-in-the-execute-sql-task.md). Weitere Informationen zur Transact-SQL-Abfragesprache finden Sie unter [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference).  
  
## <a name="static-options"></a>Statische Optionen  
 **Name**  
 Geben Sie einen eindeutigen Namen für den Task 'SQL ausführen' im Workflow an. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie den Task 'SQL ausführen'. Es wird hierbei empfohlen, das Paket zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und einfacher zu verwalten sind.  
  
 **Zeit**  
 Geben Sie die maximale Anzahl von Sekunden an, die der Task ausgeführt wird, bevor ein Timeout eintritt. Der Wert 0 gibt eine unbegrenzte Zeit an. Die Standardeinstellung ist 0.  
  
> [!NOTE]  
>  Bei gespeicherten Prozeduren tritt kein Timeout ein, wenn sie diese die Funktionalität des Ruhezustands dadurch emulieren, dass sie mehr Zeit für das Herstellen von Verbindungen und das Abschließen von Transaktionen bereitstellen, als durch den Wert für **TimeOut**angegeben wird. Gespeicherte Prozeduren, die Abfragen ausführen, unterliegen jedoch immer den durch den Wert für **TimeOut**angegebenen Zeitbeschränkungen.  
  
 **Codepage**  
 Geben Sie die Codepage an, die beim Übersetzen von Unicode-Werten in Variablen verwendet werden soll. Der Standardwert ist die Codepage des lokalen Computers.  
  
> [!NOTE]  
>  Wenn der Task „SQL ausführen“ einen ADO- oder ODBC-Verbindungs-Manager verwendet, ist die **CodePage** -Eigenschaft nicht verfügbar. Wenn Ihre Projektmappe eine Codepage erfordert, verwenden Sie einen OLE DB- oder einen ADO.NET-Verbindungs-Manager mit dem Task "SQL ausführen".  
  
 **TypeConversionMode**  
 Wenn Sie diese Eigenschaft auf `Allowed` festlegen, wird anhand des Tasks "SQL ausführen" versucht, Ausgabeparameter sowie Abfrageergebnisse in den Datentyp der Variablen zu konvertieren, der die Ergebnisse zugewiesen sind. Dies gilt für den Resultsettyp **Einzelne Zeile** .  
  
 **ResultSet**  
 Geben Sie den von der auszuführenden SQL-Anweisung erwarteten Ergebnistyp an. Wählen Sie zwischen **Einzelne Zeile**, **Vollständiges Resultset**, **XML**und **Keine**aus.  
  
 **ConnectionType**  
 Wählen Sie den Typ des Verbindungs-Managers aus, der zum Herstellen der Verbindung mit der Datenquelle verwendet werden soll. Zu den verfügbaren Verbindungstypen zählen: **OLE DB**, **ODBC**, **ADO**, **ADO.NET** und **SQLMOBILE**.  
  
 **Verwandte Themen:** [OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md), [ODBC-Verbindungs-Manager](connection-manager/odbc-connection-manager.md), [ADO-Verbindungs-Manager-](connection-manager/ado-connection-manager.md), [ADO.NET-Verbindungs-Manager](connection-manager/ado-net-connection-manager.md), [SQL Server Compact Edition-Verbindungs-Manager](connection-manager/sql-server-compact-edition-connection-manager.md)  
  
 **Connection**  
 Wählen Sie die Verbindung aus einer Liste definierter Verbindungs-Manager aus. Wählen Sie aus, um eine neue Verbindung zu erstellen \<**New connection...**> .  
  
 **SQLSourceType**  
 Wählen Sie den Quelltyp der SQL-Anweisung aus, die von dem Task ausgeführt wird.  
  
 Je nachdem, welchen Verbindungs-Manager-Typ der Task SQL ausführen verwendet, müssen Sie bestimmte Parametermarkierungen in parametrisierten SQL-Anweisungen verwenden.  
  
 **Verwandte Themen:** Abschnitt „Ausführen parametrisierter SQL-Befehle“ in [SQL ausführen (Task)](control-flow/execute-sql-task.md)  
  
 Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**Direct input**|Legen Sie als Quelle eine Transact-SQL-Anweisung fest. Bei Auswahl dieses Wertes wird die dynamische Option **SQLStatement**angezeigt.|  
|**File connection**|Wählen Sie eine Datei aus, die eine Transact-SQL-Anweisung enthält. Durch Festlegen dieser Option wird die dynamische Option **FileConnection**angezeigt.|  
|**Variable**|Legen Sie als Quelle eine Variable fest, die die Transact-SQL-Anweisung definiert. Bei Auswahl dieses Wertes wird die dynamische Option **SourceVariable**angezeigt.|  
  
 **QueryIsStoredProcedure**  
 Zeigt an, ob die angegebene auszuführende SQL-Anweisung eine gespeicherte Prozedur ist. Diese Eigenschaft weist nur dann den Lese-/Schreibmodus auf, wenn der Task den ADO-Verbindungs-Manager verwendet. Andernfalls ist die Eigenschaft schreibgeschützt und ihr Wert ist auf `false` festgelegt.  
  
 **BypassPrepare**  
 Geben Sie an, ob die SQL-Anweisung vorbereitet ist.  `true` überspringt die Vorbereitung. Mit `false` wird die SQL-Anweisung vor dem Ausführen vorbereitet. Diese Option ist nur für OLE DB-Verbindungen verfügbar, die die Vorbereitung unterstützen.  
  
 **Verwandte Themen:**  [Vorbereitete Ausführung](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
 **Durchsuchen**  
 Suchen Sie mithilfe des Dialogfelds **Öffnen** eine Datei, die eine SQL-Anweisung enthält. Wählen Sie eine Datei aus, um den Dateiinhalt als SQL-Anweisung in die **SQLStatement** -Eigenschaft zu kopieren.  
  
 **Abfrage erstellen**  
 Erstellen Sie mithilfe des Dialogfelds **Abfrage-Generator** , einem grafischen Tool zum Erstellen von Abfragen, eine SQL-Anweisung. Diese Option ist verfügbar, wenn die Option **SQLSourceType** auf **Direct input**festgelegt ist.  
  
 **Abfrage analysieren**  
 Überprüft die Syntax der SQL-Anweisung.  
  
## <a name="sqlsourcetype-dynamic-options"></a>SQLSourceType (dynamische Optionen)  
  
### <a name="sqlsourcetype--direct-input"></a>SQLSourceType = Direct input  
 **SQLStatement**  
 Geben Sie die auszuführende SQL-Anweisung in das Optionsfeld ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen (...), um die SQL-Anweisung im Dialogfeld **SQL-Abfrage eingeben** einzugeben, oder klicken Sie auf **Abfrage erstellen** , um die Anweisung mithilfe des Dialog Felds **Abfrage-Generator** zu verfassen.  
  
 **Verwandte Themen:** [Abfrage-Generator](../../2014/integration-services/query-builder.md)  
  
### <a name="sqlsourcetype--file-connection"></a>SQLSourceType = File connection  
 **FileConnection**  
 Wählen Sie einen vorhandenen Dateiverbindungs-Manager aus, oder klicken Sie \<**New connection...**> zum Erstellen eines neuen Verbindungs-Managers.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="sqlsourcetype--variable"></a>SQLSourceType = Variable  
 **SourceVariable**  
 Wählen Sie eine vorhandene Variable aus, oder klicken Sie \<**New variable...**> auf, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task ' SQL ausführen ' &#40;Seite Parameter Zuordnung&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)   
 [Editor für den Task "SQL ausführen" &#40;resultsetseite&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)  
  
  
