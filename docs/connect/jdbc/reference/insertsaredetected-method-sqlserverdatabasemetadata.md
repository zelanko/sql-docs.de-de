---
title: InsertsAreDetected-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.insertsAreDetected
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f296cc42-9d26-48c3-a360-bcf51c31f7fb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a681258a2232ed43c1547024f8bc0eff51f42e0d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742828"
---
# <a name="insertsaredetected-method-sqlserverdatabasemetadata"></a>insertsAreDetected-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob das Einfügen einer sichtbaren Zeile durch Aufrufen der [rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md)-Methode der [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse ermittelt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean insertsAreDetected(int type)  
```  
  
#### <a name="parameters"></a>Parameter  
 *type*  
  
 Eine Ganzzahl zum Angeben des Resultsettyps, bei dem es sich gemäß Definition in "java.sql.ResultSet" oder "SQLServerResultSet" um einen der folgenden Werte handeln kann:  
  
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
 **"true"** , wenn die eingefügte Zeile erkannt werden kann. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese InsertsAreDetected-Methode wird von der InsertsAreDetected-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
> [!NOTE]  
>  Von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] werden für Cursortypen keine eingefügten Zeilen ermittelt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
