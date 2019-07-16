---
title: PageCount-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ea893a019ab6d1333cecc5da5f1f66928467adfc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931786"
---
# <a name="pagecount-property-ado"></a>PageCount-Eigenschaft (ADO)
Gibt an, wie viele Seiten mit Daten der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **lange** hodnota ukazuje, die Anzahl der Seiten in der **Recordset**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **PageCount** Eigenschaft, um zu bestimmen, wie viele Seiten mit Daten in sind die **Recordset** Objekt. *Seiten* sind Gruppen von Datensätzen, deren Größe entspricht, der [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) Einstellung der Eigenschaft. Auch wenn die letzte Seite unvollständig ist, da weniger als Datensätze die **PageSize** Wert, es zählt als eine zusätzliche Seite in der **PageCount** Wert. Wenn die **Recordset** Objekt unterstützt diese Eigenschaft nicht, wird des Werts-1 gibt an, dass die **PageCount** nicht bestimmt werden.  
  
 Finden Sie unter den **PageSize** und [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) Eigenschaften für Weitere Informationen zur Seitenfunktionalität.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [AbsolutePage, PageCount und PageSize Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount und PageSize Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageSize-Eigenschaft (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [RecordCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
