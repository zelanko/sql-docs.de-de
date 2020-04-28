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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925911"
---
# <a name="boundaries-of-a-recordset"></a>Grenzen eines Recordsets
**Recordset** unterstützt die **BOF** -und **EOF** -Eigenschaften, um den Anfang bzw. das Ende des Datasets zu beschreiben. Sie können sich **BOF** und **EOF** als "Phantom"-Datensätze vorstellen, die am Anfang und am Ende des **Recordsets**positioniert sind. Wenn **BOF** und **EOF**gezählt werden, sieht das Beispiel- **Recordset** nun wie folgt aus:  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|BOF|||  
|7|Die organischen getrockneten Birnen von Onkel Bob|30,0000|  
|14|Dazugeben|23,2500|  
|28|Rssle-Sauerkraut|45,6000|  
|51|Von Manjimup getrocknete Äpfel|53,0000|  
|74|Longlife-Tofu|10,0000|  
|EOF|||  
  
 Wenn ein Cursor nach dem letzten Datensatz verschoben wird, wird **EOF** auf **true**festgelegt. Andernfalls ist der Wert **false**. Ebenso, wenn der Cursor vor dem ersten Datensatz verschoben wird, wird **BOF** auf **true**festgelegt. Andernfalls ist der Wert **false**. Diese Eigenschaften werden häufig verwendet, um Datensätze im DataSet aufzulisten, wie im folgenden JScript-Code Fragment veranschaulicht.  
  
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
  
 Wenn sowohl **BOF** als auch **EOF** **true**sind, ist das **Recordset** -Objekt leer. Beide Eigenschaften werden für ein neu geöffnetes, nicht leeres Recordsetobjekt auf " **false** " **festgelegt** . Mithilfe der **BOF** -Eigenschaft und der **EOF** -Eigenschaft können Sie ermitteln, ob ein **Recordset** -Objekt leer ist, wie im folgenden JScript-Code Fragment dargestellt.  
  
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
  
 Dieses Schema funktioniert für alle Cursor Typen und ist unabhängig von den zugrunde liegenden Anbietern. Wenn Sie versuchen, die leere eines **Recordset** -Objekts zu ermitteln, indem Sie überprüfen, ob der Wert der **RecordCount** -Eigenschaft NULL (0) ist oder nicht, müssen Sie Vorsichtsmaßnahmen ergreifen, um einen geeigneten Cursor und Anbieter zu verwenden, der die Rückgabe der Anzahl von Datensätzen im Ergebnis unterstützt.  
  
 Wenn Sie den letzten verbleibenden Datensatz im **Recordset** -Objekt löschen, bleibt der Cursor in einem unbestimmten Zustand. Die Eigenschaften **BOF** und **EOF** bleiben möglicherweise **falsch** , bis Sie versuchen, den aktuellen Datensatz neu zu positionieren, je nach Anbieter. Weitere Informationen finden Sie unter [Löschen von Datensätzen mit der Delete-Methode](../../../ado/guide/data/deleting-records-using-the-delete-method.md).
