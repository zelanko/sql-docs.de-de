---
title: Anwendungssicherheit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 940879b4-aa0f-41ce-a369-6cfc0e78e01d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 832cb6991ad095ba13226f80408fbd919db00623
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66770435"
---
# <a name="application-security"></a>Anwendungssicherheit
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwenden, müssen Sie Vorsichtsmaßnahmen ergreifen, um die Sicherheit der Anwendung sicherzustellen. Die folgenden Abschnitte enthalten Informationen zu den Schritten, die Sie zum Sichern der Anwendung ergreifen können.  
  
## <a name="using-java-policy-permissions"></a>Verwenden von Java-Richtlinienberechtigungen  
 Wenn Sie [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwenden, müssen Sie die für den JDBC-Treiber erforderlichen Java-Richtlinienberechtigungen angeben. Die JRE (Java Runtime Environment) stellt ein umfassendes Sicherheitsmodell bereit, mit dem zur Laufzeit ermittelt werden kann, ob ein Thread auf eine Ressource zugreifen kann. Dieser Zugriff kann durch Sicherheitsrichtliniendateien gesteuert werden. Die Richtliniendateien werden vom Entwickler und vom Systemadministrator des Containers verwaltet. Die in diesem Thema aufgeführten Berechtigungen wirken sich jedoch auf die Funktionsweise des JDBC-Treibers aus.  
  
 Eine normale Berechtigung in der Richtliniendatei sieht folgendermaßen aus:  
  
```  
// Example policy file entry.  
grant [signedBy <signer>,] [codeBase <code source>] {  
   permission  <class>  [<name> [, <action list>]];  
};  
```  
  
 Die folgende Codebasis muss auf die Codebasis des JDBC-Treibers beschränkt werden, damit die minimal erforderlichen Privilegien gewährt werden.  
  
```  
grant codeBase "file:/install_dir/lib/-" {  
  
// Grant access to data source.  
permission java.util.PropertyPermission "java.naming.*", "read,write";  
  
// Specify which hosts can be connected to.  
permission java.net.socketPermission "host:port", "connect";  
  
// Logger permission to take advantage of logging.  
permission java.util.logging.LoggingPermission;  
  
// Grant listen/connect/accept permissions to the driver if   
// connecting to a named instance as the client driver.   
// This connects to a udp service and listens for a response.  
permission java.net.SocketPermission "*", "listen, connect, accept";   
};   
```  
  
> [!NOTE]  
>  Der Code "file:/install_dir/lib/-" bezieht sich auf das Installationsverzeichnis des JDBC-Treibers.  
  
## <a name="protecting-server-communication"></a>Schützen der Serverkommunikation  
 Wenn Sie den JDBC-Treiber für die Kommunikation mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank verwenden, können Sie den Kommunikationskanal mit IPSec (Internet Protocol Security) und/oder SSL (Secure Sockets Layer) sichern.  
  
 Die SSL-Unterstützung kann verwendet werden, um zusätzlich zu IPSEC eine weitere Schutzebene bereitzustellen. Weitere Informationen zur Verwendung von SSL finden Sie unter [Using SSL Encryption](../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
