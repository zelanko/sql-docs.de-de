---
title: Editor für den Task Webdienst (Seite Eingabe) | Microsoft Docs
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
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8f458f4a2898915102ab2a05b04fb7ba223c5e30
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151605"
---
# <a name="web-service-task-editor-input-page"></a>Editor für den Task 'Webdienst' (Seite Eingabe)
  Mithilfe der Seite **Eingabe** des Dialogfelds **Editor für den Task 'Webdienst'** können Sie den Webdienst, die Webmethode sowie die Werte angeben, die der Webmethode als Eingabe zur Verfügung gestellt werden sollen. Die Werte können entweder durch Eingeben von Zeichenfolgen direkt in die Wert-Spalte oder durch Auswählen von Variablen in der Wert-Spalte bereitgestellt werden.  
  
 Weitere Informationen zu diesem Task finden Sie unter [Webdienst (Task)](control-flow/web-service-task.md).  
  
## <a name="options"></a>Tastatur  
 **Dienst**  
 Wählen Sie aus der Liste einen Webdienst aus, der zum Ausführen der Webmethode verwendet werden soll.  
  
 **Methode**  
 Wählen Sie für den auszuführenden Task eine Webmethode aus der Liste aus.  
  
 **WebMethodDocumentation**  
 Geben Sie eine Beschreibung der Webmethode ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen **(…)** , und geben Sie anschließend im Dialogfeld **Dokumentation der Webmethode** die Beschreibung ein.  
  
 **Name**  
 Führt die Namen der Eingaben in die Webmethode in einer Liste auf.  
  
 **Typ**  
 Führt die Datentypen der Eingaben in einer Liste auf.  
  
> [!NOTE]  
>  Der Webdiensttask unterstützt nur Parameter der folgenden Datentypen: Grundtypen, wie ganze Zahlen und Zeichenfolgen, Arrays und Sequenzen von Grundtypen sowie Enumerationen.  
  
 **Variable**  
 Aktivieren Sie die Kontrollkästchen, um Variablen für das Bereitstellen von Eingaben zu verwenden.  
  
 **ReplTest1**  
 Wenn die Kontrollkästchen für die Variablen aktiviert sind, wählen Sie die Variablen in der Liste aus, um die Eingaben bereitzustellen. Andernfalls geben Sie die Werte ein, die in den Eingaben verwendet werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task Webdienst &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task Webdienst &#40;Seite ausgeben&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)  
  
  