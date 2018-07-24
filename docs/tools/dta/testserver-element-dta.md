---
title: TestServer-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TestServer element
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c57ed1ae96ac57377a3ed7154873a9c76c828b0c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036728"
---
# <a name="testserver-element-dta"></a>TestServer-Element (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Gibt den Testserver an, der beim Optimieren eines Produktionsservers verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|**string**, unbegrenzte Länge.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Einmalige Verwendung pro **TuningOptions** -Element möglich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Reduzieren der Optimierungsauslastung des Produktionsservers](../../relational-databases/performance/reduce-the-production-server-tuning-load.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 
  [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
