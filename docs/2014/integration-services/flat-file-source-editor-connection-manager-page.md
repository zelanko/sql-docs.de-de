---
title: Quellen-Editor für Flatfiles (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43a0251b63d7a0519a2a19b6bec4c5117f0dcef0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425487"
---
# <a name="flat-file-source-editor-connection-manager-page"></a>Quellen-Editor für Flatfiles (Seite Verbindungs-Manager)
  Wählen Sie auf der Seite **Verbindungs-Manager** des Dialogfelds **Quellen-Editor für Flatfiles** den Verbindungs-Manager aus, den die Flatfilequelle verwenden soll. Die Flatfilequelle liest die Daten aus einer Textdatei, die in den Formaten mit Trennzeichen, fester Breite oder mit gemischten Inhalten vorliegen kann.  
  
 Eine Flatfilequelle kann einen der folgenden Typen von Verbindungs-Manager verwenden:  
  
-   Einen Verbindungs-Manager für Flatfiles, wenn es sich bei der Quelle um eine einzelne Flatfile handelt. Weitere Informationen finden Sie unter [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
-   Einen Verbindungs-Manager für mehrere Flatfiles, wenn es bei der Quelle um mehrere Flatfiles handelt und der Datenflusstask sich in einem Schleifencontainer wie dem For-Schleifencontainer befindet. In jeder Schleife des Containers werden von der Flatfilequelle Daten vom nächsten Dateinamen geladen, der vom Verbindungs-Manager für mehrere Flatfiles bereitgestellt wird. Weitere Informationen finden Sie unter [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).  
  
 Weitere Informationen zur Flatfilequelle finden Sie unter [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Optionen  
 **Verbindungs-Manager für Flatfiles**  
 Wählen Sie einen vorhandenen Verbindungs-Manager aus der Liste aus, oder erstellen Sie einen neuen Verbindungs-Manager, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Verbindungs-Manager-Editor für Flatfiles** einen neuen Verbindungs-Manager.  
  
 **NULL-Werte aus der Quelle als NULL-Werte im Datenfluss beibehalten**  
 Geben Sie an, ob NULL-Werte erhalten werden, wenn Daten extrahiert werden. Der Standardwert dieser Eigenschaft ist **false**. Wenn dieser Wert f`alse` ist, ersetzt die Flatfilequelle die NULL-Werte aus den Quelldaten mit entsprechenden Standardwerten für jede Spalte, z. B. mit leeren Zeichenfolgen in Zeichenfolgenspalten und Nullen in numerischen Spalten.  
  
 **Vorschau**  
 Zeigen Sie mithilfe des Dialogfelds **Datenansicht** eine Vorschau der Ergebnisse an. In der Vorschau können bis zu 200 Zeilen angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Quellen-Editor für Flatfiles &#40;Seite "Spalten"&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md)   
 [Quellen-Editor für Flatfiles &#40;Seite Fehlerausgabe&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Verbindungs-Manager für Flatfiles](connection-manager/file-connection-manager.md)  
  
  
