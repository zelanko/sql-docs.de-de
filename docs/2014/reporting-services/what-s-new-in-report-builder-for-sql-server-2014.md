---
title: Was&#39;Neues in Berichts-Generator für SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 15e4e4a90232f4db1b83b3a09d45589e6fcdeb8d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226880"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a>Was&#39;Neues in Berichts-Generator für SQLServer 2014
  In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] werden mehrere [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Funktionen eingeführt.  
  
 Informationen zu Funktionen in dieser Version für andere [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Produkten und Technologien finden Sie unter [Neuigkeiten in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
> [!TIP]  
>  Die neuesten Informationen und Ressourcen zu neuen Funktionen in dieser Version finden Sie unter [zusätzliche Informationen zu neuerungen in SQL Server Reporting Services (SSRS)](http://go.microsoft.com/fwlink/?LinkId=207147).  
  
##  <a name="ExcelRenderer"></a> Excel-Renderer für Microsoft Excel 2007-2010 und Microsoft Excel 2003  
 Die neu in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aufgenommene [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Excel-Renderingerweiterung rendert einen Bericht als Excel-Dokument, das mit [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 und [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 kompatibel ist, wenn das Microsoft Office Compatibility Pack für Word, Excel und PowerPoint installiert ist. Das Format ist Office Open XML, und die Dateierweiterung der Dateien lautet XLSX.  
  
 Diese Excel-Renderingerweiterung werden die Einschränkungen der früheren Version, die mit Excel 2003 kompatible entfernt. Im Folgenden werden die Verbesserungen der Renderingerweiterung aufgeführt:  
  
-   Die maximale Anzahl an Zeilen pro Arbeitsblatt beträgt 1.048.576.  
  
-   Die maximale Anzahl an Spalten pro Arbeitsblatt beträgt 16.384.  
  
-   Die Anzahl von in einem Arbeitsblatt zulässigen Farben beträgt ungefähr 16 Millionen (24-Bit-Farbe).  
  
-   Die ZIP-Komprimierung stellt kleinere Dateigrößen bereit.  
  
 Weitere Informationen finden Sie unter [Exportieren nach Microsoft Excel &#40;Berichts-Generator und SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md) (Exportieren nach Microsoft Excel (Berichts-Generator und SSRS)).  
  
##  <a name="WordRenderer"></a> Word-Renderer für Microsoft Word 2007-2010 und Microsoft Word 2003  
 Die neu in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aufgenommene [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]Word-Renderingerweiterung rendert einen Bericht als Word-Dokument, das mit [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 und [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003 kompatibel ist, wenn das [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Compatibility Pack für Word, Excel und PowerPoint installiert ist. Das Format ist Office Open XML, und die Dateierweiterung der Dateien lautet DOCX.  
  
 Der Word-Renderer ermöglicht nicht nur den Zugriff auf die neuen Funktionen, die in Word 2007-2010 für exportierte Berichte verfügbar sind, sondern stellt mit dem DOCX-Format meistens auch kleinere Dateien zur Verfügung. Die mit dem Word-Renderer exportierten Berichte sind normalerweise deutlich kleiner als die gleichen Berichte, die mit dem Word 2003-Renderer exportiert werden.  
  
 Weitere Informationen finden Sie unter [Exportieren nach Microsoft Word &#40;Berichts-Generator und SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
