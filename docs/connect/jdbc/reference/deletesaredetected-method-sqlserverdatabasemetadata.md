---
title: deletesAreDetected-Methode (SQLServerDatabaseMetaData)
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.deletesAreDetected
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 73f3d994-bbd7-43d2-8b64-50057e278983
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6def9d94b1cbfb1b3e6bee07454d5f5adad2392
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786111"
---
# <a name="deletesaredetected-method-sqlserverdatabasemetadata"></a>deletesAreDetected-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob das Löschen einer sichtbaren Zeile durch Aufrufen der [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)-Methode der [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse ermittelt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean deletesAreDetected(int type)  
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
 **"true"** , wenn eine Lücke auf die gelöschte Zeile ersetzt. **"false"** , wenn die gelöschte Zeile entfernt wird.  
  
 Bei Verwendung von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank wird von dieser Methode für TYPE_SS_SCROLL_KEYSET-Cursor der Wert **TRUE** und für alle anderen Resultsettypen der Wert **FALSE** zurückgegeben.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese DeletesAreDetected-Methode wird von der DeletesAreDetected-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
> [!NOTE]  
>  Gelöschte Zeilen werden von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zwar für alle aktualisierbaren Cursortypen erkannt, die Erkennung für Vorwärtscursor und dynamische Cursor ist jedoch kurzlebig.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
