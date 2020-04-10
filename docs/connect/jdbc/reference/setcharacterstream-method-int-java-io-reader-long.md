---
title: setCharacterStream-Methode (int, java.io.Reader, long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cb6ac7f5-81ae-4cb7-87c8-cbee40d278c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 14b8060d09cf70df8da011fa14add2fac613e1d6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929081"
---
# <a name="setcharacterstream-method-int-javaioreader-long"></a>setCharacterStream-Methode (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das java.io.Reader-Objekt fest, dessen Länge der angegebenen Zeichenanzahl entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                                    java.io.Reader reader,  
                                    long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterIndex*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *reader*  
  
 Das java.io.Reader-Objekt, das die Unicodedaten enthält.  
  
 *length*  
  
 Ein Wert vom Typ **long** zum Angeben der Anzahl von Zeichen im Datenstrom.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setCharacterStream-Methode wird von der setCharacterStream-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
 Entspricht die Länge des Streams nicht der Angabe im *length*-Parameter, wird vom JDBC-Treiber beim Aktualisieren oder Einfügen der Zeile eine Ausnahme ausgelöst.  
  
 Ist die Länge des Streams nicht bekannt, kann der *length*-Parameter auf „–1“ festgelegt werden, um anzugeben, dass der Stream unabhängig von seiner Länge akzeptiert werden soll. Bei „sqljdbc4.jar“ empfiehlt sich die Verwendung der JDBC 4.0-Methode [setCharacterStream-Methode &#40;int, java.io.Reader&#41;](../../../connect/jdbc/reference/setcharacterstream-method-int-java-io-reader.md), wenn von der Anwendung versucht wird, die Spalte aus einem Stream mit unbekannter Länge zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setCharacterStream-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
