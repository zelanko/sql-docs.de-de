---
title: Systemanforderungen für den JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 447792bb-f39b-49b4-9fd0-1ef4154c74ab
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 244f5383add437b8bd4985045bd9edc8538805e3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66798286"
---
# <a name="system-requirements-for-the-jdbc-driver"></a>Systemanforderungen für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Für den Zugriff auf Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] mit dem [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] müssen die folgenden Komponenten auf dem Computer installiert sein:

- [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ([Download](download-microsoft-jdbc-driver-for-sql-server.md))
- Java-Laufzeitumgebung (Java Runtime Environment, JRE)

## <a name="java-runtime-environment-requirements"></a>Anforderungen der Java-Laufzeitumgebung  

 Ab dem Microsoft JDBC-Treiber 7.2 für SQL Server werden das JDK 11.0 (Java Development Kit) und die JRE 11.0 (Java Runtime Environment) unterstützt.
 
 Ab dem Microsoft JDBC-Treiber 7.0 für SQL Server werden das JDK 10.0 (Java Development Kit) und die JRE 10.0 (Java Runtime Environment) unterstützt.

 Ab dem Microsoft JDBC-Treiber 6.4 für SQL Server werden das JDK 9.0 (Java Development Kit) und die JRE 9.0 (Java Runtime Environment) unterstützt.

 Ab dem Microsoft JDBC-Treiber 4.2 für SQL Server werden das JDK 8.0 (Java Development Kit) und die JRE 8.0 (Java Runtime Environment) unterstützt. Die Unterstützung für die Java Database Connectivity (JDBC) Spec-API wurde nun auf die JDBC 4.1 und 4.2-API ausgeweitet.
  
 Ab dem Microsoft JDBC-Treiber 4.1 für SQL Server werden das JDK 7.0 (Java Development Kit) und die JRE 7.0 (Java Runtime Environment) unterstützt.
  
 Seit der Einführung von [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] wurde die JDBC-Treiberunterstützung für die API der JDBC- (Java Database Connectivity-)Spezifikation um die JDBC 4.0-API erweitert. Die JDBC-API 4.0 wurde als Bestandteil des JDK 6.0 und der JRE 6.0 eingeführt. JDBC 4.0 ist eine Obermenge der JDBC 3.0-API.
  
 Bei der Bereitstellung von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unter Windows- und UNIX-Betriebssystemen müssen Sie entsprechend eines der folgenden Installationspakete verwenden: *sqljdbc_\<version> _enu.exe* oder *sqljdbc_\<version>_enu.tar.gz*. Weitere Informationen zum Bereitstellen des JDBC-Treibers finden Sie unter dem Thema [Bereitstellen des JDBC-Treibers](../../connect/jdbc/deploying-the-jdbc-driver.md).  

**Microsoft JDBC-Treiber 7.2 für SQL Server:**  

  Der JDBC-Treiber 7.2 enthält in jedem Installationspaket zwei JAR-Klassenbibliotheken: **mssql-jdbc-7.2.2.jre8.jar** und **mssql-jdbc-7.2.2.jre11.jar**.

  Der JDBC-Treiber 7.2 ist für die Verwendung und Unterstützung aller wichtigen virtuellen Java-Computer konzipiert. Er wird jedoch nur mit OpenJDK 8.0, OpenJDK 11.0, Azul Zulu JRE 8.0 und Azul Zulu JRE 11.0 getestet.
  
  Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den beiden im Microsoft JDBC-Treiber 7.2 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
  |JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-7.2.2.jre8.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Bei Verwendung von JRE 7.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 7.2 umfassen Folgendes: JDK 11-Unterstützung, Authentifizierung mit einer verwalteten Active Directory-Dienstidentität (Active Directory Managed Service Identity, MSI), OSGi-Unterstützung und SQLServerError-APIs. |    
|mssql-jdbc-7.2.2.jre11.jar|4.3|10|Erfordert die JRE 11.0. Bei Verwendung von JRE 10.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 7.2 umfassen Folgendes: JDK 11-Unterstützung, Authentifizierung mit einer verwalteten Active Directory-Dienstidentität (Active Directory Managed Service Identity, MSI), OSGi-Unterstützung und SQLServerError-APIs. |    


  Der JDBC-Treiber 7.2 steht auch im zentralen Maven-Repository zur Verfügung und kann einem Maven-Projekt hinzugefügt werden, indem Sie in der POM.XML-Datei den folgenden Code hinzufügen:  
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.2.jre11</version>
</dependency>
```
 
**Microsoft JDBC-Treiber 7.0 für SQL Server**  

  Der Microsoft JDBC-Treiber 7.0 enthält in jedem Installationspaket zwei JAR-Klassenbibliotheken: **mssql-jdbc-7.0.0.jre8.jar** und **mssql-jdbc-7.0.0.jre10.jar**.

  Der JDBC-Treiber 7.0 ist für die Verwendung und Unterstützung aller wichtigen virtuellen Java-Computer konzipiert. Er wird jedoch nur mit OpenJDK 8.0 und 10.0 getestet.
  
  Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den beiden im Microsoft JDBC-Treiber 7.0 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
  |JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-7.0.0.jre8.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Bei Verwendung von JRE 7.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 7.0 umfassen Folgendes: JDK 10-Unterstützung, aktualisierte Standardkonformitätsstufe in JDBC 4.2-Spezifikationen, Unterstützung von räumlichen Datentypen, cancelQueryTimeout-Verbindungseigenschaft, Methoden für Anforderungsgrenzen, useBulkCopyForBatchInsert-Verbindungseigenschaft, Datenermittlungs- und -klassifizierungsinformationen, UTF-8-Funktionserweiterung und CityHash-Unterstützung. |    
|mssql-jdbc-7.0.0.jre10.jar|4.3|10|Erfordert die Java Runtime Environment (JRE) 10.0. Bei Verwendung von JRE 9.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 7.0 umfassen Folgendes: JDK 10-Unterstützung, aktualisierte Standardkonformitätsstufe in JDBC 4.2-Spezifikationen, Unterstützung von räumlichen Datentypen, cancelQueryTimeout-Verbindungseigenschaft, Methoden für Anforderungsgrenzen, useBulkCopyForBatchInsert-Verbindungseigenschaft, Datenermittlungs- und -klassifizierungsinformationen, UTF-8-Funktionserweiterung und CityHash-Unterstützung. |    


  Der JDBC-Treiber 7.0 steht auch im zentralen Maven-Repository zur Verfügung und kann einem Maven-Projekt hinzugefügt werden, indem Sie in der POM.XML-Datei den folgenden Code hinzufügen:  
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
</dependency>
```
  
**Microsoft JDBC-Treiber 6.4 für SQL Server:**  

  Der Microsoft JDBC-Treiber 6.4 enthält in jedem Installationspaket drei JAR-Klassenbibliotheken: **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar** und **mssql-jdbc-6.4.0.jre9.jar**.

  Der JDBC-Treiber 6.4 ist für die Verwendung und Unterstützung aller wichtigen virtuellen Java-Computer konzipiert. Er wird jedoch nur mit OpenJDK 7.0, 8.0 und 9.0 getestet.
  
  Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den drei im Microsoft JDBC-Treiber 6.4 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
  |JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-6.4.0.jre7.jar|4.1|7|Erfordert die Java-Laufzeitumgebung( JRE) Version 7.0. Bei Verwendung von JRE 6.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 6.4 umfassen Folgendes: Azure AD-Authentifizierung für Linux, Prinzipal/Kennwort-Methode für Kerberos, automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, eingeschränkte Kerberos-Delegierung, Abfragetimeout, Sockettimeout und erneute Verwendung des vorbereiteten Anweisungshandles. |  
|mssql-jdbc-6.4.0.jre8.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Bei Verwendung von JRE 7.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 6.4 umfassen Folgendes: Azure AD-Authentifizierung für Linux, Prinzipal/Kennwort-Methode für Kerberos, automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, eingeschränkte Kerberos-Delegierung, Abfragetimeout, Sockettimeout und erneute Verwendung des vorbereiteten Anweisungshandles. |    
|mssql-jdbc-6.4.0.jre9.jar|4.3|9|Erfordert die Java-Laufzeitumgebung (JRE), Version 9.0. Bei Verwendung von JRE 8.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 6.4 umfassen Folgendes: Azure AD-Authentifizierung für Linux, Prinzipal/Kennwort-Methode für Kerberos, automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, eingeschränkte Kerberos-Delegierung, Abfragetimeout, Sockettimeout und erneute Verwendung des vorbereiteten Anweisungshandles. |

Der JDBC-Treiber 6.4 steht auch im zentralen Maven-Repository zur Verfügung und kann einem Maven-Projekt hinzugefügt werden, indem Sie in der POM.XML-Datei den folgenden Code hinzufügen: 

 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre9</version>
</dependency>
```

**Microsoft JDBC-Treiber 6.2 für SQL Server:**  
  
  Der Microsoft JDBC-Treiber 6.2 enthält in jedem Installationspaket drei JAR-Klassenbibliotheken: **mssql-jdbc-6.2.2.jre7.jar** und **mssql-jdbc-6.2.2.jre8.jar**. 
  
 Der JDBC-Treiber 6.2 ist für die Verwendung und Unterstützung aller wichtigen virtuellen Java-Computer konzipiert. Er wird jedoch nur mit der Sun JRE 5.0, 6.0, 7.0 und 8.0 getestet.
  
 Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den beiden in den Microsoft JDBC-Treibern 6.0 und 4.2 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
|JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|
|mssql-jdbc-6.2.2.jre7.jar|4.1|7|Erfordert die Java-Laufzeitumgebung( JRE) Version 7.0. Bei Verwendung von JRE 6.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 6.2 umfassen Folgendes: Azure AD-Authentifizierung für Linux, Prinzipal/Kennwort-Methode für Kerberos, automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, eingeschränkte Kerberos-Delegierung, Abfragetimeout, Sockettimeout und erneute Verwendung des vorbereiteten Anweisungshandles. |  
|mssql-jdbc-6.2.3.jre8.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Bei Verwendung von JRE 7.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in Version 6.2 umfassen Folgendes: Azure AD-Authentifizierung für Linux, Prinzipal/Kennwort-Methode für Kerberos, automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, eingeschränkte Kerberos-Delegierung, Abfragetimeout, Sockettimeout und erneute Verwendung des vorbereiteten Anweisungshandles|    

  Der JDBC-Treiber 6.2 steht auch im zentralen Maven-Repository zur Verfügung und kann einem Maven-Projekt hinzugefügt werden, indem Sie in der POM.XML-Datei den folgenden Code hinzufügen: 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.2.jre8</version>
</dependency>
```    

 **Microsoft JDBC-Treiber 6.0 und 4.2 für SQL Server:**  
  
  Die JDBC-Treiber 6.0 und 4.2 enthalten in jedem Installationspaket zwei JAR-Klassenbibliotheken: **sqljdbc41.jar** und **sqljdbc42.jar**. 
  
 Die JDBC-Treiber 6.0 und 4.2 sind für die Verwendung und Unterstützung aller wichtigen virtuellen Java-Computer konzipiert. Sie werden jedoch nur mit der Sun JRE 5.0, 6.0, 7.0 und 8.0 getestet.
  
 Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den beiden in den Microsoft JDBC-Treibern 6.0 und 4.2 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
|JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|   
|sqljdbc41.jar|4.1|7|Erfordert die Java-Laufzeitumgebung( JRE) Version 7.0. Bei Verwendung von JRE 6.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in 6.0- und 4.2-Paketen umfassen Folgendes: JDBC 4.1-Kompatibilität und Massenkopieren<br /><br /> Darüber hinaus umfassen neue Features im 6.0-Paket Folgendes: Always Encrypted, 	Tabellenwertparameter, Azure Active Directory-Authentifizierung, transparente Verbindungen mit Always On-Verfügbarkeitsgruppen, verbesserter Abruf von Parametermetadaten für vorbereitete Abfragen und internationalisierter Domänennamen (Internationalized Domain Name, IDN)|  
|sqljdbc42.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Bei Verwendung von JRE 7.0 oder niedriger wird eine Ausnahme ausgelöst.<br /><br /> Neue Features in 6.0- und 4.2-Paketen umfassen Folgendes: JDBC 4.1-Kompatibilität, JDBC 4.2-Kompatibilität und Massenkopieren<br /><br /> Darüber hinaus umfassen neue Features im 6.0-Paket Folgendes: Always Encrypted, 	Tabellenwertparameter, Azure Active Directory-Authentifizierung, transparente Verbindungen mit Always On-Verfügbarkeitsgruppen, verbesserter Abruf von Parametermetadaten für vorbereitete Abfragen und internationalisierter Domänennamen (Internationalized Domain Name, IDN)|  
  
 **Microsoft JDBC-Treiber 4.1 für SQL Server:**  
  
 Der JDBC-Treiber 4.1 enthält in jedem Installationspaket eine JAR-Klassenbibliothek: **sqljdbc41.jar**.  
    
|JAR|und Beschreibung|  
|---------|-----------------|  
|sqljdbc41.jar|Die Klassenbibliothek **sqljdbc41.jar** stellt Unterstützung für die JDBC 4.0-API bereit. Sie enthält außerdem alle Funktionen des JDBC 4.0-Treibers sowie die JDBC 4.0-API-Methoden. JDBC 4.1 wird nicht unterstützt (die Ausnahme „SQLFeatureNotSupportedException“ wird ausgelöst).<br /><br /> Die Klassenbibliothek **sqljdbc41.jar** erfordert JRE (Java Runtime Environment) Version 7.0. Bei Verwendung von **sqljdbc41.jar** mit JRE 6.0 und 5.0 wird eine Ausnahme ausgelöst.<br /><br /> 
  
 Der JDBC-Treiber ist für die Verwendung und Unterstützung aller wichtigen virtuellen Java-Computern konzipiert. Er wird jedoch nur mit der Sun JRE 5.0, 6.0 und 7.0 getestet.
  
 Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von der im Microsoft JDBC-Treiber 4.1 für SQL Server enthaltenen JAR-Datei bereitgestellt wird.  
  
|JAR|JDBC-Version|JRE (kann ausgeführt werden)|JDK (kann kompilieren)|  
|---------|------------------|---------------------|-------------------------|   
|sqljdbc41.jar|4|7|7 6 5|  
  
## <a name="sql-server-requirements"></a>SQL Server-Anforderungen  
 Der JDBC-Treiber unterstützt Verbindungen mit Azure-SQL-Datenbank und SQL Server. Die Microsoft JDBC-Treiber 4.2 und 4.1 für SQL Server werden beginnend mit SQL Server 2008 unterstützt.
  
## <a name="operating-system-requirements"></a>Betriebssystemanforderungen  
 Der JDBC-Treiber ist für die Verwendung mit einem Betriebssystem konzipiert, das die Java Virtual Machine (JVM) unterstützt. Allerdings wurden nur die Betriebssysteme Sun Solaris, SUSE Linux und Windows offiziell getestet.  
  
## <a name="supported-languages"></a>Unterstützte Sprachen  
 Der JDBC-Treiber unterstützt alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spaltensortierungen. Weitere Informationen zu den vom JDBC-Treiber unterstützten Sortierungen finden Sie unter [Internationale Features des JDBC-Treibers](../../connect/jdbc/international-features-of-the-jdbc-driver.md).  
  
 Weitere Informationen zu Sortierungen finden Sie unter „Arbeiten mit Sortierungen“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
