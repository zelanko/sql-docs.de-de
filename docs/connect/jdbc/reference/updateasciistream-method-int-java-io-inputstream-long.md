---
title: updateAsciiStream-Methode (java.lang.String, java.io.InputStream, long)
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 143bff3e-2b5c-485d-9529-1c2387560094
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 324b8f6ce1bd335ee7f322ffd38a18304423492a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046741"
---
# <a name="updateasciistream-method-int-javaioinputstream-long"></a>updateAsciiStream-Methode (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem ASCII-Datenstromwert mit der angegebenen Anzahl von Bytes.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateAsciiStream(int columnIndex,  
                              java.io.InputStream x,  
                              long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *x*  
  
 Ein InputStream-Objekt.  
  
 *length*  
  
 Die Länge des Datenstroms.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese UpdateAsciiStream-Methode wird von der UpdateAsciiStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode werden ASCII-Zeichen (Bytes) von einem InputStream-Objekt an konvertierbare Zeichenspalten übergeben, bei denen es sich um den ASCII-Bereich „[0x00 – 0x7F]“ von Unicode sowie um die Codepages 874, 932, 936, 949, 950 und 1250 bis 1258 handelt. Von dieser Methode wird eine Konvertierung zur Zielsortierseite vorgenommen. Beim Versuch, eine nicht konvertierbare Zielspalte zu aktualisieren, wird eine Ausnahme ausgelöst. Für Binärspalten werden Rohbytes übergeben.  
  
 Entspricht die Länge des Streams nicht der Angabe im *length*-Parameter, wird vom JDBC-Treiber beim Aktualisieren oder Einfügen der Zeile eine Ausnahme ausgelöst.  
  
 Ist die Länge des Streams nicht bekannt, kann der *length*-Parameter auf „–1“ festgelegt werden, um anzugeben, dass der Stream unabhängig von seiner Länge akzeptiert werden soll. Bei „sqljdbc4.jar“ empfiehlt sich die Verwendung der JDBC 4.0-Methode [updateAsciiStream Method &#40;int, java.io.InputStream&#41;](../../../connect/jdbc/reference/updateasciistream-method-int-java-io-inputstream.md), wenn von der Anwendung versucht wird, die Spalte aus einem Stream mit unbekannter Länge zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [updateAsciiStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
