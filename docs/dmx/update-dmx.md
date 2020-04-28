---
title: Update (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2d28df68512f9c97faebf3ee00b2aa34a2b8d1a5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028671"
---
# <a name="update-dmx"></a>UPDATE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ändert die **NODE_CAPTION** Spalte im Modell Data Mining.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
UPDATE <model>.CONTENT  
SET NODE_CAPTION='new caption'  
[WHERE <condition expression>]  
```  
  
## <a name="arguments"></a>Argumente  
 *model*  
 Ein Modellbezeichner.  
  
 *neue Beschriftung*  
 Eine Zeichenfolge, die den neuen Namen für die **NODE_CAPTION** Spalte enthält.  
  
 *Bedingungs Ausdruck*  
 (Optional) Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel ändert die **Update** -Anweisung den Standardnamen `Cluster 1`für Cluster `001` in den aussagekräftigeren Namen. `Likely Customers`  
  
```  
UPDATE [TM Clustering].CONTENT  
SET NODE_CAPTION= 'Likely Customers'  
WHERE NODE_UNIQUE_NAME = '001'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
