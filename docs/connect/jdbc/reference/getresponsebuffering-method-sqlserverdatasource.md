---
title: GetResponseBuffering-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getResponseBuffering()
apilocation:
- SQLServerDataSource.getResponseBuffering()
apitype: Assembly
ms.assetid: 19585a93-88a4-415e-a20e-12ba58cddeaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f63ae057278b996b02b42668c3ad97bcf7b3f50
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645468"
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>getResponseBuffering-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Antwortpuffermodus für dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Zeichenfolge** , enthält einen Kleinbuchstaben **vollständige** oder **adaptive**.  
  
## <a name="remarks"></a>Remarks  
 Der Wert **full** gibt an, dass zur Laufzeit das gesamte Ergebnis vom Server gelesen wird.  
  
 Der Wert **adaptive** gibt an, dass im Bedarfsfall die geringstmögliche Menge an Daten gepuffert wird. Der **adaptive**-Wert ist der Standardpuffermodus.  
  
 Weitere Informationen zur Verwendung von des antwortpuffermodus finden Sie unter [Using Adaptive Buffering](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [setResponseBuffering-Methode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
