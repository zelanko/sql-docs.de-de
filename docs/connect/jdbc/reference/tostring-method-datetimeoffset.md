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
manager: jroth
ms.openlocfilehash: 64186b6add766a21e0881fb6b3f59d49048334e8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778589"
---
# <a name="tostring-method-datetimeoffset"></a>toString-Methode (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt eine Zeichenfolgendarstellung der **DateTimeOffset** Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Zeichenfolgendarstellung der **DateTimeOffset** Objekt.  
  
## <a name="remarks"></a>Remarks  
 Die Zeichenfolge weist das Format *JJJJ*-*MM*-*tt ** Hh*:*mm*:*ss*[. *FFFFFFF*] [+ |-]*Hh*:*mm*.  
  
 Die Sekundenbruchteile der zurückgegebenen Zeichenfolge werden bis zur angegebenen Genauigkeit mit Nullen aufgefüllt. Z. B. eine **datetimeoffset(6)** mit einem Wert von "2010-03-10-12:34:56.78-08: 00" wird formatiert werden, indem DateTimeOffset.toString als "2010-03-10-12:34:56.780000-08: 00".  
  
## <a name="see-also"></a>Weitere Informationen  
 [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset-Elemente](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
