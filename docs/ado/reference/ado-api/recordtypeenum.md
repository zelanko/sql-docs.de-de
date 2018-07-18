---
title: RecordTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c583db7cb8d91090357a26f027478485d087d9f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281219"
---
# <a name="recordtypeenum"></a>RecordTypeEnum
Gibt den Typ des [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|Gibt eine *einfache* Datensatz (enthält keine untergeordneten Knoten).|  
|**adCollectionRecord**|1|Gibt eine *Auflistung* Datensatz (enthält untergeordnete Knoten).|  
|**adRecordUnknown**|-1|Gibt an, dass der Typ dieses **Datensatz** ist unbekannt.|  
|**adStructDoc**|2|Gibt an, eine spezielle Art von *Auflistung* Datensatz, der COM-strukturierte Dokumente.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [RecordType-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)
