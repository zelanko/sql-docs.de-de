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
ms.openlocfilehash: 5acd8997af6993a49ac4cbcca6e3b4c8bd26acfd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932236"
---
# <a name="maxrecords-property-ado"></a>MaxRecords-Eigenschaft (ADO)
Gibt die maximale Anzahl von Datensätzen an, die aus einer Abfrage zu einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) zurückgegeben werden sollen.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der die maximale Anzahl zurück zugebender Datensätze angibt, oder gibt ihn zurück. Der Standardwert ist**0**(null), was bedeutet, dass kein Grenzwert gilt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **maxRecords** -Eigenschaft, um die Anzahl der vom Anbieter zurückgegebenen Datensätze aus der Datenquelle einzuschränken. Die Standardeinstellung dieser Eigenschaft ist 0 (null), was bedeutet, dass der Anbieter alle angeforderten Datensätze zurückgibt.  
  
 Die **maxRecords** -Eigenschaft ist Lese-/Schreibzugriff, wenn das **Recordset** geschlossen ist, und schreibgeschützt, wenn es geöffnet ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für MaxRecords-Eigenschaft (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [MaxRecords-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   
