---
author: MikeRayMSFT
ms.prod: sql
ms.technology: big-data-cluster
ms.topic: include
ms.date: 06/22/2020
ms.author: mikeray
ms.openlocfilehash: b72f8044638adbf75049392fae32447a8a749a6d
ms.sourcegitcommit: d973b520f387b568edf1d637ae37d117e1d4ce32
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85215120"
---
Beginnend mit SQL Server 2019 CU5 verwenden alle Endpunkte einschließlich Gateway `AZDATA_USERNAME` und `AZDATA_PASSWORD`, wenn Sie einen neuen Cluster mit Standardauthentifizierung bereitstellen. Endpunkte auf Clustern, die ein Upgrade auf CU5 erhalten, verwenden weiterhin `root` als Benutzername für die Verbindung mit dem Gatewayendpunkt. Diese Änderung gilt nicht für Bereitstellungen, die die Active Directory-Authentifizierung verwenden. Weitere Informationen finden Sie unter [Anmeldeinformationen für den Zugriff auf Dienste über den Gatewayendpunkt](../big-data-cluster/release-notes-big-data-cluster.md#credentials-for-accessing-services-through-gateway-endpoint) in den Versionshinweisen.