---
title: SqlClient-Unterstützung für LocalDB
description: Beschreibt die SqlClient-Unterstützung für LocalDB-Datenbanken
ms.date: 08/15/2019
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 189d0a2997b256f9c9b615fc81b5b9ed3ef46a5c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918725"
---
# <a name="sqlclient-support-for-localdb"></a>SqlClient-Unterstützung für LocalDB

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Ab der SQL Server-Version mit dem Codenamen „Denali“ ist eine vereinfachte Version von SQL Server mit dem Namen „LocalDB“ verfügbar. In diesem Artikel wird erläutert, wie Sie eine Verbindung mit einer LocalDB-Datenbank herstellen können.  
  
## <a name="remarks"></a>Bemerkungen  
Weitere Informationen zu LocalDB, einschließlich der Installation von LocalDB und der Konfiguration der LocalDB-Instanz, finden Sie in der SQL Server-Onlinedokumentation.  
  
Sie können LocalDB für Folgendes nutzen:  
  
- Erstellen und Starten von LocalDB-Instanzen mit einer sqllocaldb.exe- oder einer app.config-Datei  
  
- Verwenden Sie „sqlcmd.exe“, um Datenbanken in einer LocalDB-Instanz hinzuzufügen und zu ändern. Beispiel: `sqlcmd -S (localdb)\myinst`.  
  
- Verwenden des `AttachDBFilename`-Schlüsselworts für eine Verbindungszeichenfolge zum Hinzufügen einer Datenbank zu Ihr LocalDB-Instanz. Wenn Sie `AttachDBFilename` verwenden und den Namen der Datenbank nicht mit dem Schlüsselwort der `Database`-Verbindungszeichenfolge angeben, wird die Datenbank aus der LocalDB-Instanz entfernt, wenn die Anwendung geschlossen wird.  
  
- Geben Sie in der Verbindungszeichenfolge eine LocalDB-Instanz an: Wenn Ihr Instanzname beispielsweise `myInstance` lautet, enthält die Verbindungszeichenfolge folgende Elemente:  
  
```console
server=(localdb)\\myInstance  
```  
  
`User Instance=True` ist nicht zulässig, wenn eine Verbindung mit einer LocalDB-Datenbank hergestellt wird.  
  
Sie können LocalDB aus dem [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065) herunterladen. Wenn Sie sqlcmd.exe verwenden, um Daten in der LocalDB-Instanz zu ändern, benötigen Sie sqlcmd von SQ 2012, das auch aus dem SQL Server 2012 Feature Pack abrufbar ist.  
  
## <a name="programmatically-create-a-named-instance"></a>Programmgesteuertes Erstellen einer benannten Instanz  
Eine Anwendung kann wie folgt eine benannte Instanz erstellen und eine Datenbank angeben:  
  
- Geben Sie wie folgt die LocalDB-Instanzen an, die in der Datei „app.config“ erstellt werden sollen.  Die Versionsnummer der Instanz sollte mit der Versionsnummer der LocalDB-Installation identisch sein.  
  
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
  
- Geben Sie den Namen der Instanz mithilfe des Schlüsselworts `server` für die Verbindungszeichenfolge an.  Der im `server`-Schlüsselwort für die Verbindungszeichenfolge angegebene Instanzname muss mit dem Namen übereinstimmen, der in der Datei app.config angegeben ist.  
  
- Verwenden Sie das Schlüsselwort `AttachDBFilename` für die Verbindungszeichenfolge, um die MDF-Datei anzugeben.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Features und ADO.NET](sql-server-features-adonet.md)
