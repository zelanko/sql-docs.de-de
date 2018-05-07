---
title: UpdateBinaryStream-Methode (Int, java.io.InputStream, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f84cfbe6-ebab-4357-8770-f1db34ecb04f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 382294d0b91ff0b563eb2aac45c18fa3464e5b7d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="updatebinarystream-method-int-javaioinputstream-long"></a>updateBinaryStream-Methode (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem Binärdatenstromwert mit der angegebenen Anzahl von Bytes.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x,  
                               long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **Int** , der den Spaltenindex angibt.  
  
 *x*  
  
 Ein InputStream-Objekt.  
  
 *length*  
  
 Ein **lang** , der die Länge des Streams angibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese UpdateBinaryStream-Methode wird von der UpdateBinaryStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode transferiert Bytes aus einem Objekt InputStream ausgewählt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] binärer Spalten wie Binary, Varbinary, varbinary(max), Image, Xml und Udt. Das Aktualisieren von Zeichenspalten wird für diese Methode nicht unterstützt. Verwenden Sie zum Aktualisieren von Zeichenspalten mit InputStream der [UpdateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) Methode.  
  
 Wenn die Länge des Datenstroms unterscheidet sich von der Angabe in der *Länge* Parameter, der JDBC-Treiber löst eine Ausnahme aus, wenn die Zeile aktualisiert oder eingefügt wird.  
  
 Wenn die Länge des Datenstroms unbekannt ist, ist die *Länge* Parameter kann auf-1 festgelegt werden, um anzugeben, dass der Treiber den Datenstrom unabhängig von seiner Länge akzeptiert werden sollen. Bei "sqljdbc4.jar", empfehlen wir, dass Sie die JDBC 4.0-Methode verwenden [UpdateBinaryStream-Methode &#40;Int, java.io.InputStream&#41; ](../../../connect/jdbc/reference/updatebinarystream-method-int-java-io-inputstream.md) Wenn die Anwendung möchte, um die Spalte aus einem Stream zu aktualisieren, deren Länge unbekannt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [UpdateBinaryStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
