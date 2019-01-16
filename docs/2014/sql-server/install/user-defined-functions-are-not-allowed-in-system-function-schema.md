---
title: Benutzerdefinierte Funktionen sind in ' system_function_schema ' nicht zulässig. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7c21521fbdd4a4e80ed196c67c72f790341f020
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54254275"
---
# <a name="user-defined-functions-are-not-allowed-in-systemfunctionschema"></a>Benutzerdefinierte Funktionen sind in 'system_function_schema' unzulässig
  Der Upgrade Advisor hat erkannt, benutzerdefinierte Funktionen, die nicht dokumentierte Benutzer gehören **System_function_schema**. Sie können eine benutzerdefinierte Systemfunktion erstellen, indem Sie diesen Benutzer angeben. Die **System_function_schema** Benutzername ist nicht vorhanden, und die Benutzer-ID, die diesem Namen zugeordnet ist (UID = 4) ist reserviert für die **Sys** Schema und den internen Gebrauch beschränkt ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Die Speicherung und der Zugriff auf Systemobjekte ändern sich wie folgt:  
  
-   Systemobjekte werden in der schreibgeschützten gespeichert **Ressource** , und direkte systemobjektupdates sind nicht zulässig.  
  
     Systemobjekte erscheinen logisch im der **Sys** -Schema jeder Datenbank. Dadurch wird die Fähigkeit beibehalten, Systemfunktionen von einer beliebigen Datenbank durch Angeben eines einteiligen Funktionsnamens aufzurufen. Zum Beispiel kann die Anweisung, `SELECT * FROM fn_helpcollations()` von jeder Datenbank ausgeführt werden.  
  
-   Der nicht dokumentierte Benutzer **System_function_schema** wurde entfernt.  
  
-   Der Benutzer-ID zugeordnet **System_function_schema** (UID = 4) ist reserviert für die **Sys** Schema und den internen Gebrauch beschränkt ist.  
  
 Diese Änderungen haben folgende Auswirkungen auf benutzerdefinierte Systemfunktionen:  
  
-   Anweisungen von Data Definition Language (DDL), die auf verweisen **System_function_schema** schlägt fehl. Z. B. die Anweisung `CREATE FUNCTION system`_`function` \_ `schema.fn` \_ `MySystemFunction` ... ist nicht erfolgreich.  
  
-   Nach der Aktualisierung auf [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], vorhandene Objekte, die im Besitz befinden **System_function_schema** befinden sich nur in der **Sys** Schema der **master** Datenbank. Da Systemobjekte nicht geändert werden können, diese Funktionen können nie geändert oder gelöscht werden, aus der **master** Datenbank. Darüber hinaus können diese Funktionen nicht von anderen Datenbanken durch Angabe eines einteiligen Funktionsnamens aufgerufen werden.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Vor dem Upgrade führen Sie die folgenden Tasks aus:  
  
1.  Ändern Sie den Besitz an vorhandenen benutzerdefinierten Funktionen zu **Dbo** mithilfe der **Sp_changeobjectowner** gespeicherten Systemprozedur.  
  
2.  Sie sollten die Funktion umbenennen, damit sie nicht das Präfix 'fn_' verwendet. Dadurch werden potenzielle Namenskonflikte mit aktuellen oder zukünftigen Systemfunktionen vermieden.  
  
3.  Fügen Sie eine Kopie der geänderten Funktionen in jeder Datenbank hinzu, die sie verwendet.  
  
4.  Ersetzen Sie Verweise auf **System_function_schema** mit **Dbo** in allen Skripts, User-defined Function, DDL-Anweisungen enthalten.  
  
5.  Ändern Sie die Skripts, die rufen diese Funktionen zur Verwendung von entweder der zweiteilige Name Dbo **.** _Function_name_, oder den dreiteiligen Namen _Database_name_**.** Dbo. *Function_name*.  
  
 Weitere Informationen finden Sie in den folgenden Themen in der SQL Server-Onlinedokumentation:  
  
-   "sp_changeobjectowner"  
  
-   "Trennung von Benutzer und Schema"  
  
-   "Ressourcendatenbank"  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)   
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Entfernen Sie Anweisungen, mit die Systemobjekte geändert](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md)   
 [Entfernen Sie Anweisungen, mit denen Systemobjekte gelöscht werden](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
