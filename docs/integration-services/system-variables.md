---
description: Systemvariablen
title: Systemvariablen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], variables
- tasks [Integration Services], variables
- system variables [Integration Services]
- event handlers [Integration Services], variables
- variables [Integration Services], system
ms.assetid: efecd0d4-1489-4eba-a8fe-275d647058b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 913345034da936d6ed7a0c9ea3678c427b4f34ef
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495313"
---
# <a name="system-variables"></a>Systemvariablen

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt eine Reihe von Systemvariablen bereit, mit denen Informationen zum ausgeführten Paket und dessen Objekten gespeichert werden können. Diese Variablen können in Ausdrücken und Eigenschaftsausdrücken verwendet werden, um Pakete, Container, Tasks und Ereignishandler anzupassen.  
  
 Alle Variablen, seien es Systemvariablen oder benutzerdefinierte Variablen, können in den Parameterbindungen verwendet werden, die der Task „SQL ausführen“ zum Zuordnen von Variablen zu Parametern verwendet.  
  
## <a name="system-variables-for-packages"></a>Systemvariablen für Pakete  
 In der folgenden Tabelle werden die Systemvariablen beschrieben, die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] für Pakete bereitstellt.  
  
|Systemvariable|Datentyp|BESCHREIBUNG|  
|---------------------|---------------|-----------------|  
|**CancelEvent**|Int32|Das Handle für ein Windows-Ereignisobjekt, das der Task signalisieren kann, um anzugeben, dass das Ausführen des Tasks beendet werden soll.|  
|**ContainerStartTime**|Datetime|Die Startzeit für den Container.|  
|**CreationDate**|Datetime|Das Datum, an dem das Paket erstellt wurde.|  
|**CreatorComputerName**|String|Der Computer, auf dem das Paket erstellt wurde.|  
|**CreatorName**|String|Der Name der Person, die das Paket erstellt hat.|  
|**ExecutionInstanceGUID**|String|Der eindeutige Bezeichner der ausführenden Instanz eines Pakets.|  
|**FailedConfigurations**|String|Die Namen von fehlerhaften Paketkonfigurationen.|  
|**IgnoreConfigurationsOnLoad**|Boolean|Gibt an, ob die Paketkonfigurationen beim Laden des Pakets ignoriert werden.|  
|**InteractiveMode**|Boolean|Gibt an, ob das Paket im interaktiven Modus ausgeführt wird. Wenn ein Paket im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer ausgeführt wird, ist diese Eigenschaft auf **TRUE**festgelegt. Wenn ein Paket mit dem Eingabeaufforderungs-Hilfsprogramm **DTExec** ausgeführt wird, ist diese Eigenschaft auf **FALSE**festgelegt.|  
|**LocaleId**|Int32|Das Gebietsschema, das vom Paket verwendet wird.|  
|**MachineName**|String|Der Name des Computers, auf dem das Paket ausgeführt wird.|  
|**OfflineMode**|Boolean|Gibt an, ob sich das Paket im Offlinemodus befindet. Im Offlinemodus werden keine Verbindungen mit Datenquellen abgerufen.|  
|**PackageID**|String|Der eindeutige Bezeichner des Pakets.|  
|**PackageName**|String|Der Name des Pakets.|  
|**StartTime**|Datetime|Der Zeitpunkt, zu dem das Paket gestartet wurde.|  
|**ServerExecutionID**|Int64|Die Ausführungs-ID für das Paket, das auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server ausgeführt wird.<br /><br /> Der Standardwert ist 0 (null). Der Wert wird nur geändert, wenn das Paket von "ISServerExec" auf dem Server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ausgeführt wird. Wenn ein untergeordnetes Paket vorhanden ist, wird der Wert vom übergeordneten Paket an das untergeordnete Paket übergeben.|  
|**UserName**|String|Das Konto des Benutzers, der das Paket gestartet hat. Der Benutzername wird durch den Domänennamen qualifiziert.|  
|**VersionBuild**|Int32|Die Paketversion|  
|**VersionComment**|String|Kommentare zur Paketversion|  
|**VersionGUID**|String|Der eindeutige Bezeichner der Version.|  
|**VersionMajor**|Int32|Die Hauptversion des Pakets.|  
|**VersionMinor**|Int32|Die Nebenversion des Pakets.|  
  
## <a name="system-variables-for-containers"></a>Systemvariablen für Container  
 In der folgenden Tabelle werden die Systemvariablen beschrieben, die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] für For-Schleifencontainer, Foreach-Schleifencontainer und Sequenzcontainer bereitstellt.  
  
|Systemvariable|Datentyp|BESCHREIBUNG|Container|  
|---------------------|---------------|-----------------|---------------|  
|**LocaleId**|Int32|Das Gebietsschema, das vom Container verwendet wird.|For-Schleifencontainer<br /><br /> Foreach-Schleifencontainer<br /><br /> Sequenzcontainer|  
  
## <a name="system-variables-for-tasks"></a>Systemvariablen für Tasks  
 In der folgenden Tabelle werden die Systemvariablen beschrieben, die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] für Tasks bereitstellt.  
  
|Systemvariable|Datentyp|BESCHREIBUNG|  
|---------------------|---------------|-----------------|  
|**CreationName**|String|Der Name der Aufgabe.|  
|**LocaleId**|Int32|Das Gebietsschema, das vom Task verwendet wird.|  
|**TaskID**|String|Der eindeutige Bezeichner einer Taskinstanz.|  
|**TaskName**|String|Der Name der Taskinstanz.|  
|**TaskTransactionOption**|Int32|Die Transaktionsoption, die vom Task verwendet wird.|  
  
## <a name="system-variables-for-event-handlers"></a>Systemvariablen für Ereignishandler  
 In der folgenden Tabelle werden die Systemvariablen beschrieben, die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] für Ereignishandler bereitstellt. Nicht alle Variablen sind für alle Ereignishandler verfügbar.  
  
|Systemvariable|Datentyp|BESCHREIBUNG|Ereignishandler|  
|---------------------|---------------|-----------------|-------------------|  
|**Abbrechen**|Boolean|Gibt an, ob das Ausführen des Ereignishandlers bei einem Fehler, einer Warnung oder beim Abbruch einer Abfrage beendet wird.|OnError-Ereignishandler<br /><br /> OnWarning-Ereignishandler<br /><br /> OnQueryCancel-Ereignishandler|  
|**ErrorCode**|Int32|Der Fehlerbezeichner.|OnError-Ereignishandler<br /><br /> OnInformation-Ereignishandler<br /><br /> OnWarning-Ereignishandler|  
|**ErrorDescription**|String|Die Beschreibung des Fehlers.|OnError-Ereignishandler<br /><br /> OnInformation-Ereignishandler<br /><br /> OnWarning-Ereignishandler|  
|**ExecutionStatus**|Boolean|Der aktuelle Ausführungsstatus.|OnExecStatusChanged-Ereignishandler|  
|**ExecutionValue**|DBNull|Der Ausführungswert.|OnTaskFailed-Ereignishandler|  
|**LocaleId**|Int32|Das Gebietsschema, das vom Ereignishandler verwendet wird.|Alle Ereignishandler|  
|**PercentComplete**|Int32|Der Prozentsatz abgeschlossener Arbeit.|OnProgress-Ereignishandler|  
|**ProgressCountHigh**|Int32|Der obere Bereich eines 64-Bit-Werts, der die Gesamtanzahl von Vorgängen angibt, die vom OnProgress-Ereignis verarbeitet wurden.|OnProgress-Ereignishandler|  
|**ProgressCountLow**|Int32|Der untere Bereich eines 64-Bit-Werts, der die Gesamtanzahl von Vorgängen angibt, die vom OnProgress-Ereignis verarbeitet wurden.|OnProgress-Ereignishandler|  
|**ProgressDescription**|String|Die Beschreibung des Status.|OnProgress-Ereignishandler|  
|**Propagate**|Boolean|Gibt an, ob das Ereignis an einen Ereignishandler auf höherer Ebene weitergegeben wird.<br /><br /> Hinweis: Der Wert der **Propagate** -Variablen wird während der Überprüfung des Pakets ignoriert. Wenn Sie **Propagate** in einem untergeordneten Paket auf **FALSE** festlegen, wird ein Ereignis dennoch an das übergeordnete Paket weitergegeben.|Alle Ereignishandler|  
|**SourceDescription**|String|Die Beschreibung der ausführbaren Datei in dem Ereignishandler, der das Ereignis ausgelöst hat.|Alle Ereignishandler|  
|**SourceID**|String|Der eindeutige Bezeichner der ausführbaren Datei in dem Ereignishandler, der das Ereignis ausgelöst hat.|Alle Ereignishandler|  
|**SourceName**|String|Der Name der ausführbaren Datei in dem Ereignishandler, der das Ereignis ausgelöst hat.|Alle Ereignishandler|  
|**VariableDescription**|String|Die Variablenbeschreibung.|OnVariableValueChanged-Ereignishandler|  
|**VariableID**|String|Der eindeutige Bezeichner der Variablen.|OnVariableValueChanged-Ereignishandler|  
  
## <a name="system-variables-in-parameter-bindings"></a>Systemvariablen in Parameterbindungen  
 Es ist häufig nützlich, beim Ausführen des Pakets die Werte von Systemvariablen in Tabellen zu speichern. Beispielsweise ein Paket, das eine Tabelle dynamisch erstellt und den GUID der Paketausführungsinstanz schreibt, mit der die Tabelle in einer Tabellenspalte erstellt wurde.  
  
 Wenn Sie Systemvariablen verwenden, um diese Parameter der SQL-Anweisung zuzuordnen, die von einem Task SQL ausführen verwendet wird, müssen Sie unbedingt sicherstellen, dass der Datentyp der einzelnen Parameterbindungen auf den jeweiligen Datentyp der Systemvariablen festgelegt ist. Andernfalls kann es sein, dass die Werte der Systemvariablen falsch übersetzt werden. Wenn beispielsweise die Systemvariable **ExecutionInstanceGUID** mit dem Zeichenfolgen-Datentyp und einer Zeichenfolge, mit der die GUID der ausführenden Instanz eines Pakets dargestellt wird, in einer Parameterbindung mit dem GUID-Datentyp verwendet wird, wird die GUID der Paketinstanz falsch übersetzt.  
  
 Diese Regel gilt auch für benutzerdefinierte Variablen. Während die Datentypen der Systemvariablen nicht geändert werden können, und Sie diese Variablen den Datentypen entsprechend anpassen müssen, sind benutzerdefinierte Variablen jedoch im Vergleich hierzu flexibler. Die in Parameterbindungen verwendeten benutzerdefinierten Variablen sind in der Regel mit den Datentypen definiert, die mit den zugeordneten Datentypen der Parameter kompatibel sind.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Zuordnen von Abfrageparametern zu Variablen in einem Task SQL ausführen](https://msdn.microsoft.com/library/6a164349-dfcf-4995-80bc-d4e7aee52a83)  
  
  
