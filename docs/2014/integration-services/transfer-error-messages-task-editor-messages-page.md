---
title: Task Editor für Fehlermeldungen übertragen (Seite Meldungen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e9d9d0d7f03b52b2ea82d555b6cbe9127128e83f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766293"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>Editor für den Task Fehlermeldungen übertragen (Seite Meldungen)
  Verwenden Sie die Seite **Meldungen** im Dialogfeld **Editor für den Task „Fehlermeldungen übertragen“**, um die Eigenschaften für das Kopieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Fehlermeldungen von einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in eine andere anzugeben. Weitere Informationen zu diesem Task finden Sie unter [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).  
  
## <a name="options"></a>Optionen  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<Neue Verbindung...>**, um eine neue Verbindung mit dem Quellserver herzustellen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<Neue Verbindung...>**, um eine neue Verbindung mit dem Zielserver herzustellen.  
  
 **IfObjectExists**  
 Wählen Sie aus, ob der Task vorhandene benutzerdefinierte Fehlermeldungen überschreiben, vorhandene Meldungen auslassen oder einen Fehler erzeugen soll, wenn auf dem Zielserver bereits Meldungen desselben Namens vorhanden sind.  
  
 **TransferAllErrorMessages**  
 Wählen Sie aus, ob der Task alle oder nur die angegebenen benutzerdefinierten Meldungen vom Quell- auf den Zielserver kopieren soll.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|Description|  
|-----------|-----------------|  
|**Wahr**|Alle benutzerdefinierten Meldungen kopieren.|  
|**False**|Nur die angegebenen benutzerdefinierten Meldungen kopieren.|  
  
 **ErrorMessagesList**  
 Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)**, um die zu kopierenden Fehlermeldungen auszuwählen.  
  
> [!NOTE]  
>  Sie müssen **SourceConnection** angeben, bevor Sie eine zu kopierende Fehlermeldung auswählen können.  
  
 **ErrorMessageLanguagesList**  
 Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)**, um die Sprachen auszuwählen, für die benutzerdefinierte Fehlermeldungen auf den Zielserver kopiert werden. Auf dem Zielserver muss eine Version der Meldung in us_english (Codepage 1033) vorhanden sein, bevor Sie andere Sprachversionen auf den Server übertragen können.  
  
> [!NOTE]  
>  Sie müssen **SourceConnection** angeben, bevor Sie eine zu kopierende Fehlermeldung auswählen können.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [Editor für den Task „Fehlermeldungen übertragen“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)   
 [Editor für den Task „Fehlermeldungen übertragen“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)  
  
  
