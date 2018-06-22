---
title: Benutzerdefinierte Funktionen sind in ' system_function_schema ' nicht zulässig. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16c6cf618028d56a3b09cdad8da4cfd9eb9309f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058622"
---
# <a name="user-defined-functions-are-not-allowed-in-systemfunctionschema"></a>Benutzerdefinierte Funktionen sind in 'system_function_schema' unzulässig
  Der Upgrade Advisor hat erkannt, benutzerdefinierte Funktionen, die nicht dokumentierte Benutzer gehören **System_function_schema**. Sie können eine benutzerdefinierte Systemfunktion erstellen, indem Sie diesen Benutzer angeben. Die **System_function_schema** Benutzername ist nicht vorhanden, und die Benutzer-ID, die diesen Namen zugeordnet ist (UID = 4) ist reserviert für die **Sys** Schema und den internen Gebrauch beschränkt ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Die Speicherung und der Zugriff auf Systemobjekte ändern sich wie folgt:  
  
-   Systemobjekte werden in der schreibgeschützten gespeichert **Ressource** , und direkte systemobjektupdates sind nicht zulässig.  
  
     Systemobjekte erscheinen logisch im die **Sys** -Schema jeder Datenbank. Dadurch wird die Fähigkeit beibehalten, Systemfunktionen von einer beliebigen Datenbank durch Angeben eines einteiligen Funktionsnamens aufzurufen. Zum Beispiel kann die Anweisung, `SELECT * FROM fn_helpcollations()` von jeder Datenbank ausgeführt werden.  
  
-   Die nicht dokumentierte Benutzer **System_function_schema** wurde entfernt.  
  
-   Der Benutzer-ID zugeordnet **System_function_schema** (UID = 4) ist reserviert für die **Sys** Schema und den internen Gebrauch beschränkt ist.  
  
 Diese Änderungen haben folgende Auswirkungen auf benutzerdefinierte Systemfunktionen:  
  
-   Anweisungen von Data Definition Language (DDL), die auf verweisen **System_function_schema** schlägt fehl. Beispielsweise ist die Anweisung `CREATE FUNCTION system`_`function` \_ `schema.fn` \_ `MySystemFunction` ... ist nicht erfolgreich.  
  
-   Nach dem upgrade auf [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], vorhandene Objekte, die im Besitz von **System_function_schema** sind nur in enthalten die **Sys** Schema der **master** Datenbank. Da Systemobjekte nicht geändert werden können, diese Funktionen können nicht geändert oder gelöscht werden aus der **master** Datenbank. Darüber hinaus können diese Funktionen nicht von anderen Datenbanken durch Angabe eines einteiligen Funktionsnamens aufgerufen werden.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Vor dem Upgrade führen Sie die folgenden Tasks aus:  
  
1.  Ändern Sie den Besitz an vorhandenen benutzerdefinierten Funktionen zu **Dbo** mithilfe der **Sp_changeobjectowner** gespeicherten Systemprozedur.  
  
2.  Sie sollten die Funktion umbenennen, damit sie nicht das Präfix 'fn_' verwendet. Dadurch werden potenzielle Namenskonflikte mit aktuellen oder zukünftigen Systemfunktionen vermieden.  
  
3.  Fügen Sie eine Kopie der geänderten Funktionen in jeder Datenbank hinzu, die sie verwendet.  
  
4.  Ersetzen Sie Verweise auf **System_function_schema** mit **Dbo** in allen Skripts, die eine benutzerdefinierte Funktion DDL-Anweisungen enthalten.  
  
5.  Ändern von Skripts, die rufen diese Funktionen zum Verwenden von entweder der zweiteilige Name Dbo **. *** Function_name*, oder den dreiteiligen Namen *Database_name ***.** Dbo.* Function_name *.  
  
 Weitere Informationen finden Sie in den folgenden Themen in der SQL Server-Onlinedokumentation:  
  
-   "sp_changeobjectowner"  
  
-   "Trennung von Benutzer und Schema"  
  
-   "Ressourcendatenbank"  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)   
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Entfernen Sie Anweisungen, die Systemobjekte ändern](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md)   
 [Entfernen Sie Anweisungen, mit denen Systemobjekte gelöscht](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
