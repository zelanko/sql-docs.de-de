---
title: API-Referenz für den JDBC-Treiber
description: Die technische API-Referenz für die JDBC-Klassen im JDBC-Treiber für SQL Server
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4e1ae9d-18a6-41db-8bd2-9cf0eee4cccb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0e96f8eb6ff2e3f20a5d6804ba3083e668c0f3a7
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391792"
---
# <a name="jdbc-driver-api-reference"></a>API-Referenz für den JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Die von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] bereitgestellte API kann innerhalb von Java-Programmiercode zum Herstellen einer Verbindung und zum Kommunizieren mit einer [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank verwendet werden.



### <a name="javadocio-website-is-primary"></a>Primäre Website „JavaDoc.io“

Die API-Referenzdokumentation für Microsoft JDBC wird zur Anzeige auf der Website „JavaDoc.io“ gehostet. „JavaDoc.io“ ist jetzt die primäre Website für die JDBC-Referenzdokumentation. Die JDBC-Referenzdokumentation auf „JavaDoc.io“ ist unter folgendem Direktlink verfügbar:

- [https://javadoc.io/doc/com.microsoft.sqlserver/mssql-jdbc/](https://javadoc.io/doc/com.microsoft.sqlserver/mssql-jdbc/)

„JavaDoc.io“ enthält die JDBC-Referenzdokumentation ab Version 6.0.

#### <a name="only-legacy-jdbc-documentation-is-here-on-docs"></a>Nur die ältere JDBC-Dokumentation finden Sie hier in der Dokumentation.

Die Artikel zur API-Referenzdokumentation für JDBC hier unter **https://docs.microsoft.com/sql/connect/jdbc/reference/** werden nicht mehr aktualisiert, wenn die JDBC-Klassen für neue Releases aktualisiert werden. Die hier enthaltenen Artikel umfassen jedoch alle Referenzinformationen für die JDBC-Versionen 4.1 und 4.2.

Die Dokumentation für die JDBC-Version 6.0 und einige spätere Versionen sind ebenfalls hier enthalten. Verwenden Sie jedoch für alle Versionen ab 6.0 die Website „JavaDoc.io“.



### <a name="important-notes"></a>Wichtige Hinweise

> [!NOTE]  
>  Konzeptionelle Informationen zur Verwendung des JDBC-Treibers finden Sie unter [Übersicht über den JDBC-Treiber](../../../connect/jdbc/overview-of-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
>  Verwenden Sie den Microsoft JDBC-Treiber 4.2 (oder höher) für SQL Server, um JDBC 4.1- und 4.2-Kompatibilität zu unterstützen. Die vorhergehenden Versionen der Microsoft JDBC-Treiber 4.1 und 4.0 unterstützen die in JDBC 4.1 und 4.2 eingeführten neuen Methoden nicht.  
>   
>  API-Details zur JDBC 4.1-Kompatibilität werden in diesem Abschnitt nicht erörtert. Weitere Informationen finden Sie unter [JDBC 4.1-Kompatibilität für den JDBC-Treiber](../../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md).  
>   
>  API-Details zur JDBC 4.2-Kompatibilität werden in diesem Abschnitt nicht erörtert. Weitere Informationen finden Sie unter [JDBC 4.2-Kompatibilität für den JDBC-Treiber](../../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).  
>   
>  API-Details zur Massenkopierfunktion, die im Microsoft JDBC-Treiber 4.2 für SQL Server zur Verfügung steht, werden in diesem Abschnitt nicht erörtert. Weitere Informationen finden Sie unter [Verwenden von Massenkopieren mit dem JDBC Driver](../../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).  
>   
>  API-Details für das Feature „Always Encrypted“, das ab dem Microsoft JDBC-Treiber 6.0 für SQL Server verfügbar ist, werden in diesem Abschnitt nicht erläutert. Weitere Informationen finden Sie unter [Always Encrypted – API-Referenz für den JDBC-Treiber](../../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  
>   
>  API-Details für das Verwenden von Tabellenwertparametern, das ab dem Microsoft JDBC-Treiber 6.0 für SQL Server verfügbar ist, sind in diesem Abschnitt nicht enthalten. Weitere Informationen finden Sie unter [Verwenden von Tabellenwertparametern](../../../connect/jdbc/using-table-valued-parameters.md).  
>   
>  Der Microsoft JDBC-Treiber 6.4 unterstützt die Kompilierung mit JDK 7.0, 8.0 und 9.0.  
>   
>  Der Microsoft JDBC-Treiber 6.2 unterstützt die Kompilierung mit JDK 7.0 und 8.0.  
>   
>  Die Microsoft JDBC-Treiber 6.0 und 4.2 unterstützen die Kompilierung mit JDK 5.0, 6.0, 7.0 und 8.0.  
>   
>  Der Microsoft JDBC-Treiber 4.1 unterstützt die Kompilierung mit JDK 5.0, 6.0 und 7.0.  



## <a name="interfaces"></a>Schnittstellen  
  
|Schnittstellenname|BESCHREIBUNG|  
|--------------------|-----------------|  
|[ISQLServerCallableStatement-Schnittstelle](../../../connect/jdbc/reference/isqlservercallablestatement-interface.md)|Mit dieser Klasse kann der gespeicherte Prozedurname angegeben werden, der mit Eingabe- und Ausgabeparametern aufgerufen wird.|  
|[ISQLServerConnection-Schnittstelle](../../../connect/jdbc/reference/isqlserverconnection-interface.md)|Stellt eine JDBC-Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank dar.|  
|[SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)|Stellt eine Liste mit spezifischen Eigenschaften für das Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank (unter Verwendung eines [ISQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekts) dar.|  
|[ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)|Stellt die grundlegende Implementierung der JDBC-Funktion für vorbereitete Anweisungen dar.|  
|[ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)|Stellt ein JDBC-Resultset dar.|  
|[ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)|Stellt die grundlegende Implementierung der JDBC-Anweisungsfunktion dar.|
| &nbsp; | &nbsp; |


  
## <a name="classes"></a>Klassen  
  
|Klassenname|BESCHREIBUNG|  
|----------------|-----------------|  
|[DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)|Stellt ein Objekt vom Typ "microsoft.sql.DateTimeOffset" dar.|  
|[SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)|Stellt ein BLOB (Binary Large Object) dar.|  
|[SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)|Implementiert ISQLServerCallableStatement.|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)|Stellt ein CLOB (Character Large Binary Object) dar.|  
|[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)|Implementiert ISQLServerConnectopn.|  
|[SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)|Stellt die physischen Datenbankverbindungen für Verbindungspool-Manager dar.|  
|[SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)|Stellt die Metadaten für die Datenbank dar.|  
|[SQLServerDataSource](../../../connect/jdbc/reference/isqlserverdatasource-interface.md)|Stellt eine Liste mit spezifischen Eigenschaften für das Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank (unter Verwendung eines [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekts) dar.|  
|[SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)|Stellt ein Objektfactory zum Materialisieren von Datenquellen aus der JNDI (Java Naming and Directory Interface) dar.|  
|[SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)|Stellt den JDBC-Treiber dar. Diese Klasse enthält Methoden zum Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank sowie zum Abrufen von Informationen zum JDBC-Treiber.|  
|[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)|Stell die fehlerhafte oder unvollständige Ausführung einer SQL-Anweisung dar.|  
|[SQLServerNClob-Klasse](../../../connect/jdbc/reference/sqlservernclob-class.md)|Stellt ein CLOB (Character Large Binary Object) mit nationalem Zeichensatz dar.|  
|[SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)|Stellt die Metadaten für die Parameter vorbereiteter Anweisungen dar.|  
|[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)|Stellt eine physische Datenbankverbindung in einem Verbindungspool dar.|  
|[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)|Implementiert ISQLServerPreparedStatement.|  
|[SQLServerResource](../../../connect/jdbc/reference/sqlserverresource-class.md)|Stellt eine Ressource für lokalisierte Fehlerzeichenfolgen dar. Diese Klasse dient nur zur internen Verwendung.|  
|[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)|Implementiert ISQLServerResultSet.|  
|[SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)|Stellt die Metadaten der Spalten innerhalb eines Resultsets dar.|  
|[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)|Stellt den Prüfpunkt dar, bis zu dem ein Transaktionsrollback durchgeführt werden kann.|  
|[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)|Implementiert ISQLServerStatement.|  
|[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)|Stellt JDBC-Verbindungen dar, die an verteilten Transaktionen (XA-Transaktionen) beteiligt sein können.|  
|[SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)|Stellt eine intern verwendete Factory für [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)-Objekte dar.|  
|[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)|Stellt ein XAResource-Objekt für die Verwaltung verteilter XA-Transaktionen dar.|
| &nbsp; | &nbsp; |



## <a name="see-also"></a>Weitere Informationen  
 [Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../../connect/jdbc/overview-of-the-jdbc-driver.md)

