---
title: Importieren von Berichten aus Microsoft Access (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 84f74f51879a777ea0b9874f1b124806c109e02f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56022191"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Importieren von Berichten aus Microsoft Access (Reporting Services)
  Sie können im Berichts-Designer Berichte importieren einer [!INCLUDE[msCoName](../includes/msconame-md.md)] Access-Datenbank oder das Projekt. Hierfür muss Access 2002 oder höher auf dem Computer, auf dem der Berichts-Designer installiert ist, installiert sein.  
  
 Bei Verwendung der Importfunktion werden alle Berichte in der Datenbank- oder Projektdatei importiert. Enthält die Access-Datei zahlreiche Berichte, ist es möglicherweise sinnvoll, ein separates Berichtsprojekt zum Importieren der Berichte zu erstellen und dann die einzelnen RDL-Dateien im Hauptberichtsprojekt zu öffnen. Sie können die Berichte nach dem Import in den Berichts-Designer bearbeiten.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt nicht alle Access-Berichtsobjekte. Elemente, die nicht konvertiert werden werden angezeigt, der **Aufgabenliste** Fenster. Weitere Informationen finden Sie unter [unterstützte Zugriffsberichtsfunktionen &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>So importieren Sie Berichte aus Microsoft Access  
  
1.  Öffnen oder erstellen Sie ein Projekt, in das Sie die Berichte importieren möchten.  
  
2.  Auf der **Projekt** Startmenü **Berichte importieren**, und klicken Sie dann auf **Microsoft Access**. Sie können auch mit der rechten Maustaste in des Projekts im Projektmappen-Explorer, zeigen Sie auf **Berichte importieren**, und klicken Sie dann auf **Microsoft Access**.  
  
3.  In der **öffnen** Dialogfeld wählen die Access-Datenbank (.mdb, .accdb) oder die Projektdatei (.adp), die die Berichte enthält, und klicken Sie dann auf **öffnen**. Es werden alle Berichte aus der Datenbank- oder Projektdatei importiert und im Berichtsordner im Projektmappen-Explorer aufgeführt.  
  
4.  Überprüfen Sie die **Aufgabenliste** Fenster nach Erstellungsfehlern. Anzeigen der **Aufgabenliste** geöffnete Fenster die **Ansicht** , zeigen Sie auf **andere Windows**, und klicken Sie dann auf **Aufgabenliste**.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
