---
title: Problembehandlung bei Machine Learning in SQL Server
description: Dieser Artikel bietet einen Ausgangspunkt für das Beheben von Problemen im Zusammenhang mit SQL Machine Learning.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 05/31/2018
ms.topic: troubleshooting
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: e2d4d278f48cd453afb0666d0c9752c86b4a7e65
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470621"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Problembehandlung bei Machine Learning in SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Verwenden Sie diesen Artikel als Ausgangspunkt für das Beheben von Problemen, die bei der Verwendung von SQL Server Machine Learning auftreten.

## <a name="known-issues"></a>Bekannte Probleme

In den folgenden Artikeln werden bekannte Probleme mit der aktuellen Version und der Vorgängerversion beschrieben:

+ [Bekannte Probleme bei R Services](known-issues-for-sql-server-machine-learning-services.md)
+ [Versionsanmerkungen zu SQL Server 2016](../../sql-server/sql-server-2016-release-notes.md)
+ [SQL Server 2017 release notes (Versionsanmerkungen zu SQL Server 2017)](../../sql-server/sql-server-2017-release-notes.md)
+ [Versionsanmerkungen zu SQL Server 2019](../../sql-server/sql-server-version-15-release-notes.md)

## <a name="how-to-gather-system-information"></a>Sammeln von Systeminformationen

Wenn ein Fehler aufgetreten ist oder Sie ein Problem in Ihrer Umgebung nachvollziehen müssen, ist es wichtig, dass Sie zusammengehörige Informationen systematisch sammeln. Der folgende Artikel enthält eine Liste von Informationen, die die Problembehandlung bei der Selbsthilfe und das Senden einer Anfrage an den technischen Support erleichtern.

+ [Problembehandlung bei der Datensammlung für Machine Learning](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Anleitungen zur Einrichtung und Konfiguration

Nehmen Sie die folgenden Artikel als Ausgangspunkt, wenn Sie Machine Learning noch nicht mit SQL Server eingerichtet haben oder wenn Sie dieses Feature hinzufügen möchten:

+ [Installieren von SQL Server Machine Learning Services (datenbankintern)](../install/sql-machine-learning-services-windows-install.md)
+ [Installieren von SQL Server Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md)
+ [Einrichten der Eingabeaufforderung](../install/sql-ml-component-commandline-install.md)
+ [Offlineeinrichtung (kein Internet)](../install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Konfiguration

Die folgenden Artikel enthalten Informationen zu Standards und zum Anpassen der Konfiguration für Machine Learning für eine SQL Server-Instanz:

+ [Skalieren der gleichzeitigen Ausführung externer Skripts in SQL Server Machine Learning Services](../administration/scale-concurrent-execution-external-scripts.md)   
+ [Erstellen von Ressourcenpools](../administration/create-external-resource-pool.md)
+ [Optimierung für R-Arbeitsauslastungen](../r/operationalizing-your-r-code.md)
