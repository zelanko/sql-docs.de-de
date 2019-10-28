---
title: SqlClient-Unterstützung für LocalDB
description: Beschreibt die SqlClient-Unterstützung für localdb-Datenbanken.
ms.date: 08/15/2019
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 14cbe4ccf227c9462d2a2dc19fb42d913ca7bc5a
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451973"
---
# <a name="sqlclient-support-for-localdb"></a>SqlClient-Unterstützung für LocalDB

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Ab SQL Server Codename Denali ist eine vereinfachte Version von SQL Server mit dem Namen localdb verfügbar. In diesem Thema wird erläutert, wie eine Verbindung mit einer localdb-Datenbank hergestellt wird.  
  
## <a name="remarks"></a>Remarks  
Weitere Informationen zu LocalDB, einschließlich der Installation von LocalDB und der Konfiguration der LocalDB-Instanz, finden Sie in der SQL Server-Onlinedokumentation.  
  
Zusammenfassend, was Sie mit localdb tun können:  
  
- Erstellen und starten Sie localdb-Instanzen mit der Datei "sqllocaldb. exe" oder der Datei "App. config".  
  
- Verwenden Sie „sqlcmd.exe“, um Datenbanken in einer LocalDB-Instanz hinzuzufügen und zu ändern. Beispiel: `sqlcmd -S (localdb)\myinst`.  
  
- Verwenden Sie das `AttachDBFilename` Verbindungs Zeichenfolgen-Schlüsselwort, um der localdb-Instanz eine Datenbank hinzuzufügen. Wenn Sie `AttachDBFilename` verwenden und den Namen der Datenbank nicht mit dem Schlüsselwort der `Database`-Verbindungszeichenfolge angeben, wird die Datenbank aus der LocalDB-Instanz entfernt, wenn die Anwendung geschlossen wird.  
  
- Geben Sie in der Verbindungszeichenfolge eine LocalDB-Instanz an: Der Instanzname lautet z. b. `myInstance`, die Verbindungs Zeichenfolge enthält Folgendes:  
  
```console
server=(localdb)\\myInstance  
```  
  
`User Instance=True` ist beim Herstellen einer Verbindung mit einer localdb-Datenbank nicht zulässig.  
  
Sie können LocalDB aus dem [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065) herunterladen. Wenn Sie sqlcmd.exe verwenden, um Daten in der LocalDB-Instanz zu ändern, benötigen Sie sqlcmd von SQ 2012, das auch aus dem SQL Server 2012 Feature Pack abrufbar ist.  
  
## <a name="programmatically-create-a-named-instance"></a>Programm gesteuertes Erstellen einer benannten Instanz  
Eine Anwendung kann eine benannte Instanz erstellen und eine Datenbank wie folgt angeben:  
  
- Geben Sie die localdb-Instanzen, die in der Datei app. config erstellt werden sollen, wie folgt an.  Die Versionsnummer der Instanz sollte mit der Versionsnummer der localdb-Installation identisch sein.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- Geben Sie den Namen der Instanz mithilfe des Schlüssel Worts der `server`-Verbindungs Zeichenfolge an.  Der im `server`-Schlüsselwort für die Verbindungszeichenfolge angegebene Instanzname muss mit dem Namen übereinstimmen, der in der Datei app.config angegeben ist.  
  
- Verwenden Sie das `AttachDBFilename` Verbindungs Zeichenfolgen-Schlüsselwort, um anzugeben. MDF-Datei.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Features und ADO.NET](sql-server-features-adonet.md)
