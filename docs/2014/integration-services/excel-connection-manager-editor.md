---
title: Excel-Verbindungs-Manager-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d9951d9bfe7e95499c2b967e6329d206cdc4aa44
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437407"
---
# <a name="excel-connection-manager-editor"></a>Verbindungs-Manager-Editor für Excel
  Mithilfe des Dialogfelds **Verbindungs-Manager-Editor für Excel** können Sie einer vorhandenen oder neuen [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] -Arbeitsmappendatei eine Verbindung hinzufügen.  
  
 Weitere Informationen zum Excel-Verbindungs-Manager finden Sie unter [Excel Connection Manager](connection-manager/excel-connection-manager.md).  
  
> [!NOTE]  
>  Es ist nicht möglich, eine Verbindung mit einer kennwortgeschützten Excel-Datei herzustellen.  
  
## <a name="options"></a>Optionen  
 **Excel-Dateipfad**  
 Geben Sie den Pfad und den Dateinamen einer vorhandenen oder neuen Excel-Arbeitsmappendatei (XLS-Datei) ein.  
  
> [!WARNING]  
>  Der **Ziel-Editor für Excel** erstellt die Excel-Datei automatisch, wenn Sie eine **Excel-Verbindung** auswählen, die auf eine neue/nicht vorhandene Datei verweist, und klicken Sie dann auf **neu** für **Name der Excel-Tabelle**.  
  
 **Durchsuchen**  
 Verwenden Sie das Dialogfeld **Öffnen** , um zu dem Ordner zu navigieren, in dem die Excel-Datei vorhanden ist oder in dem Sie die neue Datei erstellen möchten.  
  
 **Excel-Version**  
 Geben Sie die Version von Microsoft Excel an, die zum Erstellen der Datei verwendet wurde.  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|Excel 97-2003|Die Datei wurde mithilfe von Excel 97 oder höher erstellt.|  
|Excel 3,0|Die Datei wurde mithilfe von Excel 3,0 erstellt.|  
|Excel 4,0|Die Datei wurde mithilfe von Excel 4.0 erstellt.|  
|Excel 5,0|Die Datei wurde mithilfe von Excel 95 (7.0) erstellt.|  
  
 **Erste Zeile enthält Spaltennamen**  
 Geben Sie an, ob die erste Zeile der Daten in der ausgewählten Arbeitsmappe Spaltennamen enthält. Der Standardwert für diese Option ist **True**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Schleife durch Excel-Dateien und Tabellen mit einem Foreach-Schleifencontainer](control-flow/foreach-loop-container.md)  
  
  
