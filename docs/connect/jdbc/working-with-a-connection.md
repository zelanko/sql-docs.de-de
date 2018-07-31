---
title: Arbeiten mit einer Verbindung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbcd46cd9da1ab189aeafe77c7275aa103ea51f6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38060271"
---
# <a name="working-with-a-connection"></a>Arbeiten mit einer Verbindung
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Die folgenden Abschnitte enthalten Beispiele für die verschiedenen Möglichkeiten, um mit der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbank herzustellen.  
  
> [!NOTE]  
>  Wenn beim Herstellen von Verbindungen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] mit dem JDBC-Treiber Probleme auftreten, finden Sie unter [Behandlung von Verbindungsproblemen](../../connect/jdbc/troubleshooting-connectivity.md) Vorschläge zum Beheben der Probleme.  
  
## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>Erstellen einer Verbindung mit der DriverManager-Klasse  
 Die einfachste Vorgehensweise zum Erstellen einer Verbindung zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbank besteht darin, den JDBC-Treiber zu laden und wie im Folgenden dargestellt die getConnection-Methode der DriverManager-Klasse aufzurufen:  
  
```  
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 Bei diesem Verfahren wird eine Datenbankverbindung mit dem ersten verfügbaren Treiber in der Liste der Treiber erstellt, der erfolgreich eine Verbindung mit der angegebenen URL herstellen kann.  
  
> [!NOTE]  
>  Bei Verwendung der sqljdbc4.jar-Klassenbibliothek müssen Anwendungen den Treiber nicht mit der Class.forName-Methode explizit registrieren oder laden. Wenn die -Methode der -Klasse aufgerufen wird, wird aus der Gruppe der registrierten JDBC-Treiber ein geeigneter Treiber ausgewählt. Weitere Informationen finden Sie unter "Verwenden des JDBC-Treibers".  
  
## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>Erstellen einer Verbindung mit der SQLServerDriver-Klasse  
 Wenn Sie in der Liste der Treiber für DriverManager einen bestimmten Treiber angeben müssen, können Sie wie im Folgenden dargestellt eine Datenbankverbindung mit der [connect](../../connect/jdbc/reference/connect-method-sqlserverdriver.md)-Methode der [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md)-Klasse erstellen:  
  
```  
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```  
  
## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>Erstellen einer Verbindung mit der SQLServerDataSource-Klasse  
 Wenn Sie eine Verbindung mit der [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse erstellen müssen, können Sie verschiedene Festlegungsmethoden der Klasse verwenden, bevor Sie die [getConnection](../../connect/jdbc/reference/getconnection-method.md)-Methode aufrufen, z.B.:  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setUser("MyUserName");  
ds.setPassword("*****");  
ds.setServerName("localhost");  
ds.setPortNumber(1433);   
ds.setDatabaseName("AdventureWorks");  
Connection con = ds.getConnection();  
```  
  
## <a name="creating-a-connection-that-targets-a-very-specific-data-source"></a>Erstellen einer Verbindung mit eine sehr speziellen Datenquelle als Ziel  
 Wenn Sie eine Datenbankverbindung mit einer sehr speziellen Datenquelle herstellen müssen, können Sie mehrere Verfahren verwenden. Das jeweilige Verfahren hängt von den Eigenschaften ab, die Sie mit der Verbindungs-URL festlegen.  
  
 Um eine Verbindung zur Standardinstanz auf einem Remoteserver herzustellen, verwenden Sie die folgende URL:  
  
 `String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"`  
  
 Um eine Verbindung zu einem bestimmten Port eines Servers herzustellen, verwenden Sie die folgende URL:  
  
 `String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"`  
  
 Um eine Verbindung zu einer benannten Instanz eines Servers herzustellen, verwenden Sie die folgende URL:  
  
 `String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"`  
  
 Um eine Verbindung zu einer bestimmten Datenbank eines Servers herzustellen, verwenden Sie die folgende URL:  
  
 `String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"`  
  
 Weitere Beispiele für Verbindungs-URL finden Sie unter [Building the Connection URL](../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="creating-a-connection-with-a-custom-login-time-out"></a>Erstellen einer Verbindung mit einem benutzerdefinierten Anmeldetimeout  
 Wenn Sie Serverlast oder Netzwerkverkehr berücksichtigen müssen, können Sie eine Verbindung mit einem bestimmten Timeoutwert für die Anmeldung in Sekunden erstellen, wie z. B.:  
  
 `String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"`  
  
## <a name="create-a-connection-with-application-level-identity"></a>Erstellen einer Verbindung mit Identität auf Anwendungsebene  
 Wenn Sie Protokollierung und Profilerstellung verwenden, müssen Sie die Verbindung mit einer bestimmten Anwendung als Ursprung kennzeichnen, wie z. B.:  
  
 `String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"`  
  
## <a name="closing-a-connection"></a>Trennen einer Verbindung  
 Sie können durch Aufrufen der [close](../../connect/jdbc/reference/close-method-sqlserverconnection.md)-Methode der SQLServerConnection-Klasse eine Datenbankverbindung wie im Folgenden dargestellt explizit schließen:  
  
 `con.close();`  
  
 Dadurch werden die vom SQLServerConnection-Objekt verwendeten Datenbankressourcen freigegeben, bzw. die Verbindung in Poolszenarios werden an den Verbindungspool zurückgegeben.  
  
> [!NOTE]  
>  Durch den Aufruf der close-Methode wird auch ein Rollback aller anstehenden Transaktionen ausgeführt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verbinden von SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
