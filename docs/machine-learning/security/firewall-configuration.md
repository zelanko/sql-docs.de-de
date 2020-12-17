---
title: Firewallkonfiguration
description: Konfigurieren der Firewall für ausgehende Verbindungen von SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/17/2018
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 44fa8b361f74fb670dd5671bb9fbeaa9e635faad
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470701"
---
# <a name="firewall-configuration-for-sql-server-machine-learning-services"></a>Firewallkonfiguration für SQL Server- Machine Learning Services
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

In diesem Artikel werden die Überlegungen zur Firewallkonfiguration aufgeführt, die der Administrator oder Architekt bei der Verwendung der Machine Learning Services berücksichtigen sollte.

## <a name="default-firewall-rules"></a>Standardregeln für die Firewall

Standardmäßig werden ausgehende Verbindungen im Rahmen des SQL Server-Setups durch Erstellen von Firewallregeln deaktiviert.

In SQL Server 2016 und 2017 basieren diese Regeln auf lokalen Benutzerkonten, bei denen im Rahmen des Setups eine Ausgangsregel für **SQLRUserGroup** erstellt wurde, die für die Mitglieder den Netzwerkzugriff verweigert hat (jedes Workerkonto wurde gemäß der Regel als lokales Prinzip aufgeführt). Weitere Informationen zu SQLRUserGroup finden Sie unter [Sicherheitsübersicht für das Erweiterbarkeitsframework in SQL Server-Machine Learning Services](../../machine-learning/concepts/security.md#sqlrusergroup).

In SQL Server 2019 gibt es aufgrund des Wechsels zu AppContainer neue Firewallregeln, die auf AppContainer-SIDs basieren: jeweils eine Regel für jede der 20 von SQL Server-Setup erstellten AppContainer. Die Namenskonvention für den Namen der Firewallregel lautet **Netzwerkzugriff für AppContainer-00 in SQL Server-Instanz MSSQLSERVER blockieren**, wobei 00 für die Nummer des AppContainers (standardmäßig 00-20) steht und MSSQLSERVER der Name der SQL Server-Instanz ist.

> [!Note]
> Wenn Netzwerkaufrufe erforderlich sind, können Sie die Ausgangsregeln in der Windows-Firewall deaktivieren.

## <a name="restrict-network-access"></a>Einschränken des Netzwerkzugriffs

Bei einer empfohlenen Installation wird eine Windows-Firewallregel dazu verwendet, alle ausgehenden Netzwerkzugriffe durch externe Laufzeitprozesse zu blockieren. Firewallregeln sollten erstellt werden, um die externen Laufzeitprozesse daran zu hindern, Pakete herunterzuladen oder andere Netzwerke aufzurufen, die potenziell böswillig sein können.

Wenn Sie ein anderes Firewallprogramm verwenden, können Sie ebenfalls Regeln erstellen, um ausgehende Netzwerkverbindungen für die Laufzeitprozesse zu blockieren. Sie erreichen dies, indem Sie Regeln für die lokalen Benutzerkonten oder für die durch den Benutzerkontenpool dargestellte Gruppe festlegen.

Wir empfehlen Ihnen nachdrücklich, die Windows-Firewall (oder eine andere Firewall Ihrer Wahl) zu aktivieren, um den uneingeschränkten Netzwerkzugriff durch R- oder Python-Laufzeitprozesse zu verhindern.

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren der Windows-Firewall für eingehende Verbindungen](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)