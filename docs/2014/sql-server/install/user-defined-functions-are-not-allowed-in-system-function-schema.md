---
title: Benutzerdefinierte Funktionen sind in system_function_schema nicht zulässig | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 10813b7bc0a97f0ba8a81f3f48447142659cd596
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091333"
---
# <a name="user-defined-functions-are-not-allowed-in-system_function_schema"></a>Benutzerdefinierte Funktionen sind in 'system_function_schema' unzulässig
  Der Upgrade Advisor hat benutzerdefinierte Funktionen erkannt, die sich im Besitz der nicht dokumentierten Benutzer **system_function_schema**befinden. Sie können eine benutzerdefinierte Systemfunktion erstellen, indem Sie diesen Benutzer angeben. Der **system_function_schema** Benutzername ist nicht vorhanden, und die mit diesem Namen (UID = 4) verknüpfte Benutzer-ID ist für das **sys** -Schema reserviert und nur auf die interne Verwendung beschränkt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Die Speicherung und der Zugriff auf Systemobjekte ändern sich wie folgt:  
  
-   System Objekte werden in der schreibgeschützten **Ressourcen** Datenbank gespeichert, und direkte Systemobjekt Updates sind nicht zulässig.  
  
     System Objekte werden logisch im **sys** -Schema jeder Datenbank angezeigt. Dadurch wird die Fähigkeit beibehalten, Systemfunktionen von einer beliebigen Datenbank durch Angeben eines einteiligen Funktionsnamens aufzurufen. Zum Beispiel kann die Anweisung, `SELECT * FROM fn_helpcollations()` von jeder Datenbank ausgeführt werden.  
  
-   Der nicht dokumentierte Benutzer **system_function_schema** wurde entfernt.  
  
-   Die mit **system_function_schema** (UID = 4) verknüpfte Benutzer-ID ist für das **sys** -Schema reserviert und nur auf die interne Verwendung beschränkt.  
  
 Diese Änderungen haben folgende Auswirkungen auf benutzerdefinierte Systemfunktionen:  
  
-   DDL-Anweisungen (Data Definition Language), die auf **system_function_schema** verweisen, können nicht ausgeführt werden. Beispielsweise ist die Anweisung `CREATE FUNCTION system`_`function` \_ `schema.fn` \_ `MySystemFunction` ... wird nicht erfolgreich ausgeführt.  
  
-   Nachdem Sie [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]auf aktualisiert haben, sind vorhandene Objekte, die sich im Besitz von **system_function_schema** befinden, nur im **sys** -Schema der **Master** -Datenbank enthalten. Da Systemobjekte nicht geändert werden können, können diese Funktionen nie geändert oder aus der **Master** -Datenbank gelöscht werden. Darüber hinaus können diese Funktionen nicht von anderen Datenbanken durch Angabe eines einteiligen Funktionsnamens aufgerufen werden.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Vor dem Upgrade führen Sie die folgenden Tasks aus:  
  
1.  Ändern Sie den Besitz vorhandener benutzerdefinierter Funktionen in **dbo** mithilfe der gespeicherten System Prozedur **sp_changeobjectowner** .  
  
2.  Sie sollten die Funktion umbenennen, damit sie nicht das Präfix 'fn_' verwendet. Dadurch werden potenzielle Namenskonflikte mit aktuellen oder zukünftigen Systemfunktionen vermieden.  
  
3.  Fügen Sie eine Kopie der geänderten Funktionen in jeder Datenbank hinzu, die sie verwendet.  
  
4.  Ersetzen Sie Verweise auf **system_function_schema** durch **dbo** in allen Skripts, die DDL-Anweisungen für benutzerdefinierte Funktionen enthalten.  
  
5.  Ändern Sie Skripts, die diese Funktionen aufrufen, um entweder den zweiteiligen Namen dbo zu verwenden **.** _function_name_oder der dreiteilige Name _database_name_**.** dbo. *function_name*.  
  
 Weitere Informationen finden Sie in den folgenden Themen in der SQL Server-Onlinedokumentation:  
  
-   "sp_changeobjectowner"  
  
-   "Trennung von Benutzer und Schema"  
  
-   "Ressourcendatenbank"  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)   
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Entfernen von Anweisungen, mit denen Systemobjekte geändert werden](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md)   
 [Entfernen Sie Anweisungen, mit denen Systemobjekte gelöscht werden](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
