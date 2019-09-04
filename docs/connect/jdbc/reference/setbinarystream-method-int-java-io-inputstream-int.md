---
title: setBinaryStream-Methode (int, java.io.InputStream, int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fd6be063-08eb-40cf-9201-5a9f62387726
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0265f06d589ea89b38f995f8a9616fd22bcf92ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975274"
---
# <a name="setbinarystream-method-int-javaioinputstream-int"></a>setBinaryStream-Methode (int, java.io.InputStream, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf den angegebenen Eingabedatenstrom mit der angegebenen Anzahl von Bytes fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setBinaryStream(int n,  
                                  java.io.InputStream x,  
                                  int length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *n*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *x*  
  
 Ein InputStream-Objekt.  
  
 *length*  
  
 Ein Wert vom Typ **int** zum Angeben der Anzahl von Bytes.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setBinaryStream-Methode wird von der setBinaryStream-Methode in der Java. SQL. PreparedStatement-Schnittstelle angegeben.  
  
 Entspricht die Länge des Streams nicht der Angabe im *length*-Parameter, wird vom JDBC-Treiber beim Aktualisieren oder Einfügen der Zeile eine Ausnahme ausgelöst.  
  
 Ist die Länge des Streams nicht bekannt, kann der *length*-Parameter auf „–1“ festgelegt werden, um anzugeben, dass der Stream unabhängig von seiner Länge akzeptiert werden soll. Bei „sqljdbc4.jar“ empfiehlt sich die Verwendung der JDBC 4.0-Methode [setBinaryStream-Methode &#40;int, java.io.InputStream&#41;](../../../connect/jdbc/reference/setbinarystream-method-int-java-io-inputstream.md), wenn von der Anwendung versucht wird, die Spalte aus einem Stream mit unbekannter Länge zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setBinaryStream-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
