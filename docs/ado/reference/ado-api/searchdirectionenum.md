---
title: SearchDirectionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f8926e932317096cb3891cc8c480164268751cea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917000"
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Gibt die Richtung einer Daten Satz Suche innerhalb eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)an.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adsearchrückwärts**|-1|Sucht rückwärts und beendet am Anfang des **Recordsets**. Wenn keine Entsprechung gefunden wird, wird der Daten Satz Zeiger bei [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)positioniert.|  
|**adsearchforward**|1|Sucht vorwärts und beendet am Ende des **Recordsets**. Wenn keine Entsprechung gefunden wird, wird der Daten Satz Zeiger auf [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)positioniert.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
|--------------|  
|Adoumums. SearchDirection. rückwärts|  
|Adoumums. SearchDirection. Forward|  
  
## <a name="applies-to"></a>Gilt für  
 [Find-Methode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
