---
title: ownDeletesAreVisible-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.ownDeletesAreVisible
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2dd6d976-9f8f-4a24-9354-ff239cfd4364
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44672d73e7bd99a83dd0e74559c718d63693bc45
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80914564"
---
# <a name="owndeletesarevisible-method-sqlserverdatabasemetadata"></a>ownDeletesAreVisible-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob die eigenen Löschvorgänge eines Resultsets sichtbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean ownDeletesAreVisible(int type)  
```  
  
#### <a name="parameters"></a>Parameter  
 *type*  
  
 Ein **ganzzahliger** Wert zum Angeben des Resultsettyps, bei dem es sich gemäß Definition in „java.sql.ResultSet“ oder „SQLServerResultSet“ um einen der folgenden Werte handeln kann:  
  
## <a name="javasqlresultset-types"></a>java.sql.ResultSet-Typen  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>SQLServerResultSet-Typen  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert **TRUE** wird zurückgegeben, wenn die Löschvorgänge sichtbar sind. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese ownDeletesAreVisible-Methode wird von der ownDeletesAreVisible-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
