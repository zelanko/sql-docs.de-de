---
title: PageSize-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1db01010fea79d2badaf81588296391d7e2149f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931768"
---
# <a name="pagesize-property-ado"></a>PageSize-Eigenschaft (ADO)
Gibt an, wie viele Datensätze bilden eine Seite in der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** Wert, der angibt, wie viele Datensätze auf einer Seite befinden. Der Standardwert ist **10**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **PageSize** Eigenschaft, um zu bestimmen, wie viele Datensätze eine logische Seite der Daten zu stellen. Eine Seitengröße festlegen, können Sie mit der [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) Eigenschaft, um zu den ersten Datensatz einer bestimmten Seite wechseln. Dies ist nützlich in Szenarien mit Web-Server, wenn Sie den Benutzer auf der Seite durch die Daten, zulassen, eine bestimmte Anzahl von Datensätzen zu einem Zeitpunkt anzuzeigen möchten.  
  
 Diese Eigenschaft kann zu einem beliebigen Zeitpunkt festgelegt werden, und der Wert für die Berechnung des Speicherort des ersten Datensatzes einer bestimmten Seite verwendet werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [AbsolutePage, PageCount und PageSize Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount und PageSize Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
