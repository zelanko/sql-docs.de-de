---
title: Locktypeaufumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ae822794b1b06a975e1cc3cd397b5a5f00036dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918255"
---
# <a name="locktypeenum"></a>LockTypeEnum
Gibt den Typ der Sperre an, die während der Bearbeitung in Datensätzen eingefügt wird  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adlockbatchoptimistische**|4|Gibt Updates für optimistische Batches an. Erforderlich für den Batch Aktualisierungs Modus.|  
|**adlockoptimistisch**|3|Zeigt die optimistische Sperre, Datensatz nach Datensatz. Der Anbieter verwendet die optimistische Sperre und sperrt nur Datensätze, wenn Sie die [Update](../../../ado/reference/ado-api/update-method.md) -Methode aufruft.|  
|**adlockpessimi**|2|Gibt eine pessimistische Sperrung an, Daten Satz nach Datensatz. Der Anbieter übernimmt das, was erforderlich ist, um eine erfolgreiche Bearbeitung der Datensätze sicherzustellen, normalerweise durch Sperren von Datensätzen in der Datenquelle unmittelbar nach der Bearbeitung.|  
|**adlockread Only**|1|Gibt schreibgeschützte Datensätze an. Sie können die Daten nicht ändern.|  
|**adlockunspezifiziert**|-1|Gibt keinen Sperrentyp an. Bei Klonen wird der Klon mit dem gleichen Sperrentyp wie der ursprüngliche erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
|--------------|  
|Adoerums. LockType. batchoptimistischer|  
|Adoerums. LockType. optimistisch|  
|Adoerums. LockType. pessimistisch|  
|Adoerums. LockType. Read Only|  
|Adoerums. LockType. nicht angegeben|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Clone-Methode (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType-Eigenschaft (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute-Ereignis (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
