---
title: Systemanforderungen für JDBC Driver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 447792bb-f39b-49b4-9fd0-1ef4154c74ab
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: afced2ca67c104b0bb01ccfe57fee2e309cc1b08
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52410167"
---
# <a name="system-requirements-for-the-jdbc-driver"></a>Systemanforderungen für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Für den Zugriff auf Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] mit dem [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] müssen die folgenden Komponenten auf dem Computer installiert sein:

- [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ([Download](download-microsoft-jdbc-driver-for-sql-server.md))
- Java Runtime Environment (JRE)

## <a name="java-runtime-environment-requirements"></a>JRE-Anforderungen  
 Ab dem Microsoft JDBC-Treiber 7.0 für SQL Server werden Sun Java SE Development Kit (JDK) 10.0 und Java Runtime Environment (JRE) 10.0 unterstützt.

 Ab dem Microsoft JDBC-Treiber 6.4 für SQL Server werden Sun Java SE Development Kit (JDK) 9.0 und Java Runtime Environment (JRE) 9.0 unterstützt.

 Ab Version 4.2 des Microsoft JDBC-Treibers für SQL Server werden das Sun Java SE Development Kit (JDK) 8.0 und die Java-Laufzeitumgebung (JRE) 8.0 unterstützt. Die Unterstützung für die Java Database Connectivity (JDBC) Spec-API wurde nun auf die JDBC 4.1 und 4.2-API ausgeweitet.  
  
 Ab dem Microsoft JDBC-Treiber 4.1 für SQL Server werden Sun Java SE Development Kit (JDK) 7.0 und Java Runtime Environment (JRE) 7.0 unterstützt.  
  
 Seit der Einführung von [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] wurde die JDBC-Treiberunterstützung für die API der JDBC (Java Database Connectivity)-Spezifikation um die JDBC 4.0-API erweitert. Die JDBC 4.0-API wurde als Bestandteil des Sun Java SE Development Kits (JDK) 6.0 und der Java Runtime Environment (JRE) 6.0 eingeführt. JDBC 4.0 ist eine Obermenge der JDBC 3.0-API.  
  
 Bei der Bereitstellung von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unter Windows- und UNIX-Betriebssystemen müssen Sie entsprechend eines der folgenden Installationspakete verwenden: *sqljdbc_\<version> _enu.exe* oder *sqljdbc_\<version>_enu.tar.gz*. Weitere Informationen zum Bereitstellen des JDBC-Treibers finden Sie unter [Bereitstellen des JDBC-Treibers](../../connect/jdbc/deploying-the-jdbc-driver.md) Thema.  
  
**Microsoft JDBC-Treiber 7.0 für SQL Server**  

  Der Microsoft JDBC-Treiber 7.0 enthält in jedem Installationspaket zwei JAR-Klassenbibliotheken: **mssql-jdbc-7.0.0.jre8.jar** und **mssql-jdbc-7.0.0.jre10.jar**.

  Der JDBC-Treiber 7.0 ist für die Verwendung und Unterstützung aller wichtigen Sun-kompatiblen Java Virtual Machines konzipiert. Er ist jedoch nur mit der Sun JRE 8.0 und 10.0 getestet.
  
  Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den beiden im Microsoft JDBC-Treiber 7.0 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
  |JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-7.0.0.jre8.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Mithilfe von JRE 7.0 oder niedriger löst eine Ausnahme.<br /><br /> Neue Funktionen in 7.0 schließen: JDK-10-Unterstützung, aktualisierte Compliance Standardebene JDBC 4.2-Spezifikationen, Unterstützung von räumlichen Datentypen, CancelQueryTimeout-Verbindungseigenschaft, Methoden Grenze anfordern, UseBulkCopyForBatchInsert-Verbindungseigenschaft, Daten Datenermittlung und-Klassifizierung Informationen UTF-8-funktionserweiterung und CityHash Unterstützung. |    
|mssql-jdbc-7.0.0.jre10.jar|4.3|10|Erfordert die Java Runtime Environment (JRE) 10.0. Mithilfe von 9.0 mit JRE oder niedriger löst eine Ausnahme.<br /><br /> Neue Funktionen in 7.0 schließen: JDK-10-Unterstützung, aktualisierte Compliance Standardebene JDBC 4.2-Spezifikationen, Unterstützung von räumlichen Datentypen, CancelQueryTimeout-Verbindungseigenschaft, Methoden Grenze anfordern, UseBulkCopyForBatchInsert-Verbindungseigenschaft, Daten Datenermittlung und-Klassifizierung Informationen UTF-8-funktionserweiterung und CityHash Unterstützung. |    


  Der JDBC-Treiber-7.0 steht auch auf das zentrale Maven-Repository und kann durch Hinzufügen des folgenden Codes in die POM, ein Maven-Projekt hinzugefügt werden. XML-CODE:  
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
</dependency>
```      
  
**Microsoft JDBC-Treiber 6.4 für SQL Server:**  

  Der Microsoft JDBC-Treiber 6.4 enthält in jedem Installationspaket drei JAR-Klassenbibliotheken: **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar** und **mssql-jdbc-6.4.0.jre9.jar**.

  Der JDBC-Treiber 6.4 ist für die Verwendung mit allen sowie die Unterstützung aller wichtigen Sun-kompatiblen Java Virtual Machines konzipiert. Er wird jedoch nur mit der Sun-Laufzeitumgebung 7.0, 8.0 und 9.0 getestet.
  
  Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den drei im Microsoft JDBC-Treiber 6.4 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
  |JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-6.4.0.jre7.jar|4.1|7|Erfordert die Java-Laufzeitumgebung( JRE) Version 7.0. Verwendung von JRE 6.0 oder niedriger löst eine Ausnahme.<br /><br /> Neue Funktionen in 6.4 schließen: Azure AD-Authentifizierung für Linux, Prinzipal und Kennwort-Methode für die automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, Kerberos Constrained Delegation, Abfragetimeouts, Sockettimeout, Kerberos und vorbereitete Anweisungshandle erneut verwenden. |  
|mssql-jdbc-6.4.0.jre8.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Mithilfe von JRE 7.0 oder niedriger löst eine Ausnahme.<br /><br /> Neue Funktionen in 6.4 schließen: Azure AD-Authentifizierung für Linux, Prinzipal und Kennwort-Methode für die automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, Kerberos Constrained Delegation, Abfragetimeouts, Sockettimeout, Kerberos und vorbereitete Anweisungshandle erneut verwenden. |    
|mssql-jdbc-6.4.0.jre9.jar|4.3|9|Erfordert die Java-Laufzeitumgebung (JRE), Version 9.0. Verwenden JRE 8.0- oder niedrigere löst eine Ausnahme.<br /><br /> Neue Funktionen in 6.4 schließen: Azure AD-Authentifizierung für Linux, Prinzipal und Kennwort-Methode für die automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, Kerberos Constrained Delegation, Abfragetimeouts, Sockettimeout, Kerberos und vorbereitete Anweisungshandle erneut verwenden. |

Der JDBC-Treiber 6.4 steht auch auf das zentrale Maven-Repository und kann durch Hinzufügen des folgenden Codes in die POM, ein Maven-Projekt hinzugefügt werden. XML 

 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre9</version>
</dependency>
```

**Microsoft JDBC-Treiber 6.2 für SQL Server:**  
  
  Der Microsoft JDBC-Treiber 6.2 enthält in jedem Installationspaket drei JAR-Klassenbibliotheken: **mssql-jdbc-6.2.2.jre7.jar** und **mssql-jdbc-6.2.2.jre8.jar**. 
  
 Der JDBC-Treiber 6.2 ist für die Verwendung mit allen sowie die Unterstützung aller wichtigen Sun-kompatiblen Java Virtual Machines konzipiert. Er wird jedoch nur mit der Sun JRE 5.0, 6.0, 7.0 und 8.0 getestet.
  
 Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den beiden in den Microsoft JDBC-Treibern 6.0 und 4.2 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
|JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|
|MSSQL-Jdbc-6.2.2.jre7.jar|4.1|7|Erfordert die Java-Laufzeitumgebung( JRE) Version 7.0. Verwendung von JRE 6.0 oder niedriger löst eine Ausnahme.<br /><br /> Neue Features in 6.2 sind: Azure AD-Authentifizierung für Linux, Prinzipal und Kennwort-Methode für die automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, Kerberos Constrained Delegation, Abfragetimeouts, Sockettimeout, Kerberos und vorbereitete Anweisungshandle erneut verwenden. |  
|MSSQL-Jdbc-6.2.3.jre8.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Mithilfe von JRE 7.0 oder niedriger löst eine Ausnahme.<br /><br /> Neue Features in 6.2 sind: Azure AD-Authentifizierung für Linux, Prinzipal und Kennwort-Methode für die automatische Erkennung von REALM im SPN für domänenübergreifende Authentifizierung, Kerberos Constrained Delegation, Abfragetimeouts, Sockettimeout, Kerberos und vorbereitete Anweisung Handle erneut verwenden|    

  Der JDBC-Treiber 6.2 finden Sie auch auf das zentrale Maven-Repository und kann durch Hinzufügen des folgenden Codes in die POM, ein Maven-Projekt hinzugefügt werden. XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.2.jre8</version>
</dependency>
```    

 **Microsoft JDBC-Treiber 6.0 und 4.2 für SQL Server:**  
  
  Der JDBC-Treiber 6.0- und 4.2, umfassen zwei JAR-Klassenbibliotheken in jedem Installationspaket: **"sqljdbc41.jar"**, und **"sqljdbc42.jar"**. 
  
 Die JDBC-Treiber 6.0 und 4.2 sind für die Verwendung mit allen sowie die Unterstützung aller wichtigen Sun-kompatiblen Java Virtual Machines konzipiert. Sie werden jedoch nur mit der Sun JRE 5.0, 6.0, 7.0 und 8.0 getestet. 
  
 Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von den beiden in den Microsoft JDBC-Treibern 6.0 und 4.2 für SQL Server enthaltenen JAR-Dateien bereitgestellt wird:  
  
|JAR|JDBC-Versionskompatibilität|Empfohlene Java-Version|und Beschreibung|  
|---------|-----------------------------|----------------------|-----------------|   
|sqljdbc41.jar|4.1|7|Erfordert die Java-Laufzeitumgebung( JRE) Version 7.0. Verwendung von JRE 6.0 oder niedriger löst eine Ausnahme.<br /><br /> Neue Funktionen in 6.0- und 4.2-Paketen schließen Folgendes mit ein: JDBC 4.1-Kompatibilität und Massenkopieren<br /><br /> Darüber hinaus neue Features in im 6.0-Paket enthalten: Always Encrypted, Table-Valued Parameters, Azure Active Directory-Authentifizierung, transparente Verbindungen mit Always On Availability Groups, zur Verbesserung der im Parameter-Abruf von Metadaten für vorbereitete Abfragen und Internationalized Domain Name (IDN)|  
|sqljdbc42.jar|4.2|8|Erfordert die Java-Laufzeitumgebung(JRE) Version 8.0. Mithilfe von JRE 7.0 oder niedriger löst eine Ausnahme.<br /><br /> Neue Funktionen in 6.0- und 4.2-Paketen schließen Folgendes mit ein: JDBC 4.1 Compliance, JDBC 4.2 Compliance und Massenkopieren<br /><br /> Darüber hinaus neue Features in im 6.0-Paket enthalten: Always Encrypted, Table-Valued Parameters, Azure Active Directory-Authentifizierung, transparente Verbindungen mit Always On Availability Groups, zur Verbesserung der im Parameter-Abruf von Metadaten für vorbereitete Abfragen und Internationalized Domain Name (IDN)|  
  
 **Microsoft JDBC-Treiber 4.1 für SQL Server:**  
  
 Der JDBC-Treiber 4.1 enthält eine JAR-Klassenbibliothek in jedem Installationspaket: **"sqljdbc41.jar"**.  
    
|JAR|und Beschreibung|  
|---------|-----------------|  
|sqljdbc41.jar|Die Klassenbibliothek **sqljdbc41.jar** stellt Unterstützung für die JDBC 4.0-API bereit. Sie enthält außerdem alle Funktionen des JDBC 4.0-Treibers sowie die JDBC 4.0-API-Methoden. JDBC 4.1 wird nicht unterstützt (die Ausnahme „SQLFeatureNotSupportedException“ wird ausgelöst).<br /><br /> Die Klassenbibliothek **sqljdbc41.jar** erfordert JRE (Java Runtime Environment) Version 7.0. Mithilfe von **"sqljdbc41.jar"** für JRE 6.0 und 5.0 löst eine Ausnahme aus.<br /><br /> 
  
 Der JDBC-Treiber ist zwar für die Verwendung mit und die Unterstützung aller wichtigen Sun-kompatiblen Java-VMs (Virtual Machines) ausgelegt, Tests erfolgen jedoch nur mit Sun JRE 5.0, 6.0 und 7.0.  
  
 Im Folgenden finden Sie eine Übersicht über die Unterstützung, die von der im Microsoft JDBC-Treiber 4.1 für SQL Server enthaltenen JAR-Datei bereitgestellt wird.  
  
|JAR|JDBC-Version|JRE (kann ausgeführt werden)|JDK (kann kompilieren)|  
|---------|------------------|---------------------|-------------------------|   
|sqljdbc41.jar|4|7|7 6 5|  
  
## <a name="sql-server-requirements"></a>SQL Server-Anforderungen  
 Der JDBC-Treiber unterstützt Verbindungen mit Azure-SQL-Datenbank und SQL Server. Die Microsoft JDBC-Treiber 4.2 und 4.1 für SQL Server werden beginnend mit SQL Server 2008 unterstützt.
  
## <a name="operating-system-requirements"></a>Betriebssystemanforderungen  
 Der JDBC-Treiber ist für die Verwendung mit einem Betriebssystem konzipiert, das die Java Virtual Machine (JVM) unterstützt. Allerdings wurden nur die Betriebssysteme Sun Solaris, SUSE Linux und Windows offiziell getestet.  
  
## <a name="supported-languages"></a>Unterstützte Sprachen  
 Der JDBC-Treiber unterstützt alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spaltensortierungen. Weitere Informationen zu den vom JDBC-Treiber unterstützten Sortierungen finden Sie unter [internationale Funktionen des JDBC-Treibers](../../connect/jdbc/international-features-of-the-jdbc-driver.md).  
  
 Weitere Informationen zu Sortierungen finden Sie unter „Arbeiten mit Sortierungen“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
