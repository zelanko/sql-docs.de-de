---
title: getResponseBuffering-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
ms.openlocfilehash: 4b3e53579b8c95cce0585e9614152053f39cafa8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980431"
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>getResponseBuffering-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Antwortpuffermodus für dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge**, die den kleingeschriebenen Wert **full** oder **adaptive** enthält  
  
## <a name="remarks"></a>Bemerkungen  
 Der Wert **full** gibt an, dass zur Laufzeit das gesamte Ergebnis vom Server gelesen wird.  
  
 Der Wert **adaptive** gibt an, dass im Bedarfsfall die geringstmögliche Menge an Daten gepuffert wird. Der **adaptive**-Wert ist der Standardpuffermodus.  
  
 Weitere Informationen zur Verwendung des Antwortpuffermodus finden Sie unter [Verwenden der adaptiven Pufferung](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [setResponseBuffering-Methode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
