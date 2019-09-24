---
title: ToString-Methode (DateTimeOffset) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f3acffe6a922084fd63e38a8e212b5cf86d6b278
ms.sourcegitcommit: c0fd28306a3b42895c2ab673734fbae2b56f9291
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096910"
---
# <a name="tostring-method-datetimeoffset"></a>toString-Methode (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt eine Zeichen folgen Darstellung des **DateTimeOffset** -Objekts zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Zeichen folgen Darstellung des **DateTimeOffset** -Objekts.  
  
## <a name="remarks"></a>Remarks  
 Die Zeichenfolge weist folgendes Format auf: `YYYY-MM-DD HH:mm:ss[.fffffff] [+|-]HH:mm`.  
  
 Die Sekundenbruchteile der zurückgegebenen Zeichenfolge werden bis zur angegebenen Genauigkeit mit Nullen aufgefüllt. Beispielsweise wird ein **DateTimeOffset (6)** mit dem Wert "2010-03-10 12:34:56.78-08:00" von "DateTimeOffset. ToString" als "2010-03-10 12:34:56.780000-08:00" formatiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset-Elemente](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
