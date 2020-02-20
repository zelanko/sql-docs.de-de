---
title: getServerName-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 487d214dbdd6974442749dd0cff6ac24fe9d1977
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979951"
---
# <a name="getservername-method-sqlserverdatasource"></a>getServerName-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String-Objekt**, das den Servernamen oder NULL enthält, sofern kein Wert festgelegt ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Servername ist der Hostname des Zielcomputers, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird. Ist die getServerName-Eigenschaft nicht festgelegt, wird von getServerName der Standardwert (NULL) zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
