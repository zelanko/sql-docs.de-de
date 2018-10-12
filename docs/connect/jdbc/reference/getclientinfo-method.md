---
title: GetClientInfo-Methode () | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a89f2afa50b0ee1b83e72c05bf675d49dac662ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757768"
---
# <a name="getclientinfo-method-"></a>getClientInfo-Methode ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Liste mit dem Namen und dem aktuellen Wert der einzelnen Clientinformationseigenschaften ab, die vom JDBC-Treiber unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Properties-Objekt mit dem Namen und dem aktuellen Wert der einzelnen Clientinformationseigenschaften, die vom JDBC-Treiber unterstützt werden.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetClientInfo-Methode wird von der GetClientInfo-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] werden keine Eigenschaften für Clientinformationen unterstützt. Daher gibt diese Methode ein leeres Eigenschaftenobjekt zurück.  
  
 Entsprechend kann die [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)-Methode der [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Klasse von Anwendungen zum Abrufen einer Liste mit vom Treiber unterstützten Eigenschaften für Clientinformationen verwendet werden. Die [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)-Methode gibt ein leeres Resultset zurück.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getClientInfo-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
