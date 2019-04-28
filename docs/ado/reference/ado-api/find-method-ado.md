---
title: Find-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Find
- Recordset15::Find
helpviewer_keywords:
- Find method [ADO]
ms.assetid: 55c9810a-d8ca-46c2-a9dc-80e7ee7aa188
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e71776a43aa338246b4acb3b4d9f620c19234f0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028136"
---
# <a name="find-method-ado"></a>Find-Methode (ADO)
Sucht eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) für die Zeile, die die angegebenen Kriterien erfüllt. Optional kann die Richtung der Suche, Startzeile und Offset von der Startzeile angegeben werden. Wenn die Kriterien erfüllt sind, wird die aktuelle Zeilenposition auf den gefundenen Datensatz festgelegt. Andernfalls wird die Position festgelegt, oder zum Ende (Start) von der **Recordset**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Find (Criteria, SkipRows, SearchDirection, Start)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Kriterien*  
 Ein **Zeichenfolge** -Wert, der eine Anweisung, die der Name der Spalte, einen Vergleichsoperator und einen Wert mit angeben, in die Suche enthält.  
  
 *SkipRows*  
 Optional *.* Ein **lange** Wert, dessen Standardwert ist 0 (null), der angibt, den Zeilenoffset aus der aktuellen Zeile oder *starten* Lesezeichen aus, um die Suche zu starten. Standardmäßig beginnt die Suche in der aktuellen Zeile.  
  
 *SearchDirection*  
 Optional *.* Ein [SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md) Wert, der angibt, ob die Suche auf die aktuelle Zeile oder die nächste verfügbare Zeile in die Richtung für die Suche beginnen soll. Eine Suche nicht erfolgreiche beendet wird, am Ende der **Recordset** lautet der Wert **AdSearchForward**. Bei einer nicht erfolgreiche Suche wird am Anfang der **Recordset** lautet der Wert **AdSearchBackward**.  
  
 *Start*  
 Dies ist optional. Ein **Variant** Lesezeichen, das als Anfangsposition für die Suche funktioniert.  
  
## <a name="remarks"></a>Hinweise  
 Kann nur ein einzelner Spaltennamen angegeben werden, *Kriterien*. Diese Methode unterstützt keine Suche nach mehreren Spalten.  
  
 Der Vergleichsoperator im *Kriterien* möglicherweise "**>**"(größer als),"**\<**" (kleiner als), "=" (gleich), "> =" (größer als oder gleich) "< =" (kleiner als oder gleich), "<>" (ungleich), oder "like" (Mustervergleich).  
  
 Der Wert in *Kriterien* kann eine Zeichenfolge, eine Gleitkommazahl oder ein Datum sein. Zeichenfolgenwerte werden in einfache Anführungszeichen oder "#" (Nummernzeichen) ein (z. B. "State ="WA"" oder "Status = #WA #"). Date-Werte als "#" (Nummernzeichen) ein Trennzeichen (z. B. "Start_date > #7/22/97 #"). Diese Werte können Stunden, Minuten und Sekunden an, dass Zeitstempel enthalten, sollten keine Millisekunden oder kommt es zu Fehlern.  
  
 Wenn der Vergleichsoperator "like" ist, darf der Zeichenfolgenwert ein Sternchen (*), um die einem oder mehreren Vorkommen eines beliebigen Zeichens oder einer Teilzeichenfolge suchen. Z. B. "werde Zustand wie\*'" Maine und Massachusetts. Sie können auch führende und nachfolgende Sternchen, eine Teilzeichenfolge innerhalb der Werte finden. Z. B. "State wie"\*als\*"" übereinstimmt, Alaska Arkansas und Massachusetts.  
  
 Sternchen können nur am Ende einer Zeichenfolge für die Kriterien oder am Anfang und Ende einer Kriterienzeichenfolge verwendet werden, wie oben gezeigt. Sie können nicht das Sternchen als führender Platzhalter verwenden ("* str'), oder als eine eingebettete Platzhalter ('s\*R"). Dadurch wird einen Fehler.  
  
> [!NOTE]
>  Wenn eine aktuelle Zeilenposition vor dem Aufruf nicht festgelegt ist, wird ein Fehler auftreten **finden**. Jede Methode, die Position der Zeile, z. B. legt [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), aufgerufen werden soll, bevor **finden**.  
  
> [!NOTE]
>  Aufrufen der **finden** Methode für ein Recordset, und die aktuelle Position im Recordset auf dem letzten Datensatz oder ein Dateiende (EOF) ist, wird dort nicht alles. Aufrufen, müssen Sie die **MoveFirst** Methode, um die aktuelle Position/Cursor auf den Anfang des Recordset-Objekts festzulegen.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Suchen Sie die Methode – Beispiel (VB)](../../../ado/reference/ado-api/find-method-example-vb.md)   
 [Index-Eigenschaft](../../../ado/reference/ado-api/index-property.md)   
 [Optimieren Sie die dynamische Eigenschaft (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [Seek-Methode](../../../ado/reference/ado-api/seek-method.md)
