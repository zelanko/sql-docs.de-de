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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ffa741a68b646f0d0ee23be265f7d368b663cbbf
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928715"
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
  
 Ein Reader-Objekt  
  
 *length*  
  
 Die Länge des Datenstroms.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateCharacterStream-Methode wird von der updateCharacterStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode werden Unicode-Zeichen aus einem Reader-Objekt an ausgewählte Text- und Binärspalten übergeben. Hierzu zählen alle Textspalten sowie Spalten vom Typ "binary", "varbinary", "varbinary(max)", "image" und "XML", aber keine UDT-Spalten.  
  
 Entspricht die Länge des Streams nicht der Angabe im *length*-Parameter, wird vom JDBC-Treiber beim Aktualisieren oder Einfügen der Zeile eine Ausnahme ausgelöst.  
  
 Ist die Länge des Streams nicht bekannt, kann der *length*-Parameter auf „–1“ festgelegt werden, um anzugeben, dass der Stream unabhängig von seiner Länge akzeptiert werden soll. Bei „sqljdbc4.jar“ empfiehlt sich die Verwendung der JDBC 4.0-Methode [updateCharacterStream &#40;int, java.io.Reader&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-int-java-io-reader.md), wenn von der Anwendung versucht wird, die Spalte aus einem Stream mit unbekannter Länge zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateCharacterStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
