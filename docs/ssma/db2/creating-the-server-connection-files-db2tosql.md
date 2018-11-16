---
title: Erstellen den Server Connection Files (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 685419f6-8606-462c-be12-8bace45bede6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ea6d9a77cc7639bc9adc8daa38f12d0e21dbfb71
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664350"
---
# <a name="creating-the-server-connection-files-db2tosql"></a>Erstellen den Server Connection Files (DB2ToSQL)
Informationen zum Server kann entweder in den Bereich "Server", der Skriptdatei oder in eine separate Verbindung Serverdatei angegeben werden. Der Parameter über die Befehlszeile für die Server-Verbindungsdatei ist, `-c <serverconnectionfile>`. Wenn die gleiche Id in die Skriptdatei und die Server-Connection-Datei vorhanden ist, wird die Definition des Servers in der Skriptdatei als betrachtet.  
  
**Beispiel: 1**  
  
```  
<!--Sample of server connection file commands -->  
  
<db2 name="<source-server-unique-name>">  
  
    <standard-mode>  
  
      <connection-provider value ="OleDB Provider"/>  
  
      <!-- Defines server manager to connect.  
  
              Available manager attribute values  
  
              • zOs      - upgrades the project (default)  
  
              • LUW       - displays an error and halts the execution-->  
  
      <database-manager value="$Db2Manager$"/>  
  
      <server-name value="$Db2HostName$" />  
  
      <port value="$Db2Port$" />  
  
      <initial-catalog value="$Db2Instance$" />  
  
      <user-id value="$Db2UserName$" />  
  
      <password value="$Db2Password$"/>  
  
    </standard-mode>  
  
</db2>  
```  
  
```  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication>  
  
    <server value="<server-name>"/>  
  
    <database value="<database-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt in der Konsole ausgeführt wird [Executing the SSMA Console ausführen &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Executing the SSMA Console (Ausführen der SSMA-Konsole)](https://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
