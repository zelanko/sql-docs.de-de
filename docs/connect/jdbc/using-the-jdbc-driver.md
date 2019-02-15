---
title: Verwenden des JDBC-Treibers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6faaf05b-8b70-4ed2-9b44-eee5897f1cd0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e0f803b68f2ab9f62c3df27c6930da8e3a8a4a0
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737091"
---
# <a name="using-the-jdbc-driver"></a>Verwenden des JDBC-Treibers

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Abschnitt enthält Anleitungen, um in kurzer Zeit mit [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] eine einfache Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank herzustellen. Vor dem Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem lokalen Computer oder einem Server sowie der JDBC-Treiber auf dem lokalen Computer installiert werden.  
  
## <a name="choosing-the-right-jar-file"></a>Auswählen der richtigen JAR-Datei

Microsoft JDBC-Treiber bietet verschiedene JAR-Dateien in Übereinstimmung mit Ihren bevorzugten Einstellungen für die Java Runtime Environment (JRE) verwendet werden, wie unter:

Die Microsoft JDBC-Treiber 7.2 für SQL Server bietet **Mssql-Jdbc-7.2.0.jre8.jar**, und **Mssql-Jdbc-7.2.0.jre11.jar** Klassenbibliotheken.

Microsoft JDBC-Treiber 7.0 für SQL Server bietet **Mssql-Jdbc-7.0.0.jre8.jar**, und **Mssql-Jdbc-7.0.0.jre10.jar** Klassenbibliotheken.

Der Microsoft JDBC-Treiber 6.4 für SQL Server bietet **Mssql-Jdbc-6.4.0.jre7.jar**, **Mssql-Jdbc-6.4.0.jre8.jar**, und **Mssql-Jdbc-6.4.0.jre9.jar** -Klassenbibliothek Dateien.

Der Microsoft JDBC-Treiber 6.2 für SQL Server bietet **Mssql-Jdbc-6.2.2.jre7.jar**, und **Mssql-Jdbc-6.2.2.jre8.jar** Klassenbibliotheken.
  
Geben Sie den Microsoft JDBC-Treiber 6.0- und 4.2 für SQL Server **"sqljdbc41.jar"**, und **"sqljdbc42.jar"** Klassenbibliotheken.
  
Der Microsoft JDBC-Treiber 4.1 für SQL Server bietet die **"sqljdbc41.jar"** klassenbibliothekdatei.

Ihre Auswahl entscheidet auch über die verfügbaren Funktionen. Weitere Informationen zu der JAR-Datei auswählen, finden Sie unter [Systemanforderungen für JDBC Driver](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="setting-the-classpath"></a>Festlegen des Klassenpfads

Die Microsoft JDBC-Treiber JAR-Dateien sind nicht Bestandteil des Java SDK und im Klassenpfad der Benutzer die Anwendung enthalten sein müssen.

Wenn der JDBC-Treiber 4.1 und 4.2, legen Sie den Klassenpfad aufnehmen **"sqljdbc41.jar"** oder **"sqljdbc42.jar"** -Datei aus der entsprechenden Treiber-Download.

Wenn der JDBC-Treiber 6.2, legen Sie den Klassenpfad aufnehmen der **Mssql-Jdbc-6.2.2.jre7.jar** oder **Mssql-Jdbc-6.2.2.jre8.jar**.

Wenn der JDBC-Treiber 6.4, legen Sie den Klassenpfad aufnehmen der **Mssql-Jdbc-6.4.0.jre7.jar**, ** Mssql-Jdbc-6.4.0.jre8.jar oder **Mssql-Jdbc-6.4.0.jre9.jar**.

Wenn der JDBC-Treiber 7.0, legen Sie den Klassenpfad aufnehmen der **Mssql-Jdbc-7.0.0.jre8.jar** oder **Mssql-Jdbc-7.0.0.jre10.jar**.

Wenn der JDBC-Treiber 7.2, legen Sie den Klassenpfad aufnehmen der **Mssql-Jdbc-7.2.0.jre8.jar** oder **Mssql-Jdbc-7.2.0.jre11.jar**.

Wenn im Klassenpfad kein Eintrag für die richtige JAR-Datei vorhanden ist, löst eine Anwendung die allgemeine `Class not found` Ausnahme.  

### <a name="for-microsoft-jdbc-driver-72"></a>Für Microsoft JDBC-Treiber 7.2

Die **Mssql-Jdbc-7.2.0.jre8.jar** oder **Mssql-Jdbc-7.2.0.jre11.jar** Dateien werden in den folgenden Speicherorten installiert:

```bash
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-7.2.0.jre8.jar

\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-7.2.0.jre11.jar
```

Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Windows-Anwendung verwendet wird:

`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 7.2 for SQL Server\sqljdbc_7.2\enu\mssql-jdbc-7.2.0.jre11.jar`

Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Linux/Unix-Anwendung verwendet wird:

`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_7.2/enu/mssql-jdbc-7.2.0.jre11.jar`

Stellen Sie sicher, dass die CLASSPATH-Anweisung nur einen enthält [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], z. B. entweder **Mssql-Jdbc-7.2.0.jre8.jar** oder **Mssql-Jdbc-7.2.0.jre11.jar**.
  
### <a name="for-microsoft-jdbc-driver-70"></a>Für Microsoft JDBC-Treiber 7.0

Die **Mssql-Jdbc-7.0.0.jre8.jar** oder **Mssql-Jdbc-7.0.0.jre10.jar** Dateien werden in den folgenden Speicherorten installiert:

```bash
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-7.0.0.jre8.jar

\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-7.0.0.jre10.jar
```

Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Windows-Anwendung verwendet wird:  

`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 7.0 for SQL Server\sqljdbc_7.0\enu\mssql-jdbc-7.0.0.jre10.jar`  
  
Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Linux/Unix-Anwendung verwendet wird:  
  
`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_7.0/enu/mssql-jdbc-7.0.0.jre10.jar`  
  
Stellen Sie sicher, dass die CLASSPATH-Anweisung nur einen enthält [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], z. B. entweder **Mssql-Jdbc-7.0.0.jre8.jar** oder **Mssql-Jdbc-7.0.0.jre10.jar**.

### <a name="for-microsoft-jdbc-driver-64"></a>Für Microsoft JDBC-Treiber 6.4

Die **Mssql-Jdbc-6.4.0.jre7.jar**, ** Mssql-Jdbc-6.4.0.jre8.jar oder **Mssql-Jdbc-6.4.0.jre9.jar** Dateien werden am folgenden Speicherort installiert:  

```bash  
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.4.0.jre7.jar
  
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.4.0.jre8.jar

\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.4.0.jre9.jar
```

Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Windows-Anwendung verwendet wird:  
  
`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.4 for SQL Server\sqljdbc_6.4\enu\mssql-jdbc-6.4.0.jre9.jar`  
  
Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Linux/Unix-Anwendung verwendet wird:  
  
`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.4/enu/mssql-jdbc-6.4.0.jre9.jar`  
  
Stellen Sie sicher, dass die CLASSPATH-Anweisung nur einen enthält [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], z. B. entweder **Mssql-Jdbc-6.4.0.jre7.jar**, ** Mssql-Jdbc-6.4.0.jre8.jar oder **Mssql-Jdbc-6.4.0.jre9.jar**.

### <a name="for-microsoft-jdbc-driver-62"></a>Für Microsoft JDBC-Treiber 6.2

Die **Mssql-Jdbc-6.2.2.jre7.jar** oder **Mssql-Jdbc-6.2.2.jre8.jar** Dateien werden in den folgenden Speicherorten installiert:

```bash
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.2.2.jre7.jar
  
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.2.2.jre8.jar
```

Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Windows-Anwendung verwendet wird:  
  
`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.2 for SQL Server\sqljdbc_6.2\enu\mssql-jdbc-6.2.2.jre8.jar`  
  
Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Linux/Unix-Anwendung verwendet wird:  
  
`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.2/enu/mssql-jdbc-6.2.2.jre8.jar`  
  
Stellen Sie sicher, dass die CLASSPATH-Anweisung nur einen enthält [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], z. B. entweder "Mssql-Jdbc-6.2.2.jre7.jar" oder "Mssql-Jdbc-6.2.2.jre8.jar.  

### <a name="for-microsoft-jdbc-driver-41-42-and-60"></a>Für den Microsoft JDBC-Treiber 6.0, 4.2 und 4.1

Die JAR-Datei sqljdbc.jar file, sqljdbc4.jar file, sqljdbc41.jar oder sqljdbc42.jar wird an folgendem Speicherorten installiert.  

```bash
\<installation directory>\sqljdbc_<version>\<language>\sqljdbc.jar  
  
\<installation directory>\sqljdbc_<version>\<language>\sqljdbc4.jar  
  
\<installation directory>\sqljdbc_<version>\<language>\sqljdbc41.jar  
  
\<installation directory>\sqljdbc_<version>\<language>\sqljdbc42.jar  
```

Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Windows-Anwendung verwendet wird:  
  
`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.0 for SQL Server\sqljdbc_4.2\enu\sqljdbc42.jar`  
  
Der folgende Codeausschnitt stellt ein Beispiel für die CLASSPATH-Anweisung dar, die für eine Linux/Unix-Anwendung verwendet wird:  

`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_4.2/enu/sqljdbc42.jar`  
  
Stellen Sie sicher, dass die CLASSPATH-Anweisung nur eine [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Datei enthält, z.B. „sqljdbc4.jar“, „sqljdbc41.jar“ oder „sqljdbc42.jar“.  
  
> [!NOTE]  
> Auf Windows-Systemen können Verzeichnisnamen, die länger als die 8.3-Namenskonvention sind, oder Ordnernamen mit Leerzeichen zu Problemen bei Klassenpfaden führen. Wenn Sie ein derartiges Problem vermuten, sollten Sie die Datei „sqljdbc.jar“, „sqljdbc4.jar“ oder „sqljdbc41.jar“ vorübergehend in ein Verzeichnis mit einem einfachen Namen wie `C:\Temp` verschieben, den Klassenpfad ändern und prüfen, ob das Problem dadurch behoben wurde.  
  
### <a name="applications-that-are-run-directly-at-the-command-prompt"></a>Anwendungen, die direkt an der Eingabeaufforderung ausgeführt werden

Der Klassenpfad wird im Betriebssystem konfiguriert. Hängen Sie "sqljdbc.jar", "sqljdbc4.jar" oder "sqljdbc41.jar" an den Klassenpfad des Systems an. Alternativ können Sie den Klassenpfad in der Java-Befehlszeile, mit der die Anwendung ausgeführt wird, mit der Option `java -classpath` angeben.  
  
### <a name="applications-that-run-in-an-ide"></a>Anwendungen, die in einer IDE ausgeführt werden  

Jeder IDE-Hersteller verwendet eine andere Methode, um den Klassenpfad in der IDE festzulegen. Es reicht nicht aus, den Klassenpfad lediglich im Betriebssystem festzulegen. Sie müssen "sqljdbc.jar", "sqljdbc4.jar" oder "sqljdbc41.jar" an den IDE-Klassenpfad anhängen.  
  
### <a name="servlets-and-jsps"></a>Servlets und JSPs  

Servlets und JSPs werden in einer Servlet-/JSP-Engine wie Tomcat ausgeführt. Der Klassenpfad muss wie in der Dokumentation für die Servlet-/JSP-Engine angegeben festgelegt werden. Es reicht nicht aus, den Klassenpfad lediglich im Betriebssystem festzulegen. Einige Servlet-/JSP-Engines verfügen über Setupfenster, in denen Sie den Klassenpfad der Engine festlegen können. In dieser Situation müssen Sie die richtige JAR-Datei für den JDBC-Treiber an den vorhandenen Klassenpfad der Engine anhängen und die Engine neu starten. In anderen Situationen können Sie den Treiber bereitstellen, indem Sie "sqljdbc.jar", "sqljdbc4.jar" oder "sqljdbc41.jar" bei der Engine-Installation in ein bestimmtes Verzeichnis kopieren, z. B. "lib". Der Klassenpfad für den Engine-Treiber kann auch in einer Engine-spezifischen Konfigurationsdatei angegeben werden.  
  
### <a name="enterprise-java-beans"></a>Enterprise Java Beans  

Enterprise Java Beans (EJB) werden in einem EJB-Container ausgeführt. EJB-Container sind von verschiedenen Herstellern erhältlich. Java-Applets werden in einem Browser ausgeführt, aber von einem Webserver heruntergeladen. Kopieren Sie „sqljdbc.jar“ „sqljdbc4.jar“ oder „sqljdbc41.jar“ in das Stammverzeichnis des Webservers, und geben Sie den Namen der JAR-Datei auf der HTML-Archiv-Registerkarte des Applets an, z.B. `<applet ... archive=mssql-jdbc-***.jar>`.  
  
## <a name="making-a-simple-connection-to-a-database"></a>Herstellen einer einfachen Verbindung mit einer Datenbank

Mithilfe der sqljdbc.jar-Klassenbibliothek müssen Anwendungen zuerst den Treiber wie folgt zu registrieren:  
  
`Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");`  

Wenn der Treiber geladen wird, können Sie eine Verbindung herstellen, unter Verwendung einer Verbindungs-URL und die GetConnection-Methode der DriverManager-Klasse:

```java
String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
   "databaseName=AdventureWorks;user=MyUserName;password=*****;";  
Connection con = DriverManager.getConnection(connectionUrl);  
```

Ab der JDBC-API 4.0 wurde die `DriverManager.getConnection()`-Methode so erweitert, dass JDBC-Treiber automatisch geladen werden. Daher müssen Anwendungen die `Class.forName`-Methode bei Verwendung von JAR-Treiberbibliotheken nicht aufrufen, um den Treiber zu registrieren oder zu laden.  
  
Wenn die GetConnection-Methode der DriverManager-Klasse aufgerufen wird, ist ein geeigneter Treiber aus der Gruppe der registrierten JDBC-Treiber. "sqljdbc4.jar", "sqljdbc41.jar" oder "sqljdbc42.jar"-Datei enthält die Datei "META-INF/services/java.sql.Driver" enthält die **com.microsoft.sqlserver.jdbc.SQLServerDriver** als registrierten Treiber. Vorhandene Anwendungen, die die Treiber derzeit mit der Methode Class.forName laden, funktionieren auch weiterhin ohne Änderungen.  
  
> [!NOTE]  
> Die Klassenbibliothek „sqljdbc4.jar“, „sqljdbc41.jar“ oder „sqljdbc42.jar“ kann nicht mit älteren Versionen von Java Runtime Environment (JRE) verwendet werden. Finden Sie unter [Systemanforderungen für JDBC Driver](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) für die Liste der vom unterstützten JRE-Versionen der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  

Weitere Informationen zum Herstellen einer Verbindung mit Datenquellen und die Verwendung einer Verbindungs-URL finden Sie unter [Building the Connection URL](../../connect/jdbc/building-the-connection-url.md) und [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
