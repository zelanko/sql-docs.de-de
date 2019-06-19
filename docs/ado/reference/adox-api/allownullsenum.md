---
title: AllowNullsEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 53fadcddd49ebf68949da0a7dca3cb37da0b5d93
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708605"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Gibt an, ob Datensätze mit null-Werte indiziert sind.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|Der Index lässt Einträge in denen die Schlüsselspalten null sind. Wenn ein null-Wert in einer Schlüsselspalte eingegeben wird, wird der Eintrag in den Index eingefügt.|  
|**adIndexNullsDisallow**|1|Standard. Der Index lässt sich nicht auf Einträge, in denen die Schlüsselspalten null sind, aus. Wenn ein null-Wert in einer Schlüsselspalte eingegeben wird, tritt ein Fehler auf.|  
|**adIndexNullsIgnore**|2|Bei Einträgen, die null-Schlüssel wird der Index nicht eingefügt werden. Wenn ein null-Wert in einer Schlüsselspalte eingegeben wird, wird der Eintrag ignoriert, und kein Fehler auftritt.|  
|**adIndexNullsIgnoreAny**|4|Der Index werden keine Einträge eingefügt, in denen einige einen null-Wert hat. Für einen Index mit einem mehrspaltigen Schlüssel, wenn in einer Spalte, die ein null-Wert eingegeben wird der Eintrag ignoriert, und kein Fehler auftritt.|  
  
## <a name="applies-to"></a>Gilt für  
 [IndexNulls-Eigenschaft (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
