---
title: Includedatei
description: Includedatei
services: sql-database
author: MightyPen
ms.service: sql-database
ms.topic: include
ms.date: 04/05/2018
ms.author: genemi
ms.custom: include file
ms.openlocfilehash: 842a7377bcd6bdcb649a78b2f31eb66de95bc5a3
ms.sourcegitcommit: a98ed7872afc055c65aa9697d571f8b300f6eeb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313396"
---
## <a name="specifying-application-intent"></a>Angeben des Anwendungszwecks

Das Schlüsselwort **ApplicationIntent** kann in der Verbindungszeichenfolge angegeben werden. Sind zuweisbare Werte **ReadWrite** oder **ReadOnly**. Die Standardeinstellung ist **ReadWrite**.

Wenn **ApplicationIntent = ReadOnly**, fordert der Client eine lesearbeitslast aus, wenn eine Verbindung herstellen. Der Server erzwingt den Zweck zur Verbindungszeit und während einer **verwenden** database-Anweisung.

Die **ApplicationIntent** -Schlüsselwort funktioniert nicht mit älteren schreibgeschützte Datenbanken.  


#### <a name="targets-of-readonly"></a>Ziele ReadOnly

Wenn eine Verbindung auswählt **ReadOnly**, wird die Verbindung auf eine der folgenden speziellen Konfigurationen, die für die Datenbank vorhanden sind, möglicherweise zugewiesen:

- [Always On](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
    - Eine Datenbank kann gestattet oder verweigert lesearbeitslasten auf die gewünschte Always On-Datenbank. Diese Auswahl wird gesteuert, mithilfe der **ALLOW_CONNECTIONS** -Klausel der **PRIMARY_ROLE** und **SECONDARY_ROLE** Transact-SQL-Anweisungen.

- [Geografische Replikation](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)

- [Lesen mit horizontaler Skalierung](https://docs.microsoft.com/azure/sql-database/sql-database-read-scale-out)

Wenn keine spezielle Ziele verfügbar sind, ist das reguläre Datenbank gelesen werden.

&nbsp;

Die **ApplicationIntent** Schlüsselwort ermöglicht *schreibgeschütztes routing*.


## <a name="read-only-routing"></a>Schreibgeschütztes Routing

Das schreibgeschützte Routing ist eine Funktion, die die Verfügbarkeit des schreibgeschützten Replikats einer Datenbank sicherstellen kann. Um schreibgeschütztes routing zu aktivieren, gelten die folgenden:

- Sie müssen eine Verbindung zum Verfügbarkeitsgruppenlistener einer AlwaysOn-Verfügbarkeitsgruppe herstellen.

- Das Schlüsselwort der **ApplicationIntent** -Verbindungszeichenfolge muss auf **ReadOnly**festgelegt werden.

- Die Verfügbarkeitsgruppe muss vom Datenbankadministrator konfiguriert werden, um schreibgeschütztes Routing zu aktivieren.

Mehrere Verbindungen mithilfe von nur-Lese routing nicht alle mit demselben schreibgeschützten Replikat herstellen kann. Änderungen in der Datenbanksynchronisierung oder Änderungen in der Routingkonfiguration des Servers können zu Clientverbindungen mit anderen schreibgeschützten Replikaten führen. Sie können sicherstellen, dass alle schreibgeschützten Anforderungen mit demselben schreibgeschützten Replikat herstellen. Stellen Sie sicher diese Gleichwertigkeit von *nicht* übergeben einen verfügbarkeitsgruppenlistener an die **Server** Verbindungszeichenfolgen-Schlüsselwort. Geben Sie stattdessen den Namen der schreibgeschützten Instanz an.

Schreibgeschütztes routing dauert länger als die Verbindung mit dem primären Replikat. Die Wartezeit längere liegt daran, dass schreibgeschütztes routing zuerst mit dem primären Replikat herstellt und sucht dann nach dem besten verfügbaren lesbaren sekundären Replikat. Aufgrund dieser mehrere Staps sollten Sie das Anmeldetimeout auf mindestens 30 Sekunden erhöhen.

