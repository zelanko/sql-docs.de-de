---
title: Task Editor (Seite gespeicherte Prozeduren), Master gespeicherte Prozeduren übertragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f233f0730286a1623ee54c38084d07a2aba903e3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66054861"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a>Editor für den Task 'In 'master' gespeicherte Prozeduren übertragen' (Seite Gespeicherte Prozeduren)
  Verwenden Sie die Seite **Gespeicherte Prozeduren** im Dialogfeld **Editor für den Task „In 'master' gespeicherte Prozeduren übertragen“** , um die Eigenschaften für das Kopieren einer oder mehrerer benutzerdefinierter gespeicherter Prozeduren aus der **master**-Datenbank einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in die **master**-Datenbank einer anderen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu kopieren. Weitere Informationen zu diesem Task finden Sie unter [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Dieser Task überträgt lediglich die benutzerdefinierten gespeicherten Prozeduren des **dbo** -Besitzers aus einer **master** -Datenbank auf dem Quellserver in eine **master** -Datenbank auf dem Zielserver. Benutzer müssen die CREATE PROCEDURE-Berechtigung für die **master** -Datenbank des Zielservers besitzen oder Mitglieder der festen Serverrolle **sysadmin** auf dem Zielserver sein, um dort gespeicherte Prozeduren erstellen zu können.  
  
## <a name="options"></a>Optionen  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<Neue Verbindung...>** , um eine neue Verbindung mit dem Quellserver herzustellen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<Neue Verbindung...>** , um eine neue Verbindung mit dem Zielserver herzustellen.  
  
 **IfObjectExists**  
 Wählen Sie aus, wie der Task benutzerdefinierte gespeicherte Prozeduren behandeln soll, die in der **master** -Datenbank auf dem Zielserver bereits mit demselben Namen vorhanden sind.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|Description|  
|-----------|-----------------|  
|**FailTask**|Der Task schlägt fehl, wenn in der **master** -Datenbank auf dem Zielserver bereits gespeicherte Prozeduren mit demselben Namen vorhanden sind.|  
|**Overwrite**|Der Task überschreibt bereits vorhandene gespeicherte Prozeduren mit demselben Namen in der **master** -Datenbank auf dem Zielserver.|  
|**Skip**|Der Task lässt bereits vorhandene gespeicherte Prozeduren mit demselben Namen in der **master** -Datenbank auf dem Zielserver aus.|  
  
 **TransferAllStoredProcedures**  
 Wählen Sie aus, ob alle benutzerdefinierten gespeicherten Prozeduren in der **master** -Datenbank auf dem Quellserver auf den Zielserver kopiert werden sollen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Wahr**|Kopiert alle benutzerdefinierten gespeicherten Prozeduren in der **master** -Datenbank.|  
|**False**|Kopiert nur die angegebenen gespeicherten Prozeduren.|  
  
 **StoredProceduresList**  
 Wählen Sie aus, welche benutzerdefinierten gespeicherten Prozeduren in der **master** -Datenbank auf dem Quellserver in die **master** -Datenbank auf dem Zielserver kopiert werden sollen. Diese Option ist nur verfügbar, wenn **TransferAllStoredProcedures** auf **FALSE**festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [Editor für den Task „In 'master' gespeicherte Prozeduren übertragen“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)  
  
  
