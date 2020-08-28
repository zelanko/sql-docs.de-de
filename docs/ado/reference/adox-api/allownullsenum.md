---
description: AllowNullsEnum
title: AllowNullsEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c2d21b4a7e4de67e45210f11598a7cf3a2a99b9e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985541"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Gibt an, ob Datensätze mit NULL-Werten indiziert werden.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adindexnullsallow**|0|Der Index lässt Einträge zu, bei denen die Schlüssel Spalten NULL sind. Wenn ein NULL-Wert in einer Schlüssel Spalte eingegeben wird, wird der Eintrag in den Index eingefügt.|  
|**adIndexNullsDisallow**|1|Standard. Der Index lässt keine Einträge zu, bei denen die Schlüssel Spalten NULL sind. Wenn ein NULL-Wert in einer Schlüssel Spalte eingegeben wird, tritt ein Fehler auf.|  
|**adindexnullsignore**|2|Der Index fügt keine Einträge ein, die NULL-Schlüssel enthalten. Wenn ein NULL-Wert in einer Schlüssel Spalte eingegeben wird, wird der Eintrag ignoriert, und es tritt kein Fehler auf.|  
|**adindexnullsignoreany**|4|Der Index fügt keine Einträge ein, bei denen einige Schlüssel Spalten einen NULL-Wert haben. Bei einem Index mit einem mehrspaltigen Schlüssel wird der Eintrag ignoriert, wenn ein NULL-Wert in einer Spalte eingegeben wird und kein Fehler auftritt.|  
  
## <a name="applies-to"></a>Gilt für  
 [IndexNulls-Eigenschaft (ADOX)](./indexnulls-property-adox.md)