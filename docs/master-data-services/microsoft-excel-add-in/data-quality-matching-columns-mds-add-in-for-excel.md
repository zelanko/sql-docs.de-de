---
title: Spalten für Data Quality-Abgleich (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 9a7303d6791c8320bc2c45fc624c396eaee52e98
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488206"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>Spalten für Data Quality-Abgleich (MDS-Add-In für Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]können Sie nach dem Abgleichen von Daten im Menüband in der Gruppe **Data Quality** auf **Details anzeigen** klicken, um Spalten mit übereinstimmenden Details anzuzeigen.  
  
 In der folgenden Tabelle sind die Spalten aufgeführt, die beim Abgleichen von Daten angezeigt werden.  
  
|Name|Description|  
|----------|-----------------|  
|**CLUSTER_ID**|Ein eindeutiger Bezeichner, der zum Gruppieren ähnlicher Datensätze verwendet wird. Alle Zeilen, die einander ähnlich sind, haben die gleiche **CLUSTER_ID**. Wenn für eine Zeile keine **CLUSTER_ID** angezeigt wird, wurden keine ähnlichen Datensätze gefunden.|  
|**RECORD_ID**|Ein eindeutiger Bezeichner, der zum Identifizieren verwendet wird. Dies ist ein Wert, der zum Identifizieren eines Datensatzes verwendet wird und dem im MDS-Repository gespeicherten Codewert ähnelt. Er wird jeweils automatisch generiert, wenn ein Abgleich durchgeführt wird.|  
|**PIVOT_MARK**|Ein beliebiger Datensatz, mit dem andere Datensätze verglichen werden. Er verfügt nicht über einen Ergebniswert.|  
|**SCORE**|Gibt an, welchen Grad an Ähnlichkeit die Datensätze in der Gruppe mit dem Pivotdatensatz aufweisen. Dieses Ergebnis wird mithilfe von DQS bestimmt. Wenn kein Ergebnis angezeigt wird, ist der Datensatz der Pivotdatensatz für andere Datensätze, oder es wurden keine Übereinstimmungen gefunden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Quality-Abgleich im MDS-Add-In für Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Abgleichen ähnlicher Daten &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)   
 [Datenabgleich](../../data-quality-services/data-matching.md)  
  
  
