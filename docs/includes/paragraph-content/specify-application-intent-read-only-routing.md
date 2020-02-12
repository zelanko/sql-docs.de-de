---
title: include file
description: include file
services: sql-database
author: MightyPen
ms.service: sql-database
ms.topic: include
ms.date: 04/05/2018
ms.author: genemi
ms.custom: include file
ms.openlocfilehash: 0e7d549c2f3b02349007815019cc47647f172f73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68213534"
---
## <a name="specifying-application-intent"></a>Angeben des Anwendungszwecks

Das Schlüsselwort **ApplicationIntent** kann in Ihrer Verbindungszeichenfolge angegeben werden. Es können die Werte **ReadWrite** oder **ReadOnly** zugewiesen werden. Der Standardwert lautet **ReadWrite**.

Im Fall von **ApplicationIntent=ReadOnly** fordert der Client eine Leseworkload an, wenn eine Verbindung hergestellt wird. Der Server erzwingt die Absicht zur Verbindungszeit und während einer **USE**-Datenbankanweisung.

Das Schlüsselwort **ApplicationIntent** funktioniert nicht mit schreibgeschützten Legacydatenbanken.  


#### <a name="targets-of-readonly"></a>Ziele von ReadOnly

Wenn eine Verbindung **ReadOnly** auswählt, wird sie einer der folgenden speziellen Konfigurationen zugewiesen, die für die Datenbank vorhanden sein können:

- [Always On](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
    - Eine Datenbank kann Lesearbeitslasten in der Always On-Zieldatenbank zulassen bzw. nicht zulassen. Diese Auswahl wird mit der **ALLOW_CONNECTIONS**-Klausel der Transact-SQL-Anweisungen **PRIMARY_ROLE** und **SECONDARY_ROLE** gesteuert.

- [Georeplikation](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)

- [Horizontale Leseskalierung](https://docs.microsoft.com/azure/sql-database/sql-database-read-scale-out)

Wenn keins dieser speziellen Ziele verfügbar ist, erfolgt der Lesevorgang in der regulären Datenbank.

&nbsp;

Das Schlüsselwort **ApplicationIntent** aktiviert das *schreibgeschützte Routing*.


## <a name="read-only-routing"></a>Schreibgeschütztes Routing

Das schreibgeschützte Routing ist eine Funktion, die die Verfügbarkeit des schreibgeschützten Replikats einer Datenbank sicherstellen kann. Zum Aktivieren des schreibgeschützten Routings gelten sämtliche der folgenden Voraussetzungen:

- Sie müssen eine Verbindung zum Verfügbarkeitsgruppenlistener einer AlwaysOn-Verfügbarkeitsgruppe herstellen.

- Das Schlüsselwort der **ApplicationIntent** -Verbindungszeichenfolge muss auf **ReadOnly**festgelegt werden.

- Die Verfügbarkeitsgruppe muss vom Datenbankadministrator konfiguriert werden, um schreibgeschütztes Routing zu aktivieren.

Mehrere Verbindungen, die jeweils das schreibgeschützte Routing verwenden, erfolgen möglicherweise nicht alle mit demselben schreibgeschützten Replikat. Änderungen in der Datenbanksynchronisierung oder Änderungen in der Routingkonfiguration des Servers können zu Clientverbindungen mit anderen schreibgeschützten Replikaten führen. Sie können sicherstellen, dass alle schreibgeschützten Anforderungen eine Verbindung mit demselben schreibgeschützten Replikat herstellen. Um dies zu erreichen, übergeben Sie *keinen* Verfügbarkeitsgruppenlistener an das Schlüsselwort **Server** der Verbindungszeichenfolge. Geben Sie stattdessen den Namen der schreibgeschützten Instanz an.

Das schreibgeschützte Routing kann länger dauern als das Herstellen einer Verbindung mit der primären Instanz. Die längere Dauer liegt darin begründet, dass schreibgeschütztes Routing zunächst eine Verbindung mit dem primären Replikat herstellt und dann nach dem besten verfügbaren lesbaren sekundären Replikat sucht. Da mehrere Schritte ausgeführt werden, sollten Sie das Anmeldungstimeout auf mindestens 30 Sekunden erhöhen.

