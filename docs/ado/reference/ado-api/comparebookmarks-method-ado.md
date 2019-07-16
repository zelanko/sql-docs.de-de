---
title: CompareBookmarks-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CompareBookmarks
- Recordset20::CompareBookmarks
- Recordset20::raw_CompareBookmarks
helpviewer_keywords:
- CompareBookmarks method [ADO]
ms.assetid: d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0d737c2f031fa3ba630eabb7e52dff0e056c3390
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919596"
---
# <a name="comparebookmarks-method-ado"></a>CompareBookmarks-Methode (ADO)
Vergleicht zwei Lesezeichen aus, und gibt Sie eine Angabe über das Verhältnis der jeweiligen Werte zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = recordset.CompareBookmarks(Bookmark1, Bookmark2)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine [CompareEnum](../../../ado/reference/ado-api/compareenum.md) Wert, der die relative Zeilenposition von zwei Datensätzen von Textmarken dargestellt angibt.  
  
#### <a name="parameters"></a>Parameter  
 *Bookmark1*  
 Das Lesezeichen der ersten Zeile.  
  
 *Bookmark2*  
 Das Lesezeichen der zweiten Zeile.  
  
## <a name="remarks"></a>Hinweise  
 Lesezeichen müssen anwenden, auf die gleiche [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt oder ein **Recordset** Objekt und dessen [Klon](../../../ado/reference/ado-api/clone-method-ado.md). Sie können nicht zuverlässig Lesezeichen von anderen vergleichen **Recordset** Objekte, selbst wenn sie aus der gleichen Quelle oder der Befehl erstellt wurden. Auch können Sie vergleichen, Lesezeichen für eine **Recordset** Objekt, dessen zugrunde liegenden Anbieter keine Vergleiche unterstützt.  
  
 Ein Lesezeichen identifiziert eindeutig eine Zeile in einer **Recordset** Objekt. Verwenden der [Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md) -Eigenschaft der aktuellen Zeile des Lesezeichens abgerufen.  
  
 Da der Datentyp eines Lesezeichens für jeden Anbieter spezifisch ist, werden als ADO macht eine **Variant**. SQL Server-Lesezeichen sind z. B. vom Typ DBTYPE_R8 (**doppelte**). ADO macht diesen Typ als eine **Variant** mit einen Untertyp des **doppelte**.  
  
 Beim Vergleichen von Lesezeichen versucht ADO Umwandlungen nicht. Die Werte werden einfach an den Anbieter übergeben, in dem der Vergleich auftritt. Wenn die Lesezeichen zum Übergeben der **CompareBookmarks** Methode, die in Variablen für die unterschiedlichen Typen gespeichert sind, können sie die folgenden Typenkonfliktfehler generieren: "Argumente des falschen Typs sind, sind außerhalb des zulässigen Bereichs, oder in Konflikt miteinander."  
  
 Ein Lesezeichen, das nicht gültig oder nicht korrekt ist, verursacht einen Fehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CompareBookmarks-Methode – Beispiel (VB)](../../../ado/reference/ado-api/comparebookmarks-method-example-vb.md)   
 [CompareBookmarks-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/comparebookmarks-method-example-vc.md)   
 [Bookmark-Eigenschaft (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)
