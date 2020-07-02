---
title: 'Befehlszeilen-Verwaltungs Tool: SqlLocalDB.exe | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apilocation:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c39272a1f8af7fce092f7aa31ac3a4f7ebd2263
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765255"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>Verwaltungstool für Befehlszeilen: SqlLocalDB.exe
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  SqlLocalDB.exe ist ein einfaches Tool, das dem Benutzer die einfache Verwaltung der LocalDB-Instanzen in der Befehlszeile ermöglicht. Es wird als einfacher Wrapper um die LocalDB Instanz-API implementiert. Wie in vielen ähnlichen SQL Server-Tools (zum Beispiel SQLCMD) werden Parameter als Befehlszeilenargumente an SqlLocalDB übergeben, und die Ausgabe wird an die Konsole gesendet.  
  
 SqlLocalDB ermöglicht Entwicklern die Verwendung von LocalDB, ohne Code zum Aufrufen der API schreiben zu müssen und ohne von anderen Tools abhängig zu sein, die dies erledigen müssten.  
  
## <a name="sqllocaldb-options"></a>SqlLocalDB-Optionen  
 SqlLocalDB unterstützt die folgenden Optionen.  
  
|Option|Funktionsbeschreibung|  
|------------|------------------|  
|`-?`|Druckt Hilfetext.|  
|`create\|c "instance name" [version-number] [-s]`|Erstellt eine neue LocalDB-Instanz mit einem angegebenen Namen und einer Version.<br /><br /> Wenn der [Versionsnummer]-Parameter weggelassen wird, wird standardmäßig die SqlLocalDB-Buildversion verwendet.<br /><br /> -s startet die neue LocalDB-Instanz nach dem Erstellen.|  
|`delete\|d "instance name"`|Löscht die LocalDB-Instanz mit dem angegebenen Namen.|  
|`start\|s "instance name"`|Startet die LocalDB-Instanz mit dem angegebenen Namen.|  
|`stop\|p "instance name" [-i\|-k]`|Beendet die LocalDB-Instanz mit dem angegebenen Namen, nachdem die Ausführung aktueller Abfragen beendet wird.<br /><br /> -i fordert das Herunterfahren der LocalDB-Instanz mit der NOWAIT-Option an.<br /><br /> -k bricht den LocalDB-Instanzprozess ohne Kontaktieren ab.|  
|`share\|h ["owner SID or account"] "private name" "shared name"`|Gibt die angegebene private Instanz mithilfe des angegebenen freigegebenen Namens frei. Wenn die Benutzer-SID oder der Kontoname weggelassen wird, wird standardmäßig der aktuelle Benutzer verwendet.|  
|`unshare\|u "shared name"`|Hebt die Freigabe der angegebenen freigegebenen LocalDB-Instanz auf.|  
|`info\|i`|Listet alle vorhandenen LocalDB-Instanzen im Besitz des aktuellen Benutzers und aller freigegebenen LocalDB-Instanzen auf.|  
|`info\|i "instance name"`|Druckt die Informationen zur angegebenen LocalDB-Instanz.|  
|`versions\|v`|Listet alle auf dem Computer installierten LocalDB-Versionen auf.|  
|||  
|`trace\|t on\|off`|Aktiviert und deaktiviert die Ablaufverfolgung.|  
  
 SqlLocalDB behandelt Leerzeichen als Trennzeichen. Sie müssen die Instanznamen mit Anführungszeichen umschließen, die Leerzeichen und Sonderzeichen enthalten. Beispiel:  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
