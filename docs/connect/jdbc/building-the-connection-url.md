---
title: Erstellen der Verbindungs-URL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/29/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 44996746-d373-4f59-9863-a8a20bb8024a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 889571da70eaf43878d4226751b2b031853f802f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922626"
---
# <a name="building-the-connection-url"></a>Erstellen der Verbindungs-URL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Die allgemeine Form der Verbindungs-URL lautet:  
  
 `jdbc:sqlserver://[serverName[\instanceName][:portNumber]][;property=value[;property=value]]`  
  
 Dabei gilt:  
  
-   **jdbc:sqlserver://** (erforderlich) wird als Subprotokoll bezeichnet und ist konstant.  
  
-   **serverName** (optional) stellt die Adresse des Servers dar, zu dem eine Verbindung hergestellt werden soll. Dabei kann es sich um eine DNS- oder IP-Adresse bzw. "localhost" oder "127.0.0.1" für den lokalen Computer handeln. Wenn der Servername nicht in der Verbindungs-URL angegeben wird, muss er in der properties-Auflistung angegeben werden.  
  
-   **instanceName** (optional) bezeichnet die Instanz auf „serverName“, zu der eine Verbindung hergestellt werden soll. Ohne Angabe wird eine Verbindung zur Standardinstanz erstellt.  
  
-   **portNumber** (optional) bezeichnet den Port auf „serverName“, über den eine Verbindung hergestellt werden soll. Der Standardwert ist "1433". Wenn Sie den Standardport verwenden oder weder den Port noch den vorangestellten Doppelpunkt („:“) in der URL angeben müssen.  
  
    > [!NOTE]  
    >  Um eine optimale Leistung der Verbindung zu gewährleisten, sollten Sie "portNumber" festlegen, wenn Sie eine Verbindung zu einer benannten Instanz herstellen. Dadurch werden Roundtrips zum Server vermieden, um die Portnummer zu ermitteln. Wenn "portNumber" und "instanceName" verwendet werden, hat "portNumber" Vorrang und "instanceName" wird ignoriert.  
  
-   **property** (optional) ist mindestens eine optionale Verbindungseigenschaft. Weitere Informationen zum Festlegen der Verbindungseigenschaften finden Sie unter [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md). Sie können eine beliebige Eigenschaft aus der Liste angeben. Mehrere Eigenschaften müssen durch ein Semikolon („;“) getrennt werden und dürfen nicht doppelt vorkommen.  
  
> [!CAUTION]  
>  Aus Sicherheitsgründen sollten Sie es vermeiden, die Verbindungs-URLs basierend auf Benutzereingaben zu erstellen. Sie sollten in der URL lediglich Servername und Treiber angeben. Verwenden Sie für Werte von Benutzernamen und Kennwörtern die properties-Auflistungen für Verbindungen. Weitere Informationen zur Sicherheit in Ihren JDBC-Anwendungen finden Sie unter [Absichern von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md).  
  
## <a name="connection-examples"></a>Verbindungsbeispiele  
 Herstellen einer Verbindung zur Standarddatenbank auf dem lokalen Computer mit Benutzername und Kennwort:  
  
 `jdbc:sqlserver://localhost;user=MyUserName;password=*****;`  
  
> [!NOTE]  
>  Obwohl im vorherigen Beispiel in der Verbindungszeichenfolge ein Benutzername und ein Kennwort verwendet wurden, sollten Sie aufgrund der höheren Sicherheit die integrierte Sicherheit verwenden. Weitere Informationen finden Sie im Abschnitt [Herstellen einer Verbindung mit integrierter Authentifizierung](#Connectingintegrated) weiter unten in diesem Artikel.  
  
 Anhand der folgenden Verbindungszeichenfolge wird veranschaulicht, wie Sie eine Verbindung zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank mithilfe der integrierten Authentifizierung und Kerberos über eine Anwendung herstellen, die auf einem beliebigen Betriebssystem ausgeführt wird, das vom [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt wird:  
  
```java
jdbc:sqlserver://;servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos  
```  
  
 Herstellen einer Verbindung zur Standarddatenbank auf dem lokalen Computer mit integrierter Authentifizierung:  
  
 `jdbc:sqlserver://localhost;integratedSecurity=true;`  
  
 Herstellen einer Verbindung zu einer benannten Datenbank auf einem Remoteserver:  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 Herstellen einer Verbindung zum Standardport auf dem Remoteserver:  
  
 `jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 Herstellen einer Verbindung mit Angabe eines angepassten Anwendungsnamens:  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;applicationName=MyApp;`  
  
## <a name="named-and-multiple-sql-server-instances"></a>Benannte und mehrere SQL Server-Instanzen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt die Installation mehrerer Datenbankinstanzen auf einem Server zu. Jede Instanz wird durch einen bestimmten Namen gekennzeichnet. Um eine Verbindung zu einer benannten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen, können Sie entweder die Portnummer der benannten Instanz angeben (bevorzugte Vorgehensweise) oder den Instanznamen als JDBC-URL-Eigenschaft oder **datasource**-Eigenschaft angeben. Wenn keine Eigenschaft für Instanzname oder Portnummer angegeben wurde, wird eine Verbindung zur Standardinstanz erstellt. Hierzu folgende Beispiele:  
  
 Gehen Sie folgendermaßen vor, wenn eine Portnummer verwendet werden soll:  
  
 `jdbc:sqlserver://localhost:1433;integratedSecurity=true;<more properties as required>;`  
  
 Gehen Sie folgendermaßen vor, wenn eine JDBC-URL-Eigenschaft verwendet werden soll:  
  
 `jdbc:sqlserver://localhost;instanceName=instance1;integratedSecurity=true;<more properties as required>;`  
  
## <a name="escaping-values-in-the-connection-url"></a>Maskieren von Werten in der Verbindungs-URL  
 Eventuell müssen Sie bestimmte Teile von Werten der Verbindungs-URL aufgrund enthaltener Sonderzeichen wie Leerzeichen, Semikolons und Anführungszeichen maskieren. Der JDBC-Treiber unterstützt die Maskierung dieser Zeichen, indem sie in geschweifte Klammern gesetzt werden. So maskiert {;} beispielsweise ein Semikolon.  
  
 Maskierte Werte können Sonderzeichen enthalten (insbesondere '=', ';', '[]' und Leerzeichen), dürfen aber keine geschweiften Klammern enthalten. Werte, die maskiert werden müssen und geschweifte Klammern enthalten, müssen zu einer properties-Auflistung hinzugefügt werden.  
  
> [!NOTE]  
>  Leerräume innerhalb der Klammern sind literal und werden nicht gekürzt.  
  
##  <a name="connecting-with-integrated-authentication-on-windows"></a><a name="Connectingintegrated"></a> Herstellen einer Verbindung mit integrierter Authentifizierung unter Windows  
 Der JDBC-Treiber unterstützt über die integratedSecurity-Verbindungszeichenfolgeneigenschaft die Verwendung der integrierten Authentifizierung vom Typ 2 auf Windows-Betriebssystemen. Wenn Sie die integrierte Authentifizierung verwenden möchten, müssen Sie die Datei mssql-jdbc_auth-\<version>-\<arch>.dll in ein Verzeichnis im Windows-Systempfad des Computers kopieren, auf dem der JDBC-Treiber installiert ist.  
  
 Die mssql-jdbc_auth-\<version>-\<arch>.dll-Dateien werden im folgenden Pfad installiert:  
  
 \<*Installationsverzeichnis*>\sqljdbc_\<*Version*>\\<*Sprache*>\auth\  
  
 Unter [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]Herstellen von Verbindungen mit SQL Server mit der integrierten Kerberos-Authentifizierung[ finden Sie für alle vom ](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md) unterstützten Betriebssysteme eine Beschreibung einer in [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] eingeführten Funktion, dank derer eine Anwendung mithilfe der integrierten Kerberos-Authentifizierung Typ 4 eine Verbindung mit einer Datenbank herstellen kann.  
  
> [!NOTE]  
>  Wenn Sie eine 32-Bit-JVM (Java Virtual Machine) ausführen, verwenden Sie die Datei mssql-jdbc_auth-\<version>-\<arch>.dll im Ordner x86, auch wenn es sich bei dem Betriebssystem um die x64-Version handelt. Wenn Sie eine 64-Bit-JVM mit einem x64-Prozessor ausführen, verwenden Sie die Datei mssql-jdbc_auth-\<version>-\<arch>.dll im Ordner x64.  
  
 Alternativ können Sie mit der java.libary.path-Systemeigenschaft das Verzeichnis von mssql-jdbc_auth-\<version>-\<arch>.dll angeben. Wenn der JDBC-Treiber beispielsweise im Standardverzeichnis installiert ist, können Sie den Speicherort der DLL beim Start der Java-Anwendung mit dem folgenden VM-Argument (Virtual Machine) angeben:  
  
 `-Djava.library.path=C:\Microsoft JDBC Driver 6.4 for SQL Server\sqljdbc_<version>\enu\auth\x86`  
  
## <a name="connecting-with-ipv6-addresses"></a>Herstellen von Verbindungen mit IPv6-Adressen  
 Der JDBC-Treiber unterstützt die Verwendung von IPv6-Adressen in der properties-Auflistung der Verbindung und in der serverName-Eigenschaft der Verbindungszeichenfolge. Der ursprüngliche serverName-Wert. z.B. jdbc:*sqlserver*://*serverName*, wird in Verbindungszeichenfolgen nicht für IPv6-Adressen unterstützt. Für *serverName* kann in allen Fällen anstatt einer IPv6-Adresse problemlos ein Name in der Verbindung verwendet werden. Die folgenden Beispiele enthalten weitere Informationen.  
  
 **Verwenden der serverName-Eigenschaft**  
  
 `jdbc:sqlserver://;serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1;integratedSecurity=true;`  
  
 **Verwenden der Auflistung von Eigenschaften**  
  
 `Properties pro = new Properties();`  
  
 `pro.setProperty("serverName", "serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1");`  
  
 `Connection con = DriverManager.getConnection("jdbc:sqlserver://;integratedSecurity=true;", pro);`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbinden mit SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
