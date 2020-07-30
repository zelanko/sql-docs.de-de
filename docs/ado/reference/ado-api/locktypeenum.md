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
author: rothja
ms.author: jroth
ms.openlocfilehash: e609a51d6b9f42cb6101ff485633302193757fbd
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242650"
---
# <a name="locktypeenum"></a>LockTypeEnum
Gibt den Typ der Sperre an, die während der Bearbeitung in Datensätzen eingefügt wird  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adlockbatchoptimistische**|4|Gibt Updates für optimistische Batches an. Erforderlich für den Batch Aktualisierungs Modus.|  
|**adlockoptimistisch**|3|Zeigt die optimistische Sperre, Datensatz nach Datensatz. Der Anbieter verwendet die optimistische Sperre und sperrt nur Datensätze, wenn Sie die [Update](../../../ado/reference/ado-api/update-method.md) -Methode aufruft.|  
|**adlockpessimi**|2|Gibt eine pessimistische Sperrung an, Daten Satz nach Datensatz. Der Anbieter übernimmt das, was erforderlich ist, um eine erfolgreiche Bearbeitung der Datensätze sicherzustellen, normalerweise durch Sperren von Datensätzen in der Datenquelle unmittelbar nach der Bearbeitung.|  
|**adlockread Only**|1|Gibt schreibgeschützte Datensätze an. Sie können die Daten nicht ändern.|  
|**adlockunspezifiziert**|-1|Gibt keinen Sperrentyp an. Bei Klonen wird der Klon mit dem gleichen Sperrentyp wie der ursprüngliche erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums.LockType.BATchoptimistische|  
|Adoerums. LockType. optimistisch|  
|Adoerums. LockType. pessimistisch|  
|Adoerums. LockType. Read Only|  
|Adoerums. LockType. nicht angegeben|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Clone-Methode (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)  
        [LockType-Eigenschaft (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)  
    :::column-end:::
    :::column:::
        [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)  
        [WillExecute-Ereignis (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)  
    :::column-end:::
:::row-end:::
