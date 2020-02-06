---
title: Problembehandlung
description: Bietet einen Ausgangspunkt für das Beheben von bekannten Problemen
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c9be3a8dff314f6645029fb54803ad30dc04db27
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727567"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Problembehandlung bei Machine Learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Verwenden Sie diesen Artikel als Ausgangspunkt für das Beheben von bekannten Problemen.

## <a name="known-issues"></a>Bekannte Probleme

In den folgenden Artikeln werden bekannte Probleme mit der aktuellen Version und der Vorgängerversion beschrieben:

+ [Bekannte Probleme bei R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Versionsanmerkungen zu SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [SQL Server 2017 release notes (Versionsanmerkungen zu SQL Server 2017)](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Sammeln von Systeminformationen

Wenn ein Fehler aufgetreten ist oder Sie ein Problem in Ihrer Umgebung nachvollziehen müssen, ist es wichtig, dass Sie zusammengehörige Informationen systematisch sammeln. Der folgende Artikel enthält eine Liste von Informationen, die die Problembehandlung bei der Selbsthilfe und das Senden einer Anfrage an den technischen Support erleichtern.

+ [Problembehandlung bei der Datensammlung für Machine Learning](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Anleitungen zur Einrichtung und Konfiguration

Nehmen Sie die folgenden Artikel als Ausgangspunkt, wenn Sie Machine Learning noch nicht mit SQL Server eingerichtet haben oder wenn Sie dieses Feature hinzufügen möchten:

+ [Installieren von SQL Server Machine Learning Services (datenbankintern)](install/sql-machine-learning-services-windows-install.md)
+ [Installieren von SQL Server Machine Learning Server (eigenständig)](install/sql-machine-learning-standalone-windows-install.md)
+ [Einrichten der Eingabeaufforderung](install/sql-ml-component-commandline-install.md)
+ [Offlineeinrichtung (kein Internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Konfiguration

Die folgenden Artikel enthalten Informationen zu Standards und zum Anpassen der Konfiguration für Machine Learning für eine Instanz:

+ [Skalieren der gleichzeitigen Ausführung externer Skripts in SQL Server Machine Learning Services](administration/modify-user-account-pool.md)   
+ [Konfigurieren und Verwalten von Advanced Analytics-Erweiterungen](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Erstellen von Ressourcenpools](r/how-to-create-a-resource-pool-for-r.md)
+ [Optimierung für R-Arbeitsauslastungen](r/operationalizing-your-r-code.md)
