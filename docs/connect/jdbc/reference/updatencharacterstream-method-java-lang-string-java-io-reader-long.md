---
title: updateNCharacterStream Method String – Reader – long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: db0a96a8-248f-4664-9c13-f480f309ab91
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0582672a9203e8efbae1de9767ff4c24a10919f9
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928350"
---
# <a name="updatencharacterstream-method-javalangstring-javaioreader-long"></a>updateNCharacterStream-Methode (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem Zeichendatenstromwert mit der angegebenen Anzahl von Bytes.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateNCharacterStream(java.lang.String columnLabel,  
                                    java.io.Reader reader,  
                                    long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnLabel*  
  
 Eine **Zeichenfolge**, die die Spaltenbezeichnung enthält.  
  
 *reader*  
  
 Ein Reader-Objekt  
  
 *length*  
  
 Die Länge des Datenstroms.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateNCharacterStream-Methode wird von der updateNCharacterStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode übergibt Unicode-Zeichen aus einem Reader-Objekt an ausgewählte **nchar**-, **nvarchar(max)** -, **ntext**- und **xml**-Spalten. Bei Verwendung dieser Methode für andere Datentypspalten wird eine Ausnahme ausgelöst.  
  
 Entspricht die Länge des Streams nicht der Angabe im *length*-Parameter, wird vom JDBC-Treiber beim Aktualisieren oder Einfügen der Zeile eine Ausnahme ausgelöst.  
  
 Ist die Länge des Streams nicht bekannt, kann der *length*-Parameter auf „–1“ festgelegt werden, um anzugeben, dass der Stream unabhängig von seiner Länge akzeptiert werden soll. Bei „sqljdbc4.jar“ empfiehlt sich die Verwendung der JDBC 4.0-Methode [updateNCharacterStream &#40;java.lang.String, java.io.Reader&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-java-lang-string-java-io-reader.md), wenn von der Anwendung versucht wird, die Spalte aus einem Stream mit unbekannter Länge zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateNCharacterStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
