---
title: updateCharacterStream-Methode (java.io.Reader, long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c426b0e3-2f9d-425a-b7da-1d0325e292d1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7a3747df1ff5f64b0f7ebdfa1ff383eb497a8d0a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784222"
---
# <a name="updatecharacterstream-method-int-javaioreader-long"></a>updateCharacterStream-Methode (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem Zeichendatenstromwert mit der angegebenen Anzahl von Zeichen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateCharacterStream(int columnIndex,  
                                  java.io.Reader x,  
                                  long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *x*  
  
 Ein Readerobjekt.  
  
 *length*  
  
 Die Länge des Datenstroms.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese UpdateCharacterStream-Methode wird von der UpdateCharacterStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode werden Unicode-Zeichen aus einem Reader-Objekt an ausgewählte Text- und Binärspalten übergeben. Hierzu zählen alle Textspalten sowie Spalten vom Typ "binary", "varbinary", "varbinary(max)", "image" und "XML", aber keine UDT-Spalten.  
  
 Entspricht die Länge des Streams nicht der Angabe im *length*-Parameter, wird vom JDBC-Treiber beim Aktualisieren oder Einfügen der Zeile eine Ausnahme ausgelöst.  
  
 Ist die Länge des Streams nicht bekannt, kann der *length*-Parameter auf „–1“ festgelegt werden, um anzugeben, dass der Stream unabhängig von seiner Länge akzeptiert werden soll. Bei „sqljdbc4.jar“ empfiehlt sich die Verwendung der JDBC 4.0-Methode [updateCharacterStream &#40;int, java.io.Reader&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-int-java-io-reader.md), wenn von der Anwendung versucht wird, die Spalte aus einem Stream mit unbekannter Länge zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateCharacterStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
