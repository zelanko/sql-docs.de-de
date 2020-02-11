---
title: Erstellen der Server Verbindungs Dateien (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 03d622c50a8760bbf1767bc8a4f79e215773695f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006608"
---
# <a name="creating-the-server-connection-files-accesstosql"></a>Erstellen der Server Verbindungs Dateien (accesstosql)
Server Informationen können entweder im Abschnitt Server der Skriptdatei angegeben werden. Server Informationen können auch in einer separaten Server Verbindungs Datei angegeben werden. Der Befehlszeilenparameter für die Server Verbindungs Datei ist `-c <serverconnectionfile>`. Wenn in den Skript-und Server Verbindungs Dateien dieselbe Server-ID vorhanden ist, wird die Server Definition in der Skriptdatei berücksichtigt.  
  
```xml  
<!--Sample of server connection file commands -->  
<!--Connection to SQL Server-->  
  
<sql-server name="target_3">  
  
  <sql-server-authentication>  
  
    <server value="$TargetServerName$"/>  
  
    <database value="$TargetDB$"/>  
  
    <user-id value="$TargetUserName$"/>  
  
    <password value="$TargetPassword$"/>  
  
    <encrypt value="true"/>  
  
    <trust-server-certificate value="true"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="target_azure">  
  
  <server value="$TargetAzureServerName$"/>  
  
  <database value="$TargetAzureDB$"/>  
  
  <user-id value="$TargetAzureUserName$"/>  
  
  <password value="$TargetAzurePassword$"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Überprüfung der Server Verbindungs Datei  
Der Benutzer kann seine Server Verbindungs Datei mit der Schema Definitionsdatei **"A2SSConsoleScriptServersSchema. xsd"** , die im Ordner "Schemas" verfügbar ist, problemlos überprüfen.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt beim Betrieb der Konsole ist [die Ausführung der SSMA-Konsole &#40;Access Token&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen der SSMA-Konsole (Zugriff)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
