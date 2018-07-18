---
title: Kombinieren von Daten (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f570016f39dab2b62276dc3b64ad2c135b05460d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197440"
---
# <a name="combine-data-mds-add-in-for-excel"></a>Kombinieren von Daten (MDS-Add-In für Excel)
  Kombinieren Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]Daten aus zwei Arbeitsblättern, wenn Sie Daten vor der Veröffentlichung vergleichen möchten. In diesem Verfahren kombinieren Sie Daten aus zwei Arbeitsblättern in einem Arbeitsblatt. Anschließend können Sie weitere Vergleiche ausführen und bestimmen, welche Daten ggf. im MDS-Repository veröffentlicht werden sollen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Sie müssen über ein Arbeitsblatt mit von MDS verwalteten Daten verfügen. Weitere Informationen finden Sie unter [Laden von Daten aus MDS in Excel](export-data-to-excel-from-master-data-services.md).  
  
-   Sie müssen über ein Arbeitsblatt verfügen, in dem Daten enthalten sind, die Sie mit von MDS verwalteten Daten kombinieren möchten. Dieses Blatt muss über eine Kopfzeile verfügen.  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a>So kombinieren Sie nicht verwaltete Daten zu einem von MDS verwalteten Blatt  
  
1.  Klicken Sie auf dem Blatt, das die von MDS verwalteten Daten enthält, in der Gruppe **Veröffentlichen und Überprüfen** auf **Daten kombinieren**.  
  
2.  Klicken Sie im Dialogfeld **Daten kombinieren** neben dem Textfeld **Mit MDS-Daten zu kombinierender Bereich** auf das Symbol. Das Dialogfeld wird reduziert.  
  
3.  Klicken Sie auf das Blatt mit den Daten, die Sie kombinieren möchten.  
  
4.  Heben Sie alle Zellen im Blatt hervor, die Sie kombinieren möchten, einschließlich der Kopfzeile.  
  
5.  Klicken Sie im Dialogfeld **Daten kombinieren** auf das Symbol. Das Dialogfeld wird erweitert.  
  
6.  Wählen Sie unter **Entsprechende Spalte**eine Spalte für eine unter der MDS-Entität aufgeführte Spalte aus. Es sind nicht für alle MDS-Spalten entsprechende Spalten erforderlich.  
  
7.  Klicken Sie auf **Kombinieren**. Eine Spalte **QUELLE** wird angezeigt und gibt an, ob die Daten aus MDS oder einer externen Quelle stammen.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   Informationen zur Ermittlung von Ähnlichkeiten zwischen von MDS verwalteten Daten und externen Daten finden Sie unter [Abgleichen ähnlicher Daten (Master Data Services)](match-similar-data-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Laden von Daten &#40;MDS-Add-in für Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Data Quality-Abgleich im MDS-Add-In für Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
