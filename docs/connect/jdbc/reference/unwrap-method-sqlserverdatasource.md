---
title: Unwrap-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eb8abe29-f3ec-4752-a590-1d5dc3e48f08
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00d6f3bd7d512342565da93dd245a0f5714f5021
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682618"
---
# <a name="unwrap-method-sqlserverdatasource"></a>unwrap-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt ein Objekt zurück, das die angegebene Schnittstelle implementiert, um den Zugriff auf die [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifischen Methoden zu ermöglichen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>Parameter  
 *iface*  
  
 Eine Klasse vom Typ T zum Definieren einer Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Objekt, von dem die angegebene Schnittstelle implementiert wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Die [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)-Methode wird von der java.sql.Wrapper-Schnittstelle definiert, die in den JDBC 4.0-Spezifikationen eingeführt wird.  
  
 Von den Anwendungen muss möglicherweise auf [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifische JDBC-API-Erweiterungen zugegriffen werden. Die unwrap-Methode unterstützt das Entpacken in öffentliche, von diesem Objekt erweiterte Klassen, wenn von den Klassen Herstellererweiterungen verfügbar gemacht werden.  
  
 Beim Aufrufen dieser Methode wird das Objekt in die [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse entpackt.  
  
 Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [isWrapperFor-Methode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)   
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
