---
title: Grenzen eines Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- EOF property [ADO], boundaries of a Recordset
- Recordset object [ADO], boundaries of a Recordset
- BOF property [ADO], boundaries of a Recordset
ms.assetid: c0dd4a0f-478d-4c5e-b5d5-7535f211d064
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8f4efddad1b55ce57c62ce52418539ec06599bb8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925911"
---
# <a name="boundaries-of-a-recordset"></a>Grenzen eines Recordsets
**Recordset** unterstützt die **BOF** und **EOF** Eigenschaften, die Anfang und Ende des Datasets skizziert. Sie können sich vorstellen **BOF** und **EOF** als "phantom"-Datensätze, die am Anfang und Ende des positioniert sind die **Recordset**. Zählen von **BOF** und **EOF**, unser Beispiel **Recordset** sieht nun wie folgt:  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|BOF|||  
|7|Onkel Bobs Trockenbirnen|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle Sauerkraut|45.6000|  
|51|Manjimup getrocknet Äpfel|53.0000|  
|74|Longlife Tofu|10.0000|  
|EOF|||  
  
 Wechselt von ein Cursor hinter dem letzten Datensatz, **EOF** nastaven NA hodnotu **"true"** ist, andernfalls der Wert ist **"false"** . Auf ähnliche Weise, wenn der Cursor springt vor dem ersten Datensatz, **BOF** nastaven NA hodnotu **"true"** ist, andernfalls der Wert ist **"false"** . Diese Eigenschaften werden häufig zum Aufzählen der Datensätze im Dataset verwendet, wie im folgenden JScript-Codefragment veranschaulicht.  
  
```  
while (objRecordset.EOF != true)   
{  
   // Work on the current record.  
   ...  
   // Advance the cursor forward to the next record.  
   objRecordset.MoveNext();  
}  
or  
while (objRecordset.BOF != true)   
{  
   // Work on the current record.  
   ...  
   // Move the cursor to the previous record.  
   objRecordset.MovePrevious();  
}  
```  
  
 Wenn beide **BOF** und **EOF** sind **"true"** , **Recordset** Objekt leer ist. Beide Eigenschaften werden **"false"** für ein neu geöffneten, nicht leeres **Recordset** Objekt. Können Sie die **BOF** und **EOF** Eigenschaften zusammen, um zu bestimmen, ob eine **Recordset** Objekt ist leer oder nicht, wie in der folgenden JScript-Codefragment.  
  
```  
if (objRecordset.EOF == true && objRecordset.BOF == true)  
{  
   WScript.Echo("we got an empty dataset.");  
}  
else  
{  
   WScript.Echo("we got a full dataset.");  
}  
```  
  
 Dieses Schema ist für alle Arten von Cursor und ist unabhängig von der zugrunde liegenden Anbieter. Wenn Sie versuchen, um zu bestimmen, die überprüft, der eine **Recordset** Objekt, indem Sie überprüfen, ob die **RecordCount** -Eigenschaftswert ist 0 (null) oder nicht, Sie müssen Vorsichtsmaßnahmen ergreifen, um einen geeigneten Cursor und Anbieter verwenden, unterstützen Sie die Anzahl der Datensätze im Ergebnis zurückgegeben.  
  
 Wenn Sie den letzten verbleibenden Datensatz im Löschen der **Recordset** Objekt ist, bleibt der Cursor in einem unbestimmten Zustand befindet. Die **BOF** und **EOF** Eigenschaften bleiben möglicherweise **"false"** , bis Sie versuchen, den aktuellen Datensatz neu positionieren, je nach den Anbieter. Weitere Informationen finden Sie unter [löschen Datensätze, die mit der Delete-Methode](../../../ado/guide/data/deleting-records-using-the-delete-method.md).
