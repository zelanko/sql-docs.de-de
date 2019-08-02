---
title: Problembehandlung und häufig gestellte Fragen zu Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1573c260c3d34ba3f733316fbae2672b2f9adfb1
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715150"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Problembehandlung bei Machine Learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Verwenden Sie diese Seite als Ausgangspunkt für bekannte Probleme.

## <a name="known-issues"></a>Bekannte Probleme

In den folgenden Artikeln werden bekannte Probleme mit der aktuellen und der vorherigen Version beschrieben:

+ [Bekannte Probleme bei R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Versionsanmerkungen zu SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [SQL Server 2017 release notes (Versionsanmerkungen zu SQL Server 2017)](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Sammeln von Systeminformationen

Wenn ein Fehler aufgetreten ist oder Sie ein Problem in Ihrer Umgebung verstehen müssen, ist es wichtig, dass Sie zusammen gehörige Informationen systematisch sammeln. Der folgende Artikel enthält eine Liste der Informationen, die die Problembehandlung bei der Selbsthilfe und eine Anforderung für technischen Support erleichtern.

+ [Datensammlung für Machine Learning-Problembehandlung](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Anleitungen für Setup und Konfiguration

Beginnen Sie hier, wenn Sie Machine Learning nicht mit SQL Server eingerichtet haben, oder wenn Sie die Funktion hinzufügen möchten:

+ [Installieren von SQL Server Machine Learning Services (Daten bankeigen)](install/sql-machine-learning-services-windows-install.md)
+ [Installieren von SQL Server Machine Learning Server (eigenständig)](install/sql-machine-learning-standalone-windows-install.md)
+ [Setup für die Eingabeaufforderung](install/sql-ml-component-commandline-install.md)
+ [Offlineeinrichtung (kein Internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Konfiguration

Die folgenden Artikel enthalten Informationen zu Standardwerten und zum Anpassen der Konfiguration für Machine Learning auf einer-Instanz:

+ [Skalieren der gleichzeitigen Ausführung externer Skripts in SQL Server Machine Learning Services](administration/modify-user-account-pool.md)   
+ [Konfigurieren und Verwalten von Advanced Analytics-Erweiterungen](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Erstellen eines Ressourcenpools](r/how-to-create-a-resource-pool-for-r.md)
+ [Optimierung für R-Arbeits Auslastungen](r/operationalizing-your-r-code.md)
