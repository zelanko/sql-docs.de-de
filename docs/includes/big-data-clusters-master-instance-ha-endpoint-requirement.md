---
ms.openlocfilehash: 497a564a10a3d35b33f47222fce8f89fe36bd15e
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73530926"
---
Bestimmte Vorgänge, einschließlich der Konfiguration von Servereinstellungen (auf Instanzebene) oder manuelles Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe, erfordern eine Verbindung mit der SQL Server-Instanz. Vorgänge wie `sp_configure`, `RESTORE DATABASE` oder ein beliebiger DDL-Befehl in einer Datenbank einer Verfügbarkeitsgruppe erfordern eine Verbindung mit der SQL Server-Instanz. Standardmäßig enthält ein Big Data-Cluster keinen Endpunkt, der eine Verbindung mit der Instanz ermöglicht. Sie müssen diesen Endpunkt manuell verfügbar machen.

Anweisungen finden Sie unter [Herstellen einer Verbindung mit Datenbanken auf dem primären Replikat](../big-data-cluster/deployment-high-availability.md#instance-connect).