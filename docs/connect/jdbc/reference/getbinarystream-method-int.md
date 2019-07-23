---
title: getBinaryStream-Methode (int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBinaryStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de22a6c4-1ba3-4ed0-91a2-bf235c2ceec3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0add171861f2ea9e021b9f9342968baf1601557
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953701"
---
# <a name="getbinarystream-method-int"></a>getBinaryStream-Methode (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltenindexes in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Binärdatenstrom nicht interpretierter Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.InputStream getBinaryStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein InputStream-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getBinaryStream-Methode wird von der getBinaryStream-Methode in der Java. SQL. Resultset-Schnittstelle angegeben.  
  
 Diese Methode kann nur mit folgenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen verwendet werden: binary, varbinary, varbinary(max) und image. Bei Verwendung dieser Methode mit anderen Datentypen wird eine Ausnahme ausgelöst.  
  
 Nachdem der Wert von der Methode als Datenstrom empfangen wurde, kann der Wert in Ausschnitten aus dem Strom gelesen werden. Diese Methode ist besonders zum Abrufen umfangreicher LONGVARBINARY-Werte geeignet.  
  
> [!NOTE]  
>  Alle Daten im zurückgegebenen Datenstrom müssen vor dem Abrufen des Werts aus einer anderen Spalte gelesen werden. Der nächste Aufruf einer Getter-Methode schließt den Datenstrom implizit. Ein Datenstrom kann ebenfalls 0 (null) zurückgeben, wenn die InputStream.available-Methode aufgerufen wird, egal ob Daten verfügbar sind oder nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getBinaryStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
