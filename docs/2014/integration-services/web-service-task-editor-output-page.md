---
title: Web Service Task-Editor (Seite "Fehlerausgabe") | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: bcf7bd1ce50b19f62de5f249a1f89a4fdda0f5b0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048998"
---
# <a name="web-service-task-editor-output-page"></a>Editor für den Task 'Webdienst' (Seite Ausgabe)
  Verwenden Sie die Seite **Ausgabe** des Dialogfelds **Editor für den Task 'Webdienst'** , um anzugeben, wo das durch die Webmethode zurückgegebene Ergebnis gespeichert werden soll.  
  
 Weitere Informationen zu diesem Task finden Sie unter [Webdienst (Task)](control-flow/web-service-task.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **OutputType**  
 Wählt den Speichertyp, der beim Speichern der Ergebnisse verwendet werden soll. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|Description|  
|-----------|-----------------|  
|**File Connection**|Speichert die Ergebnisse in einer Datei. Wenn Sie diesen Wert auswählen, wird die dynamische Option **Datei**angezeigt.|  
|**Variable**|Speichert die Ergebnisse in einer Variablen. Wenn Sie diesen Wert auswählen, wird die dynamische Option **Variable**angezeigt.|  
  
## <a name="outputtype-dynamic-options"></a>OutputType (dynamische Optionen)  
  
### <a name="outputtype--file-connection"></a>OutputType = File Connection  
 **File**  
 Wählen Sie in der Liste einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>OutputType = Variable  
 **Variable**  
 Wählen Sie in der Liste eine Variable aus, oder klicken Sie auf \<**Neue Variable…**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task Webdienst &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task Webdienst &#40;Seite Eingabe&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)  
  
  