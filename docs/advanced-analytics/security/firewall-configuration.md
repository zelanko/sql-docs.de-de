---
title: Firewallkonfiguration
description: Konfigurieren der Firewall für ausgehende Verbindungen von SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c55f68a1134fee6477c52182ad66b8705e363296
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715594"
---
# <a name="firewall-configuration-for-sql-server-machine-learning-services"></a>Firewallkonfiguration für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die Überlegungen zur Firewallkonfiguration aufgeführt, die der Administrator oder Architekt bei der Verwendung der Machine Learning-Dienste berücksichtigen sollte.

## <a name="default-firewall-rules"></a>Standardmäßige Firewallregeln

Standardmäßig werden durch das SQL Server Setup ausgehende Verbindungen durch Erstellen von Firewallregeln deaktiviert.

In SQL Server 2016 und 2017 basieren diese Regeln auf lokalen Benutzerkonten, in denen Setup eine ausgehende Regel für **sqlrusergroup** erstellt hat, die den Netzwerk Zugriff auf seine Mitglieder verweigert hat (jedes Workerkonto wurde als lokales Prinzip für die Regel aufgeführt. Weitere Informationen zu sqlrusergroup finden Sie unter [Sicherheitsübersicht für das Erweiterbarkeit Framework in SQL Server Machine Learning Services](../../advanced-analytics/concepts/security.md#sqlrusergroup).

In SQL Server 2019 sind im Rahmen der Umstellung auf appcontainers neue Firewallregeln auf Basis von appcontainer SIDs vorhanden: eine für jeden der 20 appcontainers, die durch SQL Server-Setup erstellt wurden. Benennungs Konventionen für den Namen der Firewallregel sind das **Blockieren des Netzwerk Zugriffs für appcontainer-00 in SQL Server Instanz MSSQLSERVER**, wobei 00 die Nummer von appcontainer (standardmäßig 00-20) und MSSQLSERVER der Name der SQL Server Instanz ist.

> [!Note]
> Wenn Netzwerk Aufrufe erforderlich sind, können Sie die ausgehenden Regeln in der Windows-Firewall deaktivieren.

## <a name="restrict-network-access"></a>Einschränken des Netzwerk Zugriffs

In einer Standardinstallation wird eine Windows-Firewallregel verwendet, um den gesamten ausgehenden Netzwerk Zugriff auf externe Lauf Zeit Prozesse zu blockieren. Firewallregeln sollten erstellt werden, um zu verhindern, dass externe Lauf Zeit Prozesse Pakete herunterladen oder andere Netzwerk Aufrufe vornehmen, die potenziell schädlich sein könnten.

Wenn Sie ein anderes Firewallprogramm verwenden, können Sie auch Regeln erstellen, um ausgehende Netzwerkverbindungen für externe Laufzeiten zu blockieren, indem Sie Regeln für die lokalen Benutzerkonten oder für die durch den Benutzerkonten Pool dargestellte Gruppe festlegen.

Es wird dringend empfohlen, die Windows-Firewall (oder eine andere Firewall Ihrer Wahl) zu aktivieren, um einen uneingeschränkten Netzwerk Zugriff durch R-oder python-Laufzeiten zu verhindern.

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren der Windows-Firewall für eingehende Verbindungen](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)