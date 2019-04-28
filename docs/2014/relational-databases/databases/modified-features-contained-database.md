---
title: Geänderte Funktionen (Enthaltene Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f78f4bdf08b9a5caf9b2654289bf181080efff02
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871514"
---
# <a name="modified-features-contained-database"></a>Geänderte Funktionen (Enthaltene Datenbank)
  Die folgenden Funktionen wurden geändert, damit sie von einer teilweise eigenständigen Datenbank unterstützt werden. Funktionen wurden i. d. R. so geändert, dass sie die Datenbankbegrenzung nicht überschreiten.  
  
 Weitere Informationen finden Sie unter [Contained Databases](contained-databases.md).  
  
## <a name="alter-database"></a>ALTER DATABASE  
  
### <a name="application-level"></a>Anwendungsebene  
 Wenn die ALTER DATABASE-Anweisung aus einer enthaltenen Datenbank heraus verwendet wird, unterscheidet sich die Syntax von der für eine nicht enthaltene Datenbank. Zu diesen Unterschieden zählen u. a. Einschränkungen für die Elemente der Anweisung, die sich über die Datenbank hinaus zur Instanz erstrecken. Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
### <a name="instance-level"></a>Instanzebene  
 Die Syntax für ALTER DATABASE bei Verwendung außerhalb einer enthaltenen Datenbank unterscheidet sich von der für nicht enthaltene Datenbanken. Diese Änderungen verhindern, dass die Datenbankbegrenzung überschritten wird. Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="create-database"></a>CREATE DATABASE  
 Die CREATE DATABASE-Syntax für eine enthaltene Datenbank unterscheidet sich von der für eine nicht enthaltene Datenbank. Informationen zu neuen Syntaxanforderungen und -optionen finden Sie unter [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
## <a name="temporary-tables"></a>Temporäre Tabellen  
 Lokale temporäre Tabellen sind in einer enthaltenen Datenbank zulässig, ihr Verhalten unterscheidet sich jedoch von dem temporärer Tabellen in nicht enthaltenen Datenbanken. In abhängigen Datenbanken werden temporäre Tabellendaten in der Sortierung von **tempdb** sortiert. In einer enthaltenen Datenbank werden temporäre Tabellendaten in der Sortierung der enthaltenen Datenbank sortiert.  
  
 Sämtliche Metadaten, die temporären Tabellen zugeordnet sind (z. B. Tabellen- und Spaltennamen, Indizes usw.) liegen in der Katalogsortierung vor.  
  
 Benannte Einschränkungen dürfen in temporären Tabellen nicht verwendet werden.  
  
 Temporäre Tabellen dürfen nicht auf benutzerdefinierte Typen, XML-Schemaauflistungen und benutzerdefinierte Funktionen verweisen.  
  
## <a name="collation"></a>Sortierung  
 Im nicht enthaltenen Datenbankmodell sind es drei separate sortierungstypen: -Datenbanksortierung, instanzsortierung und Tempdb-Sortierung. In enthaltenen Datenbanken hingegen werden nur zwei Sortierungen verwendet: die Datenbanksortierung und die neue Katalogsortierung. Weitere Details zur Sortierung in eigenständigen Datenbanken finden Sie unter [Contained Database Collations](contained-database-collations.md) .  
  
## <a name="user-options"></a>user options  
 Beim Aktivieren eigenständiger Datenbanken muss die [Benutzeroptionen-Option](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf 0 (null) festgelegt sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Contained Database Collations](contained-database-collations.md)   
 [Contained Databases](contained-databases.md)  
  
  
