---
title: Azure Arc-fähige Version von SQL Server – Versionshinweise
description: Aktuelle Versionshinweise
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 10/29/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3dcbc6b17d5abe87aabe923d70746d65595b9de6
ms.sourcegitcommit: dc3ea1696b8a4332934568439aed6cce4e9737eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93244652"
---
# <a name="release-notes---azure-arc-enabled-sql-server-preview"></a>Versionshinweise – Azure Arc-fähige Version von SQL Server (Vorschauversion)

> [!NOTE]
> Als Previewfunktion unterliegt die in diesem Artikel vorgestellte Technologie den [zusätzlichen Nutzungsbedingungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

## <a name="september-2020"></a>September 2020

Die Azure Arc-fähige Version von SQL Server ist nun als Public Preview verfügbar. Dank der Azure Arc-fähigen Version von SQL Server sind die Azure-Dienste auch für Instanzen verfügbar, die außerhalb von Azure im Rechenzentrum des Kunden, am Edge oder in einer Multicloudumgebung gehostet werden.

Weitere Informationen finden Sie unter [Übersicht über die Azure Arc-fähige Version von SQL Server](overview.md).

### <a name="known-issues"></a>Bekannte Probleme

Das Septemberrelease weist die folgenden Probleme auf:

* Das Blatt **Register Azure Arc enabled SQL Server** (Azure Arc-fähigen SQL-Server registrieren) unterstützt nicht das Konfigurieren benutzerdefinierter Tags. Zum Hinzufügen von benutzerdefinierten Tags müssen Sie nach der Registrierung die Ressource **SQL Server - Azure Arc** öffnen und die Tags auf der Seite **Übersicht** ändern.

* Das Herstellen einer Verbindung zwischen SQL Server-Instanzen und Azure Arc erfordert ein Konto, das über verschiedene Berechtigungen verfügt. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen](overview.md#required-permissions).

## <a name="october-2020"></a>Oktober 2020

Das Oktoberupdate umfasst die folgenden Verbesserungen:

* Das Blatt „Azure Arc-fähigen SQL-Server registrieren“ enthält jetzt die Registerkarte **Tags**. Die Tags sind im Registrierungsskript enthalten und werden in den Ressourcen unter **SQL Server - Azure Arc** angezeigt. Weitere Informationen finden Sie unter [Herstellen einer Verbindung zwischen Ihrer SQL Server-Instanz und Azure Arc](connect.md).

* Der Eintrag **Environment Health** (Umgebungsintegrität) unterstützt jetzt die Aktivierung der **SQL-Bewertung** über das Portal durch Bereitstellen einer *benutzerdefinierten Skripterweiterung* (CustomScriptExtension). Ausführliche Informationen finden Sie unter [Konfigurieren der SQL-Bewertung](assess.md#run-on-demand-sql-assessment).

### <a name="known-issues"></a>Bekannte Probleme

Das Oktoberrelease weist die folgenden Probleme auf:

* Das Herstellen einer Verbindung zwischen SQL Server-Instanzen und Azure Arc erfordert ein Konto, das über verschiedene Berechtigungen verfügt. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen](overview.md#required-permissions).

## <a name="next-steps"></a>Nächste Schritte

**Möchten Sie es selbst ausprobieren?**  Legen Sie los mit dem [Schnellstart für die Azure Arc-fähige Version von SQL Server](https://aka.ms/AzureArcSqlServerJumpstart).
