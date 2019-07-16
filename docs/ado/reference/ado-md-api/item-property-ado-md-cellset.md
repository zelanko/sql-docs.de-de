---
title: Item-Eigenschaft (ADO MD Cellset) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Item
- Cellset::Item
helpviewer_keywords:
- Item property [ADO MD]
ms.assetid: 0e93d79b-b12e-4e98-889e-c2dfcca20fd0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c7fbce544cac188db7ed3b3d40478aa63809405
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949623"
---
# <a name="item-property-ado-md-cellset"></a>Item-Eigenschaft (ADO MD Cellset)
Ruft eine Zelle aus einem [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) unter Verwendung seiner Koordinaten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set  
Cell = Cellset.Item ( Positions)  
```  
  
## <a name="parameters"></a>Parameter  
 *Positionen*  
 Ein **VariantArray** von Werten, die eine Zelle eindeutig angeben. *Positionen* kann einen der folgenden sein:  
  
-   Ein Array von Zahlen für position  
  
-   Ein Array von Elementnamen  
  
-   Die Ordnungsposition  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Element** zurückzugebende Eigenschaft eine [Zelle](../../../ado/reference/ado-md-api/cell-object-ado-md.md) -Objekt in ein [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Objekt. Wenn die **Element** Eigenschaft kann nicht gefunden, die Zelle, entspricht die *Positionen* -Argument, ein Fehler auftritt.  
  
 Die **Element** -Eigenschaft ist die Standardeigenschaft für die **Cellset** Objekt. Die folgende Syntaxformen sind austauschbar:  
  
```  
  
Cellset.Item ( Positions )Cellset ( Positions )  
```  
  
## <a name="remarks"></a>Hinweise  
 Die *Positionen* Argument gibt an, welche Zelle zurückgegeben. Sie können die Zelle nach Ordnungsposition oder durch die Position, an jeder Achse angeben. Wenn Sie die Zelle anhand der Position, an jeder Achse angeben möchten, können Sie den numerischen Wert der Position oder die Namen der Elemente für jede Position angeben.  
  
 Die Ordnungsposition ist eine Zahl, die Identifizierung einer Zelle innerhalb der **Cellset**. Grundsätzlich werden Zellen in nummeriert eine **Cellset** als ob die **Cellset** wurden eine *p*-, eindimensionales Array, in denen *p* ist die Anzahl der Achsen. Die Zellen werden in zeilengerichteter Reihenfolge adressiert. Es folgt die Formel zum Berechnen der Ordinalzahl einer Zelle:  
  
 Wenn Elementnamen übergeben, werden als Formatzeichenfolgen auf **Element**, müssen die Elemente in aufsteigender Reihenfolge der numerischen Achse Bezeichner aufgeführt werden. Innerhalb einer Achse die Elemente müssen in aufsteigender Reihenfolge aufgeführt werden, –, also der äußersten Dimension-Element wird zuerst angegeben, gefolgt von einem Mitglied der internen Dimensionen. Jede Dimension durch eine separate Zeichenfolge dargestellt werden soll, und die Liste der Member-Zeichenfolgen sollten durch Kommas getrennt werden.  
  
> [!NOTE]
>  Abrufen von Zellen nach Elementnamen möglicherweise nicht vom Datenanbieter unterstützt werden. Finden Sie in der Dokumentation für Ihren Anbieter, um weitere Informationen.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Cell-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)
