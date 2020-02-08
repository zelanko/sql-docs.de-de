---
title: Neuigkeiten zu SQL Server 2019 für Linux
description: In diesem Artikel sind die Neuigkeiten für SQL Server 2019 für Linux zusammengestellt.
author: VanMSFT
ms.author: vanto
ms.date: 10/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 5183efa51afd89ad82d0cdcb6448996429b81d28
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "72890559"
---
# <a name="whats-new-for-sql-server-2019-on-linux"></a>Neuigkeiten zu SQL Server 2019 für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel sind die wichtigsten Features und Dienste beschrieben, die für SQL Server 2019 für Linux verfügbar sind. Informationen über Paketdownloads und bekannte Probleme finden Sie unter [Versionshinweise](sql-server-linux-release-notes-2019.md?view=sql-server-linux-ver15).

## <a name="updates"></a>Aktualisierungen

Die Updates wurden in SQL Server 2019 unter Linux vorgenommen:

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Replikationsunterstützung |[SQL Server Replication on Linux (SQL Server-Replikation unter Linux)](sql-server-linux-replication.md)
|Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC) |[How to configure MSDTC on Linux (Vorgehensweise: Konfigurieren von MSDTC unter Linux)](sql-server-linux-configure-msdtc.md) |
|OpenLDAP-Unterstützung für AD-Drittanbieter |[Tutorial: Use Active Directory authentication with SQL Server on Linux (Tutorial: Verwenden der Azure Active Directory-Authentifizierung mit SQL Server unter Linux)](sql-server-linux-active-directory-authentication.md) |
|Machine Learning unter Linux |[Configure Machine Learning on Linux (Konfigurieren von Machine Learning unter Linux)](sql-server-linux-setup-machine-learning.md) |
|`tempdb`-Verbesserungen | Standardmäßig erstellt eine neue Installation von SQL Server für Linux mehrere `tempdb`-Datendateien, deren Anzahl sich nach der Anzahl von logischen Kernen richtet (bis zu 8 Datendateien). Das gilt nicht für direkte Upgrades der Neben- oder Hauptversion. Jede `tempdb`-Datei ist 8 MB groß und wird automatisch um 64 MB vergrößert. Dieses Verhalten ähnelt dem der SQL Server-Standardinstallation unter Windows. |
| PolyBase unter Linux | [Installieren Sie PolyBase](../relational-databases/polybase/polybase-linux-setup.md) für Nicht-Hadoop-Connectors unter Linux.<br/><br/>[PolyBase type mapping (Typzuordnung mit PolyBase)](../relational-databases/polybase/polybase-type-mapping.md) |
| Unterstützung von Change Data Capture (CDC) | Change Data Capture (CDC) wird jetzt unter Linux für SQL Server 2019 unterstützt. |
| Microsoft Container Registry | [Microsoft Container Registry](https://www.ntweekly.com/2019/09/23/microsoft-container-registry-to-replace-docker-hub-for-new-images/) ersetzt nun Docker Hub für neue offizielle Microsoft-Containerimages, einschließlich [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |
| Container ohne Root-Berechtigung | Mit [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die Möglichkeit eingeführt, sicherere Container zu erstellen, indem der [!INCLUDE[sql-server](../includes/ssnoversion-md.md)]-Prozess standardmäßig als Nicht-Root-Benutzer gestartet wird. Weitere Informationen finden Sie unter [Erstellen und Ausführen von SQL Server-Containern als Nicht-Root-Benutzer](sql-server-linux-configure-docker.md#buildnonrootcontainer). |

## <a name="next-steps"></a>Nächste Schritte

Um SQL Server für Linux zu installieren, gehen Sie gemäß einem der folgenden Tutorials vor:

- [Installation unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md?view=sql-server-linux-ver15)
- [Installation unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md?view=sql-server-linux-ver15)
- [Installation unter Ubuntu](quickstart-install-connect-ubuntu.md?view=sql-server-linux-ver15)
- [Ausführung in Docker](quickstart-install-connect-docker.md?view=sql-server-linux-ver15)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

Antworten auf häufig gestellte Fragen finden Sie unter [Häufig gestellte Fragen zu SQL Server für Linux](sql-server-linux-faq.md). Weitere Verbesserungen, die in SQL Server 2019 eingeführt wurden, finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
