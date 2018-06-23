---
title: Importieren von Berichten aus Microsoft Access (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
caps.latest.revision: 39
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: ec0461f278bfe6556d4a1fa221d5b33426d8ed01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148779"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Importieren von Berichten aus Microsoft Access (Reporting Services)
  In Berichts-Designer importieren Sie Berichte aus einer [!INCLUDE[msCoName](../includes/msconame-md.md)] Access-Datenbank oder ein Projekt. Hierfür muss Access 2002 oder höher auf dem Computer, auf dem der Berichts-Designer installiert ist, installiert sein.  
  
 Bei Verwendung der Importfunktion werden alle Berichte in der Datenbank- oder Projektdatei importiert. Enthält die Access-Datei zahlreiche Berichte, ist es möglicherweise sinnvoll, ein separates Berichtsprojekt zum Importieren der Berichte zu erstellen und dann die einzelnen RDL-Dateien im Hauptberichtsprojekt zu öffnen. Sie können die Berichte nach dem Import in den Berichts-Designer bearbeiten.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt nicht alle Access-Berichtsobjekte. Elemente, die nicht konvertiert werden werden angezeigt, der **Aufgabenliste** Fenster. Weitere Informationen finden Sie unter [Access-Berichtsfunktionen unterstützt &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>So importieren Sie Berichte aus Microsoft Access  
  
1.  Öffnen oder erstellen Sie ein Projekt, in das Sie die Berichte importieren möchten.  
  
2.  Auf der **Projekt** Sie im Menü **Berichte importieren**, und klicken Sie dann auf **Microsoft Access**. Alternativ können Sie mit der rechten Maustaste des Projekts im Projektmappen-Explorer, zeigen Sie auf **Berichte importieren**, und klicken Sie dann auf **Microsoft Access**.  
  
3.  In der **öffnen** Dialogfeld wählen die Access-Datenbank (.mdb, .accdb) oder ein Projekt (.adp), die die Berichte enthält, und klicken Sie dann auf **öffnen**. Es werden alle Berichte aus der Datenbank- oder Projektdatei importiert und im Berichtsordner im Projektmappen-Explorer aufgeführt.  
  
4.  Überprüfen Sie die **Aufgabenliste** Fenster nach Erstellungsfehlern. Anzeigen der **Aufgabenliste** geöffnete Fenster die **Ansicht** Sie im Menü **Weitere Fenster**, und klicken Sie dann auf **Aufgabenliste**.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  