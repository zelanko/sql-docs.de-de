---
title: Problembehandlung sowie häufig gestellte Fragen für Machine Learning in SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6ef72ae56973e695b96f0dfac7c0a3414bca5225
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707358"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Problembehandlung bei Machine Learning in der SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Verwenden Sie diese Seite als Ausgangspunkt für die Arbeit über bekannte Probleme.

**Gilt für:** SQL Server 2016-R-Services, SqlServer 2017 Machine Learning-Dienste (R und Python)

## <a name="known-issues"></a>Bekannte Probleme

In den folgenden Artikeln werden bekannte Probleme mit der aktuellen und vorherigen Versionen beschrieben:

+ [Bekannte Probleme für R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Versionsanmerkungen zu SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [SQL Server 2017 release notes (Versionsanmerkungen zu SQL Server 2017)](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Gewusst wie: Sammeln von Systeminformationen

Wenn Sie haben, ist ein Fehler aufgetreten, oder ein Problem in Ihrer Umgebung kennen müssen, ist es wichtig, dass Sie systematisch Informationen sammeln. Im folgende Artikel enthält eine Liste von Informationen, die zur Selbsthilfe Problembehandlung vereinfacht oder eine Anforderung für den technischen Support.

+ [Die Datensammlung für die Problembehandlung von Machine learning](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Setup- und Konfigurations-Handbücher

Beginnen Sie hier, wenn Sie Machine Learning mit SQL Server nicht eingerichtet haben, oder wenn Sie die Funktion hinzufügen möchten:

+ [Installieren von SQL Server 2017 Machine Learning-Services (Datenbankintern)](install/sql-machine-learning-services-windows-install.md)
+ [Installieren von SQL Server 2017 Machine Learning-Server (eigenständig)](install/sql-machine-learning-standalone-windows-install.md)
+ [Installieren von SQL Server 2016 R Services (Datenbankintern)](install/sql-r-services-windows-install.md)
+ [Installieren von SQL Server 2016 R Server (eigenständig)](install/sql-r-standalone-windows-install.md)
+ [Eingabeaufforderung-setup](install/sql-ml-component-commandline-install.md)
+ [Offlineeinrichtung (kein Internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Konfiguration

Die folgenden Artikel enthalten Informationen über die Standardwerte sowie zum Anpassen der Konfiguration für den Machine learning in einer Instanz:

+ [Ändern des benutzerkontenpools für SQL Server R Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Konfigurieren und Verwalten von advanced Analytics-Erweiterungen](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Vorgehensweise: erstellen ein Ressourcenpools](r/how-to-create-a-resource-pool-for-r.md)
+ [Optimierung für R-arbeitsauslastungen](r/operationalizing-your-r-code.md)
