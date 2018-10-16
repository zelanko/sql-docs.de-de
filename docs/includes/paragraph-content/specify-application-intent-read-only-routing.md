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
ms.openlocfilehash: 0e7d549c2f3b02349007815019cc47647f172f73
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072334"
---
## <a name="specifying-application-intent"></a>Angeben des Anwendungszwecks

Das Schlüsselwort **ApplicationIntent** kann in der Verbindungszeichenfolge angegeben werden. Die Werte zugewiesen sind **"ReadWrite"** oder **ReadOnly**. Der Standardwert ist **"ReadWrite"**.

Wenn **ApplicationIntent = ReadOnly**, fordert der Client eine lesearbeitslast aus, wenn eine Verbindung herstellen. Der Server erzwingt den Versuch zur Verbindungszeit und während einer **verwenden** database-Anweisung.

Das Schlüsselwort **ApplicationIntent** funktioniert nicht mit schreibgeschützten Legacydatenbanken.  


#### <a name="targets-of-readonly"></a>Ziele ReadOnly

Wenn eine Verbindung auswählt **ReadOnly**, eine der folgenden speziellen Konfigurationen, die für die Datenbank vorhanden sind, können die Verbindung zugewiesen:

- [Always On](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
    - Eine Datenbank kann Lesearbeitslasten in der Always On-Zieldatenbank zulassen bzw. nicht zulassen. Diese Option wird gesteuert durch Verwendung der **ALLOW_CONNECTIONS** -Klausel der **PRIMARY_ROLE** und **SECONDARY_ROLE** Transact-SQL-Anweisungen.

- [Georeplikation](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)

- [Horizontale Leseskalierung](https://docs.microsoft.com/azure/sql-database/sql-database-read-scale-out)

Wenn keines dieser spezielle Ziele verfügbar sind, wird die reguläre Datenbank gelesen werden.

&nbsp;

Die **ApplicationIntent** kann der Schlüsselwort *schreibgeschütztes routing*.


## <a name="read-only-routing"></a>Schreibgeschütztes Routing

Das schreibgeschützte Routing ist eine Funktion, die die Verfügbarkeit des schreibgeschützten Replikats einer Datenbank sicherstellen kann. Um schreibgeschütztes routing zu aktivieren, gelten die folgenden:

- Sie müssen eine Verbindung zum Verfügbarkeitsgruppenlistener einer AlwaysOn-Verfügbarkeitsgruppe herstellen.

- Das Schlüsselwort der **ApplicationIntent** -Verbindungszeichenfolge muss auf **ReadOnly**festgelegt werden.

- Die Verfügbarkeitsgruppe muss vom Datenbankadministrator konfiguriert werden, um schreibgeschütztes Routing zu aktivieren.

Mehrere Verbindungen mithilfe von schreibgeschütztem routing nicht alle mit demselben schreibgeschützten Replikat herstellen kann. Änderungen in der Datenbanksynchronisierung oder Änderungen in der Routingkonfiguration des Servers können zu Clientverbindungen mit anderen schreibgeschützten Replikaten führen. Sie können sicherstellen, dass alle schreibgeschützten Anforderungen mit demselben schreibgeschützten Replikat herstellen. Stellen Sie sicher diese gleichheitsprüfungen von *nicht* übergeben einen verfügbarkeitsgruppenlistener an das **Server** Schlüsselwort für Verbindungszeichenfolgen. Geben Sie stattdessen den Namen der schreibgeschützten Instanz an.

Schreibgeschütztes routing dauert länger als eine Verbindung mit dem primären Replikat. Die längere Dauer liegt darin begründet, dass schreibgeschütztes Routing zunächst eine Verbindung mit dem primären Replikat herstellt und dann nach dem besten verfügbaren lesbaren sekundären Replikat sucht. Aufgrund dieser mehrere Staps sollten Sie Ihre Anmeldungstimeout auf mindestens 30 Sekunden erhöhen.

