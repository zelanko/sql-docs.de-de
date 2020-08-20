---
description: Erstellen der Server Verbindungs Dateien (DB2ToSQL)
title: Erstellen der Server Verbindungs Dateien (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 07/14/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 685419f6-8606-462c-be12-8bace45bede6
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5a27b74e529d917cf746d617e08dd44f9953a800
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497757"
---
# <a name="creating-the-server-connection-files-db2tosql"></a>Erstellen der Server Verbindungs Dateien (DB2ToSQL)

Server Informationen können entweder im Abschnitt Server der Skriptdatei oder in einer separaten Server Verbindungs Datei angegeben werden. Der Befehlszeilenparameter für die Server Verbindungs Datei ist, `-c <serverconnectionfile>` . Wenn dieselbe Server-ID sowohl in der Skriptdatei als auch in der Server Verbindungs Datei vorhanden ist, wird die Server Definition in der Skriptdatei berücksichtigt.

**Beispiel: 1**

```xml
<!-- Sample of server connection file commands -->
<db2 name="<source-server-unique-name>">
  <standard-mode>

    <connection-provider value="OleDB Provider" />

    <!-- Defines server manager to connect.
         Available manager attribute values
           • zOs - DB2 for z/OS
           • LUW - DB2 for Linux, Unix and Windows
           • DBi - DB2 for i -->
    <database-manager value="$Db2Manager$" />

    <server-name value="$Db2HostName$" />

    <port value="$Db2Port$" />

    <initial-catalog value="$Db2Instance$" />

    <user-id value="$Db2UserName$" />

    <password value="$Db2Password$"/>

  </standard-mode>
</db2>
```

```xml
<sql-server name="<target-server-unique-name>">
  <sql-server-authentication>

    <server value="<server-name>" />

    <database value="<database-name>" />
  
    <user-id value="<user-name>"/>
  
    <password value="<password>"/>

  </sql-server-authentication>
</sql-server>
```

## <a name="next-step"></a>Nächster Schritt

Der nächste Schritt beim Betrieb der Konsole ist [die Ausführung der SSMA-Konsole &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md)

## <a name="see-also"></a>Siehe auch

- [Ausführen der SSMA-Konsole](https://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)
