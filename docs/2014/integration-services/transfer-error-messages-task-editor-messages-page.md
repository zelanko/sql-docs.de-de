---
title: Editor für den Task Fehlermeldungen übertragen (Seite Meldungen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b551d60d36948cb4c950dfcd9a17e2c16229420
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420697"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>Editor für den Task Fehlermeldungen übertragen (Seite Meldungen)
  Verwenden Sie die Seite **Meldungen** im Dialogfeld **Editor für den Task „Fehlermeldungen übertragen“** , um die Eigenschaften für das Kopieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Fehlermeldungen von einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in eine andere anzugeben. Weitere Informationen zu diesem Task finden Sie unter [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).  
  
## <a name="options"></a>Optionen  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie **\<New connection...>** auf, um eine neue Verbindung mit dem Quell Server zu erstellen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie **\<New connection...>** auf, um eine neue Verbindung mit dem Zielserver zu erstellen.  
  
 **IfObjectExists**  
 Wählen Sie aus, ob der Task vorhandene benutzerdefinierte Fehlermeldungen überschreiben, vorhandene Meldungen auslassen oder einen Fehler erzeugen soll, wenn auf dem Zielserver bereits Meldungen desselben Namens vorhanden sind.  
  
 **TransferAllErrorMessages**  
 Wählen Sie aus, ob der Task alle oder nur die angegebenen benutzerdefinierten Meldungen vom Quell- auf den Zielserver kopieren soll.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**True**|Alle benutzerdefinierten Meldungen kopieren.|  
|**Alarm**|Nur die angegebenen benutzerdefinierten Meldungen kopieren.|  
  
 **ErrorMessagesList**  
 Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** , um die zu Kopierfehler Meldungen auszuwählen.  
  
> [!NOTE]  
>  Sie müssen **SourceConnection** angeben, bevor Sie eine zu kopierende Fehlermeldung auswählen können.  
  
 **ErrorMessageLanguagesList**  
 Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** , um die Sprachen auszuwählen, für die benutzerdefinierte Fehlermeldungen auf den Zielserver kopiert werden sollen. Auf dem Zielserver muss eine Version der Meldung in us_english (Codepage 1033) vorhanden sein, bevor Sie andere Sprachversionen auf den Server übertragen können.  
  
> [!NOTE]  
>  Sie müssen **SourceConnection** angeben, bevor Sie eine zu kopierende Fehlermeldung auswählen können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Aufgaben Integration Services](control-flow/integration-services-tasks.md)   
 [Editor für den Task Fehlermeldungen übertragen &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)   
 [Editor für den Task Fehlermeldungen übertragen &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)  
  
  
