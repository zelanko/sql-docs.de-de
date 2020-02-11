---
title: Importieren von Berichten aus Microsoft Access (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108932"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Importieren von Berichten aus Microsoft Access (Reporting Services)
  In Berichts-Designer können Sie Berichte aus einer Access- [!INCLUDE[msCoName](../includes/msconame-md.md)] Datenbank oder einem-Projekt importieren. Hierfür muss Access 2002 oder höher auf dem Computer, auf dem der Berichts-Designer installiert ist, installiert sein.  
  
 Bei Verwendung der Importfunktion werden alle Berichte in der Datenbank- oder Projektdatei importiert. Enthält die Access-Datei zahlreiche Berichte, ist es möglicherweise sinnvoll, ein separates Berichtsprojekt zum Importieren der Berichte zu erstellen und dann die einzelnen RDL-Dateien im Hauptberichtsprojekt zu öffnen. Sie können die Berichte nach dem Import in den Berichts-Designer bearbeiten.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt nicht alle Access-Berichtsobjekte. Elemente, die nicht konvertiert werden, werden im Fenster **Aufgabenliste** angezeigt. Weitere Informationen finden Sie [unter Supported Access Report Features &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>So importieren Sie Berichte aus Microsoft Access  
  
1.  Öffnen oder erstellen Sie ein Projekt, in das Sie die Berichte importieren möchten.  
  
2.  Zeigen Sie im Menü **Projekt** auf **Berichte importieren**, und klicken Sie dann auf **Microsoft Access**. Alternativ klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, zeigen Sie auf **Berichte importieren**, und klicken Sie dann auf **Microsoft Access**.  
  
3.  Wählen Sie im Dialogfeld **Öffnen** die Access-Datenbank (. mdb,. accdb) oder das Projekt (. ADP) aus, die die Berichte enthält, und klicken Sie dann auf **Öffnen**. Es werden alle Berichte aus der Datenbank- oder Projektdatei importiert und im Berichtsordner im Projektmappen-Explorer aufgeführt.  
  
4.  Überprüfen Sie das **Aufgabenliste** Fenster auf Buildfehler. Um das Fenster **Aufgabenliste** anzuzeigen, öffnen Sie das Menü **Ansicht** , zeigen Sie auf **Weitere Fenster**, und klicken Sie dann auf **Aufgabenliste**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
