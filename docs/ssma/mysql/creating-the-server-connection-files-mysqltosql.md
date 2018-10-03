---
title: Erstellen den Server Connection Files (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Server connection file validation
- Server connection files
ms.assetid: df0e970c-da0b-4118-b359-c9dcbbad16d6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bf218f229ad8f97e1bdcda086f19bd7517896873
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608618"
---
# <a name="creating-the-server-connection-files-mysqltosql"></a>Erstellen der Datenbankverbindungsdateien (MySqlToSql)
Informationen zum Server kann entweder in den Bereich "Server", der Skriptdatei oder in eine separate Verbindung Serverdatei angegeben werden. Der Parameter über die Befehlszeile für die Server-Verbindungsdatei ist, `-c <serverconnectionfile>`. Wenn die gleiche Id in die Skriptdatei und die Server-Connection-Datei vorhanden ist, wird die Definition des Servers in der Skriptdatei als betrachtet.  
  
**Beispiel:**  
  
```xml  
<!--Sample of server connection file commands -->  
  
<mysql name ="<source-server-unique-name>">  
  
   <standard-mode>  
  
      <server value ="<server-name>"/>  
  
      <user-id value ="<user-name>"/>  
  
      <password value ="<password>"/>  
  
      <port value ="<port>"/>  
  
   </standard-mode>  
  
</mysql>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
   <sql-server-authentication>  
  
      <server value="<server-name>"/>  
  
      <database value="<database-name>"/>  
  
      <user-id value="<user-name>"/>  
  
      <password value="<password>"/>  
  
      <encrypt value="<true/false>"/>  
  
      <trust-server-certificate value="<true/false>"/>  
  
   </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="<target-server-unique-name>">  
  
   <server value="<server-name>"/>  
  
   <database value="<database-name>"/>  
  
   <user-id value="<user-name>"/>  
  
   <password value="<password>"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Datei-Überprüfung von Server-Verbindung  
Benutzer kann ganz einfach überprüfen, seine Verbindung-Serverdatei anhand der Schemadefinitionsdatei **"M2SSConsoleScriptServersSchema.xsd"** in den Ordner "Schemas" verfügbar.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt in der Konsole ausgeführt wird [Executing the SSMA Console ausführen &#40;MySQLToSQL&#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Executing the SSMA Console ausführen (MySQL)](http://msdn.microsoft.com/en-us/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
