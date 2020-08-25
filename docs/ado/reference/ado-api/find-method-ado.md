---
description: Find-Methode (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0312fb8a8f91e8b56cb6c29a3a64b3a36bcec69d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775229"
---
# <a name="find-method-ado"></a>Find-Methode (ADO)
Durchsucht ein [Recordset](./recordset-object-ado.md) nach der Zeile, die die angegebenen Kriterien erfüllt. Optional können die Suchrichtung, die Anfangs Zeile und der Offset der Anfangs Zeile angegeben werden. Wenn die Kriterien erfüllt sind, wird die aktuelle Zeilen Position für den gefundenen Datensatz festgelegt. Andernfalls wird die Position auf das Ende (oder den Anfang) des **Recordsets**festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Find (Criteria, SkipRows, SearchDirection, Start)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Kriterien*  
 Ein **Zeichen** folgen Wert, der eine-Anweisung enthält, die den Spaltennamen, den Vergleichs Operator und den Wert angibt, der in der Suche verwendet werden soll.  
  
 *Skiprows*  
 Optional. Ein **Long** -Wert, dessen Standardwert 0 (null) ist, der den Zeilen Offset aus der aktuellen Zeile oder dem *Start* Lesezeichen angibt, um die Suche zu starten. Standardmäßig wird die Suche in der aktuellen Zeile gestartet.  
  
 *Suchrichtung*  
 Optional. Ein [SearchDirectionEnum](./searchdirectionenum.md) -Wert, der angibt, ob die Suche mit der aktuellen Zeile oder der nächsten verfügbaren Zeile in der Suchrichtung beginnen soll. Eine fehlgeschlagene Suche wird am Ende des **Recordsets** angehalten, wenn der Wert **adsearchforward**lautet. Eine nicht erfolgreiche Suche wird am Anfang des **Recordsets** angehalten, wenn der Wert **adsearchrückwärts**lautet.  
  
 *Starten*  
 Optional. Ein **Variant** -Lesezeichen, das als Startposition für die Suche fungiert.  
  
## <a name="remarks"></a>Bemerkungen  
 In den *Kriterien*kann nur ein einspaltige Name angegeben werden. Diese Methode unterstützt keine Suchvorgänge mit mehreren Spalten.  
  
 Der Vergleichs Operator in den *Kriterien* kann " **>** " (größer als), "* * \<**" (less than), "=" (equal), "> =" (größer als oder gleich), "<=" (kleiner als oder gleich), "<>" (nicht gleich) oder "like" (Muster Vergleich) sein.  
  
 Der Wert in den *Kriterien* kann eine Zeichenfolge, eine Gleit Komma Zahl oder ein Datum sein. Zeichen folgen Werte werden durch einfache Anführungszeichen oder #-Zeichen (Nummern Zeichen) getrennt (z. b. "State = ' WA '" oder "State = #WA #"). Datumswerte werden durch die Zeichen "#" (Nummern Zeichen) getrennt (z. b. "start_date > #7/22/97 #"). Diese Werte können Stunden, Minuten und Sekunden enthalten, um Zeitstempel anzugeben, Sie sollten jedoch keine Millisekunden enthalten, oder es werden Fehler auftreten.  
  
 Wenn der Vergleichs Operator "like" ist, kann der Zeichen folgen Wert ein Sternchen (*) enthalten, um eine oder mehrere Vorkommen eines beliebigen Zeichens oder einer Teil Zeichenfolge zu suchen. Beispiel: "State like es" \* entspricht "Maine and Massachusetts". Sie können auch führende und nachfolgende Sternchen verwenden, um eine Teil Zeichenfolge zu finden, die in den Werten enthalten ist. Beispielsweise entspricht "State like" \* As " \* " Alaska, Arkansas und Massachusetts.  
  
 Sternchen können nur am Ende einer Kriterienzeichenfolge oder am Anfang und am Ende einer Kriterienzeichenfolge verwendet werden, wie oben gezeigt. Sie können das Sternchen nicht als führenden Platzhalter ("* str") oder als eingebetteten Platzhalter (" \* r") verwenden. Dies führt zu einem Fehler.  
  
> [!NOTE]
>  Wenn eine aktuelle Zeilen Position vor dem Aufrufen von **Find**nicht festgelegt ist, tritt ein Fehler auf. Jede Methode, die die Zeilen Position festlegt, [wie z](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md). b. "", sollte vor dem Aufrufen von " **Find**" aufgerufen werden.  
  
> [!NOTE]
>  Wenn Sie die **Find** -Methode für ein Recordset aufzurufen und die aktuelle Position im Recordset den letzten Datensatz oder das Ende der Datei (EOF) enthält, werden Sie nichts finden. Sie müssen die Methode " **muvefirst** " aufzurufen, um die aktuelle Position/den Cursor auf den Anfang des Recordsets festzulegen.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Find Method-Beispiel (VB)](./find-method-example-vb.md)   
 [Index-Eigenschaft](./index-property.md)   
 [Optimieren von Eigenschaften-Dynamic (ADO)](./optimize-property-dynamic-ado.md)   
 [Seek-Methode](./seek-method.md)