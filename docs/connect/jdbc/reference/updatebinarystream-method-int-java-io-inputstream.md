---
title: updateBinaryStream-Methode (int, java.io.InputStream) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8a1b69d4f4e1845b4ec86297c06298c1302becea
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67985371"
---
# <a name="updatebinarystream-method-int-javaioinputstream"></a>updateBinaryStream-Methode (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem Binärdatenstromwert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *x*  
  
 Ein InputStream-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateBinaryStream-Methode wird von der updateBinaryStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Die Verwendung dieser Methode für die Datentypen **image**, **text** und **ntext**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann sich negativ auf die Leistung auswirken.  
  
 Von dieser Methode werden Bytes aus einem InputStream-Objekt an ausgewählte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Binärspalten wie „binary“, „varbinary“, „varbinary(max)“, „image“, „xml“ oder „udt“ übergeben. Das Aktualisieren von Zeichenspalten wird für diese Methode nicht unterstützt. Verwenden Sie die [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)-Methode, um Zeichenspalten mit InputStream zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateBinaryStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
