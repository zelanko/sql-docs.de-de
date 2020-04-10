---
title: setCatalog-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a7da2d69f4865eda439b0fb1219be6357c1c40e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929097"
---
# <a name="setcatalog-method-sqlserverconnection"></a>setCatalog-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Katalognamen fest, um einen Teilbereich der Datenbank dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekts auszuwählen, in dem gearbeitet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setCatalog-Methode wird von der setCatalog-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Das *catalog*-Argument wird automatisch von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit Escapezeichen versehen. Bei Verwendung dieser Methode wird die catalog-Eigenschaft für das Connection-Objekt festgelegt. Diese wird auf keine andere Weise implizit festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
