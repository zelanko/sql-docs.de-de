---
title: Sqllocaldb-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 168a343c208c7b9d98f3f03a802e40488602a7d0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007069"
---
# <a name="sqllocaldb-utility"></a>SqlLocalDB-Hilfsprogramm
  Verwenden `SqlLocalDB` Sie das Hilfsprogramm, um eine Instanz von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **localdb**zu erstellen. Das- `SqlLocalDB` Hilfsprogramm (SqlLocalDB.exe) ist ein einfaches Befehlszeilen Tool, mit dem Benutzer und Entwickler eine Instanz von [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **localdb**erstellen und verwalten können. Weitere Informationen zur Verwendung von **localdb**finden Sie unter [SQL Server 2014 Express localdb](../database-engine/configure-windows/sql-server-2016-express-localdb.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a>Argumente  
 [ **Erstellen**  |  **c** ] *\<instance-name>* *\<instance-version>* [**-s** ]  
 Erstellt eine neue Instanz von [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. `SqlLocalDB`verwendet die Version der [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] Binärdateien, die durch das-Argument angegeben sind *\<instance-version>* . Die Versionsnummer wird im numerischen Format mit mindestens einer Dezimalzahl angegeben. Die Nebenversionsnummern (Service Packs) sind optional. Beispielsweise werden die folgenden zwei Versionsnummern akzeptiert: 11.0 oder 11.0.1186. Die angegebene Version muss auf dem Computer installiert sein. Wenn nicht angegeben, wird standardmäßig die Version des `SqlLocalDB` Hilfsprogramms verwendet. Durch Hinzufügen von **-s** wird die neue Instanz von **LocalDB**gestartet.  
  
 [ **share** | **h** ]  
 Gibt die angegebene private Instanz von **LocalDB** mithilfe des angegebenen freigegebenen Namens frei. Wenn die Benutzer-SID oder der Kontoname weggelassen wird, wird standardmäßig der aktuelle Benutzer verwendet.  
  
 [ **unshared** | **u** ]  
 Beendet die Freigabe der angegebenen freigegebenen Instanz von **LocalDB**.  
  
 [ **Löschen**  |  **d** ]*\<instance-name>*  
 Löscht die angegebene Instanz von [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.  
  
 [ **Start**  |  **s** ] " *\<instance-name>* "  
 Startet die angegebene Instanz von [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. Bei Erfolg gibt die Anweisung die Named Pipe-Adresse von **LocalDB**zurück.  
  
 [ **Abbrechen**  |  **p** ] *\<instance-name>* [**-i** ] [**-k** ]  
 Beendet die angegebene Instanz von [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. Durch Hinzufügen von **-i** wird das Herunterfahren der Instanz mit der `NOWAIT` Option angefordert Durch Hinzufügen von **-k** wird der Instanzprozess ohne Kontaktieren abgebrochen.  
  
 [ **Info**  |  **i** ] [ *\<instance-name>* ]  
 Listet alle Instanzen von [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** auf, die im Besitz des aktuellen Benutzers sind.  
  
 *\<instance-name>* gibt Name, Version, Status (wird ausgeführt oder beendet), Letzte Startzeit für die angegebene Instanz von [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **localdb**und den lokalen Pipenamen von **localdb**zurück.  
  
 [ **trace** | **t** ] **on** | **off**  
 **Trace on** aktiviert die Ablauf Verfolgung für die `SqlLocalDB` API-Aufrufe für den aktuellen Benutzer. **trace off** deaktiviert die Ablaufverfolgung.  
  
 **-?**  
 Gibt kurze Beschreibungen der einzelnen `SqlLocalDB` Optionen zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Für das *instance name* -Argument müssen die Regeln für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Bezeichner befolgt werden, oder das Argument muss in doppelte Anführungszeichen eingeschlossen werden.  
  
 Bei der Ausführung von „SqlLocalDB“ ohne Argumente wird der Hilfetext zurückgegeben.  
  
 Vorgänge, die keine Startvorgänge sind, können nur für eine Instanz ausgeführt werden, die zum derzeit angemeldeten Benutzer gehört.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-an-instance-of-localdb"></a>A. Erstellen einer Instanz von LocalDB  
 Im folgenden Beispiel wird mithilfe der [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **-Binärdateien eine Instanz von** LocalDB `DEPARTMENT` namens [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] erstellt und die Instanz gestartet.  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a>B. Verwenden einer freigegebenen Instanz von LocalDB  
 Öffnen Sie eine Eingabeaufforderung unter Administratorberechtigungen.  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd -S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 Führen Sie den folgenden Code aus, um unter Verwendung des **-Anmeldenamens eine Verbindung zur freigegebenen** LocalDB `NewLogin` -Instanz herzustellen.  
  
```  
sqlcmd -S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  
