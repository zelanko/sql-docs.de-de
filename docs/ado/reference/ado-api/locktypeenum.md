---
description: LockTypeEnum
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
ms.openlocfilehash: 7ba912f082cbd621d2d2205c6505e8c2be309bec
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774549"
---
# <a name="locktypeenum"></a>LockTypeEnum
Gibt den Typ der Sperre an, die während der Bearbeitung in Datensätzen eingefügt wird  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adlockbatchoptimistische**|4|Gibt Updates für optimistische Batches an. Erforderlich für den Batch Aktualisierungs Modus.|  
|**adlockoptimistisch**|3|Zeigt die optimistische Sperre, Datensatz nach Datensatz. Der Anbieter verwendet die optimistische Sperre und sperrt nur Datensätze, wenn Sie die [Update](./update-method.md) -Methode aufruft.|  
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
        [Clone-Methode (ADO)](./clone-method-ado.md)  
        [LockType-Eigenschaft (ADO)](./locktype-property-ado.md)  
    :::column-end:::
    :::column:::
        [Open-Methode (ADO-Recordset)](./open-method-ado-recordset.md)  
        [WillExecute-Ereignis (ADO)](./willexecute-event-ado.md)  
    :::column-end:::
:::row-end:::