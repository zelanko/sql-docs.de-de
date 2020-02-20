---
title: nativeSQL-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.nativeSQL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2188a6e1-792f-47bd-b207-1d01741231b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b4e5d97f3b4b47e111da7c4a9efd9edeb87f168c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67976791"
---
# <a name="nativesql-method-sqlserverconnection"></a>nativeSQL-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Konvertiert die angegebene SQL-Anweisung zur systemeigenen SQL-Grammatik des Datenbankservers.  
  
> [!NOTE]  
>  Diese Methode wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String nativeSQL(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sql*  
  
 Eine **Zeichenfolge**, die eine SQL-Anweisung enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge** mit der konvertierten SQL-Anweisung.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese nativeSQL-Methode wird von der nativeSQL-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
