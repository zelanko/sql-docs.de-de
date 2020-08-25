---
description: MaxRecords-Eigenschaft (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4431d9a8af8623150717474cd5429a772f86be8c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774449"
---
# <a name="maxrecords-property-ado"></a>MaxRecords-Eigenschaft (ADO)
Gibt die maximale Anzahl von Datensätzen an, die aus einer Abfrage zu einem [Recordset](./recordset-object-ado.md) zurückgegeben werden sollen.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der die maximale Anzahl zurück zugebender Datensätze angibt, oder gibt ihn zurück. Der Standardwert ist**0**(null), was bedeutet, dass kein Grenzwert gilt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **maxRecords** -Eigenschaft, um die Anzahl der vom Anbieter zurückgegebenen Datensätze aus der Datenquelle einzuschränken. Die Standardeinstellung dieser Eigenschaft ist 0 (null), was bedeutet, dass der Anbieter alle angeforderten Datensätze zurückgibt.  
  
 Die **maxRecords** -Eigenschaft ist Lese-/Schreibzugriff, wenn das **Recordset** geschlossen ist, und schreibgeschützt, wenn es geöffnet ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für MaxRecords-Eigenschaft (VB)](./maxrecords-property-example-vb.md)   
 [MaxRecords-Eigenschaft – Beispiel (VC++)](./maxrecords-property-example-vc.md)