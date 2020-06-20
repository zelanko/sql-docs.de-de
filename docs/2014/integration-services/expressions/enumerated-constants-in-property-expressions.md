---
title: Aufgezählte Konstanten in Eigenschaftsausdrücken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4b691367b8cfbe00c1e383fa3a2fd18e2d545be8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967420"
---
# <a name="enumerated-constants-in-property-expressions"></a>Aufgezählte Konstanten in Eigenschaftsausdrücken
  Wenn Eigenschaftsausdrücke Werte aus einer Liste von Enumeratorelementen enthalten, müssen die Ausdrücke den numerischen Wert des Enumeratorelements anstelle des Anzeigenamens des Elements verwenden. Wenn z. B. ein Ausdruck die `LoggingMode`-Eigenschaft festlegt, müssen Sie den numerischen Wert 2 anstelle des Anzeigenamens Disabled verwenden.  
  
 In diesem Thema werden nur die entsprechenden numerischen Werte für Anzeigenamen von Enumeratoren aufgelistet, deren Elemente häufig in Eigenschaftsausdrücken verwendet werden. Das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objektmodell enthält viele zusätzliche Enumeratoren, die Sie beim Programmieren des Objektmodells verwenden können, um Pakete programmgesteuert zu erstellen oder um benutzerdefinierte Paketelemente, wie z. B. Tasks und Datenflusskomponenten, zu programmieren.  
  
 Neben den benutzerdefinierten Eigenschaften für Pakete und Paketobjekte enthält das Eigenschaftenfenster in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] eine Reihe von Eigenschaften, die für Pakete, Tasks, für die Foreach- und For-Schleife sowie für Sequenzcontainer zur Verfügung stehen. Die allgemeinen Eigenschaften, die durch Werte von Enumeratoren,, und festgelegt werden, `ForceExecutionResult` `LoggingMode` `IsolationLevel` `Transaction Option` sind im Abschnitt Allgemeine Eigenschaften aufgeführt.  
  
 In den folgenden Abschnitten werden Informationen zu den folgenden aufgelisteten Konstanten bereitgestellt:  
  
 [Paket](#Package)  
  
 [Foreach-Schleifenenumeratoren](#Foreach)  
  
 [Aufgaben](#Tasks)  
  
 [Wartungsplantasks](#MaintenancePlanTasks)  
  
 [Common Properties](#CommonProperties)  
  
##  <a name="package"></a><a name="Package"></a> Paket  
 In den folgenden Tabellen finden Sie eine Auflistung der Anzeigenamen und der entsprechenden numerischen Werte für Eigenschaften von Paketen, die Sie mithilfe von Werten eines Enumerators festlegen.  
  
 `PackageType`Eigenschaften Satz mithilfe von Werten aus der- `DTSPackageType` Enumeration.  
  
|Anzeigename in DTSPackageType|Numerischer Wert|  
|-------------------------------------|-------------------|  
|Standard|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage`Eigenschaften Satz mithilfe von Werten aus der- `DTSCheckpointUsage` Enumeration.  
  
|Anzeigename in DTSCheckpointUsage|Numerischer Wert|  
|-----------------------------------------|-------------------|  
|Nie|0|  
|IfExists|1|  
|Always|2|  
  
 `PackagePriorityClass`Eigenschaften Satz mithilfe von Werten aus der- `DTSPriorityClass` Enumeration.  
  
|Anzeigename in DTSPriorityClass|Numerischer Wert|  
|---------------------------------------|-------------------|  
|Standard|0|  
|AboveNormal|1|  
|Normal|2|  
|BelowNormal|3|  
|Idle|4|  
  
 `ProtectionLevel`Eigenschaften Satz mithilfe von Werten aus der- `DTSProtectionLevel` Enumeration.  
  
|Anzeigename in DTSProtectionLevel|Numerischer Wert|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="precedence-constraints"></a><a name="PrecedenceConstraints"></a> Rangfolgeneinschränkungen  
 `EvalOp`Eigenschaften Satz mithilfe von Werten aus der- `DTSPrecedenceEvalOp` Enumeration.  
  
|Anzeigename in DTSPrecedenceEvalOp|Numerischer Wert|  
|------------------------------------------|-------------------|  
|Ausdruck|1|  
|Einschränkung|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value`Eigenschaften Satz mithilfe von Werten aus der- `DTSExecResult` Enumeration.  
  
|Anzeigename|Numerischer Wert|  
|-------------------|-------------------|  
|Erfolg|0|  
|Fehler|1|  
|Completion|2|  
|Canceled|3|  
  
##  <a name="foreach-loop-enumerators"></a><a name="Foreach"></a> Foreach-Schleifenenumeratoren  
 Die Foreach-Schleife enthält eine Reihe von Enumeratoren mit Eigenschaften, die mithilfe von Eigenschaftsausdrücken festgelegt werden können.  
  
### <a name="foreach-ado-enumerator"></a>Foreach-ADO-Enumerator  
 `Type`Eigenschaften Satz mithilfe von Werten aus der- `ADOEnumerationType` Enumeration.  
  
|Anzeigename in ADOEnumerationType|Numerischer Wert|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Foreach-NodeList-Enumerator  
 `SourceDocumentType``InnerXPathStringSourceType`die Eigenschaften, und **OuterXPathStringSourceType** werden mithilfe von Werten aus der- `SourceType` Enumeration festgelegt.  
  
|Anzeigename in SourceType|Numerischer Wert|  
|---------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
|DirectInput|2|  
  
 `EnumerationType`Eigenschaften Satz mithilfe von Werten aus der- `EnumerationType` Enumeration.  
  
|Anzeigename in EnumerationType|Numerischer Wert|  
|--------------------------------------|-------------------|  
|Navigator|0|  
|Node|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType`Eigenschaften Satz mithilfe von Werten aus der- `InnerElementType` Enumeration.  
  
|Anzeigename in InnerElementType|Numerischer Wert|  
|---------------------------------------|-------------------|  
|Navigator|0|  
|Node|1|  
|NodeText|2|  
  
##  <a name="tasks"></a><a name="Tasks"></a> Aufgaben  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält eine Reihe von Tasks mit Eigenschaften, die mithilfe von Eigenschaftsausdrücken festgelegt werden können.  
  
### <a name="analysis-services-execute-ddl-task"></a>DDL ausführen (Analysis Services-Task)  
 `SourceType`Eigenschaften Satz mithilfe von Werten aus der- `DDLSourceType` Enumeration.  
  
|Anzeigename in DDLSourceType|Numerischer Wert|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variable|2|  
  
### <a name="bulk-insert-task"></a>Masseneinfügungstask  
 `DataFileType`Eigenschaften Satz mithilfe von Werten aus der- `DTSBulkInsert_DataFileType` Enumeration.  
  
|Anzeigename in DTSBulkInsert_DataFileType|Numerischer Wert|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>SQL ausführen (Task)  
 `ResultSetType`Eigenschaften Satz mithilfe von Werten aus der- `ResultSetType` Enumeration.  
  
|Anzeigename in ResultSetType|Numerischer Wert|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType`Eigenschaften Satz mithilfe von Werten aus der- `SqlStatementSourceType` Enumeration.  
  
|Anzeigename in SqlStatementSourceType|Numerischer Wert|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|FileConnection|2|  
|Variable|3|  
  
### <a name="file-system-task"></a>Task Dateisystem  
 `Operation`Eigenschaften Satz mithilfe von Werten aus der- `DTSFileSystemOperation` Enumeration.  
  
|Anzeigename in DTSFileSystemOperation|Numerischer Wert|  
|---------------------------------------------|-------------------|  
|CopyFile|0|  
|MoveFile|1|  
|DeleteFile|2|  
|RenameFile|3|  
|SetAttributes|4|  
|CreateDirectory|5|  
|CopyDirectory|6|  
|MoveDirectory|7|  
|DeleteDirectory|8|  
|DeleteDirectoryContent|9|  
  
 `Attributes`Eigenschaften Satz mithilfe von Werten aus der- `DTSFileSystemAttributes` Enumeration.  
  
|Anzeigename in DTSFileSystemAttributes|Numerischer Wert|  
|----------------------------------------------|-------------------|  
|Normal|0|  
|Archivieren|1|  
|Ausgeblendet|2|  
|ReadOnly|4|  
|System|8|  
  
### <a name="ftp-task"></a>FTP-Task  
 `Operation`Eigenschaften Satz mithilfe von Werten aus der- `DTSFTPOp` Enumeration.  
  
|Anzeigename in DTSFTPOp|Numerischer Wert|  
|-------------------------------|-------------------|  
|Send|0|  
|Empfangen|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType`Eigenschaften Satz mithilfe von Werten aus der- `MQMessageType` Enumeration.  
  
|Anzeigename in MQMessageType|Numerischer Wert|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType`Eigenschaften Satz mithilfe von Werten aus der- `MQStringMessageCompare` Enumeration.  
  
|Anzeigename in MQStringMessageCompare|Numerischer Wert|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType`Eigenschaften Satz mithilfe von Werten aus der- `MQType` Enumeration.  
  
|Anzeigename in MQType|Numerischer Wert|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>Mail senden (Task)  
 `MessageSourceType`Eigenschaften Satz mithilfe von Werten aus der- `SendMailMessageSourceType` Enumeration.  
  
|Anzeigename in SendMailMessageSourceType|Numerischer Wert|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variable|2|  
  
 `Priority`Eigenschaften Satz mithilfe von Werten aus der- `MailPriority` Enumeration.  
  
|Anzeigename in MailPriority|Numerischer Wert|  
|-----------------------------------|-------------------|  
|High|1|  
|Normal|3|  
|Niedrig|5|  
  
### <a name="transfer-database-task"></a>Datenbanken übertragen (Task)  
 `Action`Eigenschaften Satz mithilfe von Werten aus der- `TransferAction` Enumeration.  
  
|Anzeigename in TransferAction|Numerischer Wert|  
|-------------------------------------|-------------------|  
|Kopieren|0|  
|Move|1|  
  
 `Method`Eigenschaften Satz mithilfe von Werten aus der- `TransferMethod` Enumeration.  
  
|Anzeigename in TransferMethod|Numerischer Wert|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>Fehlermeldungen übertragen (Task)  
 `IfObjectExists`Eigenschaften Satz mithilfe von Werten aus der- `IfObjectExists` Enumeration.  
  
|Anzeigename in IfObjectExists|Numerischer Wert|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-jobs-task"></a>Aufträge übertragen (Task)  
 `IfObjectExists`Eigenschaften Satz mithilfe von Werten aus der- `IfObjectExists` Enumeration.  
  
|Anzeigename in IfObjectExists|Numerischer Wert|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-logins-task"></a>Task "Anmeldungen übertragen"  
 `IfObjectExists`Eigenschaften Satz mithilfe von Werten aus der- `IfObjectExists` Enumeration.  
  
|Anzeigename in IfObjectExists|Numerischer Wert|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
 `LoginsToTransfer`Eigenschaften Satz mithilfe von Werten aus der- `LoginsToTransfer` Enumeration.  
  
|Anzeigename in LoginsToTransfer|Numerischer Wert|  
|---------------------------------------|-------------------|  
|AllLogins|0|  
|SelectedLogins|1|  
|AllLoginsFromSelectedDatabases|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>In master gespeicherte Prozeduren übertragen (Task)  
 `IfObjectExists`Eigenschaften Satz mithilfe von Werten aus der- `IfObjectExists` Enumeration.  
  
|Anzeigename in IfObjectExists|Numerischer Wert|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-sql-server-objects-task"></a>SQL Server-Objekte kopieren (Task)  
 `ExistingData`Eigenschaften Satz mithilfe von Werten aus der- `ExistingData` Enumeration.  
  
|Anzeigename in ExistingData|Numerischer Wert|  
|-----------------------------------|-------------------|  
|Replace|0|  
|Anfügen|1|  
  
### <a name="web-service-task"></a>Webdienst (Task)  
 `OutputType`Eigenschaften Satz mithilfe von Werten aus der- `DTSOutputType` Enumeration.  
  
|Anzeigename in DTSOutputType|Numerischer Wert|  
|------------------------------------|-------------------|  
|Datei|0|  
|Variable|1|  
  
### <a name="wmi-data-reader-task"></a>WMI-Datenleser (Task)  
 `OverwriteDestination`Eigenschaften Satz mithilfe von Werten aus der- `OverwriteDestination` Enumeration.  
  
|Anzeigename in OverwriteDestination|Numerischer Wert|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType`Eigenschaften Satz mithilfe von Werten aus der- `OutputType` Enumeration.  
  
|Anzeigename in OutputType|Numerischer Wert|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType`Eigenschaften Satz mithilfe von Werten aus der- `DestinationType` Enumeration.  
  
|Anzeigename in DestinationType|Numerischer Wert|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
  
 `WqlQuerySourceType`Eigenschaften Satz mithilfe von Werten aus der- `QuerySourceType` Enumeration.  
  
|Anzeigename in QuerySourceType|Numerischer Wert|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variable|2|  
  
 Eigenschaft "WMI-Ereignisüberwachung", `ActionAtEvent` die mithilfe von Werten aus der-Enumeration festgelegt wird `ActionAtEvent` .  
  
|Anzeigename in ActionAtEvent|Numerischer Wert|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout`Eigenschaften Satz mithilfe von Werten aus der- `ActionAtTimeout` Enumeration.  
  
|Anzeigename in ActionAtTimeout|Numerischer Wert|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent`Eigenschaften Satz mithilfe von Werten aus der- `AfterEvent` Enumeration.  
  
|Anzeigename in AfterEvent|Numerischer Wert|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout`Eigenschaften Satz mithilfe von Werten aus der- `AfterTimeout` Enumeration.  
  
|Anzeigename in AfterTimeout|Numerischer Wert|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType`Eigenschaften Satz mithilfe von Werten aus der- `QuerySourceType` Enumeration.  
  
|Anzeigename in QuerySourceType|Numerischer Wert|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variable|2|  
  
### <a name="xml-task"></a>XML-Task  
 `OperationType`Eigenschaften Satz mithilfe von Werten aus der- `DTSXMLOperation` Enumeration.  
  
|Anzeigename in DTSXMLOperation|Numerischer Wert|  
|--------------------------------------|-------------------|  
|Überprüfen|0|  
|XSLT|1|  
|XPATH|2|  
|Merge|3|  
|Diff|4|  
|Patch|5|  
  
 `SourceType``SecondOperandType` `XPathSourceType` -,-und-Eigenschaften, die mithilfe von Werten aus der-Enumeration festgelegt werden `DTSXMLSourceType` .  
  
|Anzeigename in DTSXMLSourceType|Numerischer Wert|  
|---------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
|DirectInput|2|  
  
 `DestinationType`und **diffgrammdestinationtype** -Eigenschaften, die mithilfe von Werten aus der-Enumeration festgelegt werden `DTSXMLSaveResultTo` .  
  
|Anzeigename in DTSXMLSaveResultTo|Numerischer Wert|  
|-----------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
  
 `ValidationType`Eigenschaften Satz mithilfe von Werten aus der- `DTSXMLValidationType` Enumeration.  
  
|Anzeigename in DTSXMLValidationType|Numerischer Wert|  
|-------------------------------------------|-------------------|  
|DTD|0|  
|XSD|1|  
  
 `XPathOperation`Eigenschaften Satz mithilfe von Werten aus der- `DTSXMLXPathOperation` Enumeration.  
  
|Anzeigename in DTSXMLXPathOperation|Numerischer Wert|  
|-------------------------------------------|-------------------|  
|Auswertung|0|  
|Werte|1|  
|NodeList|2|  
  
 `DiffOptions`Eigenschaften Satz mithilfe von Werten aus der- `DTSXMLDiffOptions` Enumeration. Die Optionen in diesem Enumerator schließen sich nicht gegenseitig aus. Stellen Sie eine durch Trennzeichen getrennte Liste der anzuwendenden Optionen bereit, um mehrere Optionen zu verwenden.  
  
|Anzeigename in DTSXMLDiffOptions|Numerischer Wert|  
|----------------------------------------|-------------------|  
|Keine|0|  
|IgnoreChildOrder|1|  
|IgnoreComments|2|  
|IgnorePI|4|  
|IgnoreWhitespace|8|  
|IgnoreNamespaces|16|  
|IgnorePrefixes|32|  
|IgnoreXmlDecl|64|  
|IgnoreDtd|128|  
  
 `DiffAlgorithm`Eigenschaften Satz mithilfe von Werten aus der- `DTSXMLDiffAlgorithm` Enumeration.  
  
|Anzeigename in DTSXMLDiffAlgorithm|Numerischer Wert|  
|------------------------------------------|-------------------|  
|Auto|0|  
|Schnell|1|  
|Precise|2|  
  
##  <a name="maintenance-plan-tasks"></a><a name="MaintenancePlanTasks"></a> Wartungsplantasks  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält eine Reihe von Tasks, mit denen SQL Server-Tasks für die Verwendung in Wartungsplänen und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen ausgeführt werden.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt nicht die programmgesteuerte Verwendung dieser Tasks, und die Programmierungsreferenzdokumentation enthält keine API-Dokumentation dieser Tasks und ihrer zugehörigen Enumeratoren.  
  
### <a name="all-maintenance-tasks"></a>Alle Wartungstasks  
 Die folgenden Enumerationen werden in allen Wartungstasks verwendet, um die angegebenen Eigenschaften festzulegen.  
  
 `DatabaseSelectionType`Eigenschaften Satz mithilfe von Werten aus der- `DatabaseSelection` Enumeration.  
  
|Anzeigename in DatabaseSelection|Numerischer Wert|  
|----------------------------------------|-------------------|  
|Keine|0|  
|All|1|  
|System|2|  
|Benutzer|3|  
|Spezifisch|4|  
  
 `TableSelectionType`Eigenschaften Satz mithilfe von Werten aus der- `TableSelection` Enumeration.  
  
|Anzeigename in TableSelection|Numerischer Wert|  
|-------------------------------------|-------------------|  
|Keine|0|  
|All|1|  
|Spezifisch|2|  
  
 `ObjectTypeSelection`Eigenschaften Satz mithilfe von Werten aus der- `ObjectType` Enumeration.  
  
|Anzeigename in ObjectType|Numerischer Wert|  
|---------------------------------|-------------------|  
|Tabelle|0|  
|Sicht|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>Datenbank sichern (Task)  
 `DestinationCreationType`Eigenschaften Satz mithilfe von Werten aus der- `DestinationType` Enumeration.  
  
|Anzeigename in DestinationType|Numerischer Wert|  
|--------------------------------------|-------------------|  
|Auto|0|  
|Manuell|1|  
  
 `ExistingBackupsAction`Eigenschaften Satz mithilfe von Werten aus der- `ActionForExistingBackups` Enumeration.  
  
|Anzeigename in ActionForExistingBackups|Numerischer Wert|  
|-----------------------------------------------|-------------------|  
|Anfügen|0|  
|Overwrite|1|  
  
 `BackupAction`Eigenschaften Satz mithilfe von Werten aus der- `BackupTaskType` Enumeration. Diese Eigenschaft arbeitet mit der `BackupIsIncremental`-Eigenschaft zusammen, um den Typ der vom Task durchgeführten Sicherung zu definieren.  
  
|Anzeigename in BackupTaskType|Numerischer Wert|  
|-------------------------------------|-------------------|  
|Datenbank|0|  
|Dateien|1|  
|Log|2|  
  
 `BackupDevice`Eigenschaften Satz, der mithilfe von Werten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO)-Enumeration festgelegt wird `DeviceType` .  
  
|Anzeigename in DeviceType|Numerischer Wert|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|Band|1|  
|Datei|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>Wartungscleanup (Task)  
 `FileTypeSelected`Eigenschaften Satz mithilfe von Werten aus der- `FileType` Enumeration.  
  
|Anzeigename in FileType|Numerischer Wert|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType`Eigenschaften Satz mithilfe von Werten aus der- `TimeUnitType` Enumeration.  
  
|Anzeigename in TimeUnitType|Numerischer Wert|  
|-----------------------------------|-------------------|  
|Day (Tag)|0|  
|Week|1|  
|Month (Monat)|2|  
|Jahr|3|  
  
### <a name="update-statistics-task"></a>Statistiken aktualisieren (Task)  
 `UpdateType`Eigenschaften Satz, der mithilfe von Werten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO)-Enumeration festgelegt wird `StatisticsTarget` .  
  
|Anzeigename in StatisticsTarget|Numerischer Wert|  
|---------------------------------------|-------------------|  
|Column|1|  
|Index|2|  
|All|3|  
  
##  <a name="common-properties"></a><a name="CommonProperties"></a> Allgemeine Eigenschaften  
 Pakete, Tasks, die Foreach-Schleife, die For-Schleife und Sequenzcontainer können die folgenden Enumerationen verwenden, um die angegebenen Eigenschaften festzulegen.  
  
 `ForceExecutionResult`Eigenschaften Satz mithilfe von Werten aus der- `DTSForcedExecResult` Enumeration.  
  
|Anzeigename in DTSForcedExecResult|Numerischer Wert|  
|------------------------------------------|-------------------|  
|Keine|-1|  
|Erfolg|0|  
|Fehler|1|  
|Completion|2|  
  
 `IsolationLevel`Eigenschaft: Festlegung durch die .NET Framework- `IsolationLevel` Enumeration. Weitere Informationen finden Sie in der .NET Framework-Klassenbibliothek unter der [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313).  
  
 `LoggingMode`Eigenschaften Satz mithilfe von Werten aus der- `DTSLoggingMode` Enumeration.  
  
|Anzeigename in DTSLoggingMode|Numerischer Wert|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|Enabled|1|  
|Disabled|2|  
  
 `TransactionOption`Eigenschaften Satz mithilfe von Werten aus der- `DTSTransactionOption` Enumeration.  
  
|Anzeigename in DTSTransactionOption|Numerischer Wert|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|Unterstützt|1|  
|Erforderlich|2|  
  
## <a name="related-tasks"></a>Related Tasks  
 [Hinzufügen oder Ändern eines Eigenschaftsausdrucks](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Eigenschaftsausdrücken in Paketen](use-property-expressions-in-packages.md)   
 [Integration Services-Pakete &#40;SSIS&#41;](../integration-services-ssis-packages.md)   
 [Integration Services-Container](../control-flow/integration-services-containers.md)   
 [Integration Services-Tasks](../control-flow/integration-services-tasks.md)   
 [Rangfolgeneinschränkungen](../control-flow/precedence-constraints.md)  
  
  
