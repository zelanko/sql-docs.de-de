---
title: Erstellen der Server Verbindungs Dateien (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Creating Server Connection Files
- Sybase Console,Server Connection File Validation
ms.assetid: 35ef396f-9f98-429d-9fc5-4f413d08fb37
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: d50dead28fa182c946ec1abf0ac9cc4bb3f052d9
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87931883"
---
# <a name="creating-the-server-connection-files-sybasetosql"></a>Erstellen der Serververbindungsdateien (SybaseToSQL)
Server Informationen können entweder im Abschnitt Server der Skriptdatei oder in einer separaten Server Verbindungs Datei angegeben werden. Der Befehlszeilenparameter für die Server Verbindungs Datei ist, `-c <serverconnectionfile>` . Wenn dieselbe Server-ID sowohl in der Skriptdatei als auch in der Server Verbindungs Datei vorhanden ist, wird die Server Definition in der Skriptdatei berücksichtigt.  
  
**Beispiel:**  
  
```  
1.<!--Sample of server connection file commands -->  
  
<sybase name="<source-server-unique-name>">  
  
  <standard-mode>  
  
    <provider value="Ole DB Provider"/>  
  
    <server-name value="<server-name>"/>  
  
    <server-port value="<port>"/>  
  
    <user-id value="<password>"/>  
  
  </standard-mode>  
  
</sybase>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication>  
  
    <database value="<database-name>"/>  
  
    <server value="<server-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
    <encrypt value="<true/false>"/>  
  
    <trust-server-certificate value="<true/false>"/>  
  
  </sql-server-authentication >  
  
</sql-server>  
```  
  
```  
2.<!-Sample of server connection file commands-->  
<sybase name="<source-server-unique-name>">  
  
  <advanced-mode>  
  
    <connection-string value="User ID=<user-name>;Password=<password>;Provider=ASEOLEDB.1;Server=<server-name>;Port=<port>;OLE DB Services = -2;"/>  
  
  </advanced-mode >  
  
</sybase>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication >  
  
    <database value="<database-name>"/>  
  
    <server value="<server-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
  </sql-server-authentication >  
  
</sql-server>  
```  
  
## <a name="server-connection-file-validation"></a>Überprüfung der Server Verbindungs Datei  
Der Benutzer kann seine Server Verbindungs Datei problemlos mit der Schema Definitionsdatei **S2SSConsoleScriptServersSchema. xsd** überprüfen, die im Ordner "Schemas" verfügbar ist.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt beim Betrieb der Konsole ist [die Ausführung der SSMA-Konsole &#40;sybasedesql&#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen der SSMA-Konsole](executing-the-ssma-console-sybasetosql.md)  
  
