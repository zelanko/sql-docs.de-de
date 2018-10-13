---
title: Problembehandlung und häufig gestellte Fragen für Machine Learning in SQL Server | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dc04f74c4db5c05840795caea87efb9b0001171c
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48877923"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Problembehandlung bei Machine Learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Verwenden Sie diese Seite als Ausgangspunkt für die Arbeit über bekannte Probleme.

**Gilt für:** SQL Server 2016 R Services, SqlServer 2017 Machine Learning-Dienste (R- und Python)

## <a name="known-issues"></a>Bekannte Probleme

In den folgenden Artikeln werden bekannte Probleme mit der aktuellen und vorherigen Versionen beschrieben:

+ [Bekannte Probleme bei R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Versionsanmerkungen zu SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [SQL Server 2017 release notes (Versionsanmerkungen zu SQL Server 2017)](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Gewusst wie: Sammeln von Systeminformationen

Wenn Sie einen Fehler aufgetreten, oder, um ein Problem in Ihrer Umgebung zu verstehen müssen, ist es wichtig, dass Sie systematisch Informationen sammeln. Im folgende Artikel enthält eine Liste von Informationen, die zur Selbsthilfe zur Problembehandlung ermöglicht und eine Anforderung für den technischen Support.

+ [Die Datensammlung für die Problembehandlung von Machine learning](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Setup- und Konfigurationsleitfäden

Beginnen Sie hier, wenn Sie Machine Learning mit SQL Server nicht eingerichtet haben, oder wenn Sie die Funktion hinzufügen möchten:

+ [Installieren von SQL Server 2017-Machine Learning-Dienste (Datenbankintern)](install/sql-machine-learning-services-windows-install.md)
+ [Installieren von SQL Server 2017-Machine Learning Server (eigenständig)](install/sql-machine-learning-standalone-windows-install.md)
+ [Installieren von SQL Server 2016 R Services (Datenbankintern)](install/sql-r-services-windows-install.md)
+ [Installieren von SQL Server 2016 R Server (eigenständig)](install/sql-r-standalone-windows-install.md)
+ [Eingabeaufforderung-setup](install/sql-ml-component-commandline-install.md)
+ [Offlineeinrichtung (kein Internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Konfiguration

Die folgenden Artikel enthalten Informationen zu Standardeinstellungen und das Anpassen der Konfiguration für Machine learning in einer Instanz:

+ [Gleichzeitige Ausführung externer Skripts in SQL Server-Machine Learning-Dienste skalieren](administration/modify-user-account-pool.md)   
+ [Konfigurieren und Verwalten von advanced Analytics-Erweiterungen](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Gewusst wie: Erstellen eines Ressourcenpools](r/how-to-create-a-resource-pool-for-r.md)
+ [Optimierung für R-arbeitsauslastungen](r/operationalizing-your-r-code.md)
