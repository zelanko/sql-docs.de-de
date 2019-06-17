---
title: Anwenden von Geschäftsregeln (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 32819a694769092c255c4b2ed918dd8fde99362e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65482605"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Anwenden von Geschäftsregeln (MDS-Add-In für Excel)
  Wenden Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] Geschäftsregeln an, wenn Sie Daten überprüfen und bestätigen möchten, dass sie gültig sind. Sie können Überprüfungen korrigieren und die Daten erneut veröffentlichen.  
  
> [!NOTE]  
>  Die Datenüberprüfung findet automatisch statt, wenn Sie Daten veröffentlichen. Weitere Informationen finden Sie unter [Gespeicherte Überprüfungsprozedur &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
-   Sie müssen über ein aktives Arbeitsblatt mit von MDS verwalteten Daten verfügen.  
  
### <a name="to-apply-business-rules"></a>So wenden Sie Geschäftsregeln an  
  
1.  Klicken Sie in der Gruppe **Veröffentlichen und Validieren** auf **Regeln anwenden**.  
  
    > [!NOTE]  
    >  Die Anzahl der Elemente (Zeilen), die gleichzeitig überprüft werden, richtet sich nach einer Einstellung in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Weitere Informationen finden Sie unter [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules).  
  
2.  Die Daten werden anhand von Geschäftsregeln überprüft, und zwei Statusspalten werden angezeigt. Wenn diese Spalten nicht automatisch angezeigt werden, klicken Sie in der Gruppe **Veröffentlichen und Validieren** auf **Status anzeigen** , um sie anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Daten &#40;MDS-Add-in für Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
