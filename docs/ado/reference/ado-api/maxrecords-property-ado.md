---
title: MaxRecords-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 130a67f10e8b7deaf8f48e94f949b43682f61ca1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707628"
---
# <a name="maxrecords-property-ado"></a>MaxRecords-Eigenschaft (ADO)
Gibt die maximale Anzahl von Datensätzen, die zum Zurückgeben einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) aus einer Abfrage.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** Wert, der die maximale Anzahl der zurückzugebenden Datensätze angibt. Standardwert ist 0 (null) (**0**), was bedeutet, dass keine Begrenzung.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **MaxRecords** Eigenschaft, um die Anzahl der Datensätze einzuschränken, die der Anbieter aus der Datenquelle zurückgibt. Die Standardeinstellung dieser Eigenschaft ist 0 (null), was bedeutet, dass alle angeforderten Datensätze, gibt der Anbieter zurück.  
  
 Die **MaxRecords** -Eigenschaft ist Lese-/Schreibzugriff bei der **Recordset** geschlossen ist, und schreibgeschützt, wenn es geöffnet ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [MaxRecords-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [MaxRecords-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   
