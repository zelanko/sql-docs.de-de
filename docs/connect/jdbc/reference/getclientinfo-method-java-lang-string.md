---
title: getClientInfo(java.lang.String)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 82dee3b10241abf2cfb014d4617d2ae2c5588eae
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907486"
---
# <a name="getclientinfo-method-javalangstring"></a>getClientInfo-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert einer angegebenen Eigenschaft für Clientinformationen ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>Parameter  
 *name*  
  
 Eine Zeichenfolge mit dem Namen der abzurufenden Eigenschaft für Clientinformationen.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Zeichenfolge mit dem Wert der Eigenschaft für Clientinformationen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getClientInfo-Methode wird von der getClientInfo-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] werden keine Eigenschaften für Clientinformationen unterstützt. Daher gibt diese Methode einen **null**-Wert zurück.  
  
 Entsprechend kann die [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)-Methode der [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Klasse von Anwendungen zum Abrufen einer Liste mit vom Treiber unterstützten Eigenschaften für Clientinformationen verwendet werden. Die [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)-Methode gibt ein leeres Resultset zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getClientInfo-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
