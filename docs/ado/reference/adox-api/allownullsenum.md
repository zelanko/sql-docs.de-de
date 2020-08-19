---
description: AllowNullsEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 058df53811bfbb48005f1f9c6f08f38410bc54cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440502"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Gibt an, ob Datensätze mit NULL-Werten indiziert werden.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adindexnullsallow**|0|Der Index lässt Einträge zu, bei denen die Schlüssel Spalten NULL sind. Wenn ein NULL-Wert in einer Schlüssel Spalte eingegeben wird, wird der Eintrag in den Index eingefügt.|  
|**adIndexNullsDisallow**|1|Standard. Der Index lässt keine Einträge zu, bei denen die Schlüssel Spalten NULL sind. Wenn ein NULL-Wert in einer Schlüssel Spalte eingegeben wird, tritt ein Fehler auf.|  
|**adindexnullsignore**|2|Der Index fügt keine Einträge ein, die NULL-Schlüssel enthalten. Wenn ein NULL-Wert in einer Schlüssel Spalte eingegeben wird, wird der Eintrag ignoriert, und es tritt kein Fehler auf.|  
|**adindexnullsignoreany**|4|Der Index fügt keine Einträge ein, bei denen einige Schlüssel Spalten einen NULL-Wert haben. Bei einem Index mit einem mehrspaltigen Schlüssel wird der Eintrag ignoriert, wenn ein NULL-Wert in einer Spalte eingegeben wird und kein Fehler auftritt.|  
  
## <a name="applies-to"></a>Gilt für  
 [IndexNulls-Eigenschaft (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
