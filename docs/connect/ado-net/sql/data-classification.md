---
title: Datenermittlung und -klassifizierung in SqlClient
description: In diesem Artikel wird erläutert, wie Sie überprüfen, ob eine SQL Server-Datenbank die Datenklassifizierung unterstützt. Außerdem erfahren Sie, wie Sie über das SqlDataReader-Objekt auf Datenklassifizierungsinformationen zugreifen.
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: b53e71c4c302145af14c1f2e37f30fe0e3c8f8e2
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725721"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>Datenermittlung und -klassifizierung in SqlClient

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Bei der [Datenermittlung und -klassifizierung](../../../relational-databases/security/sql-data-discovery-and-classification.md?view=sql-server-2017) handelt es sich um mehrere erweiterte Dienste für die Ermittlung, Klassifizierung, Bezeichnung und Berichterstellung für vertrauliche Daten in Ihren Datenbanken. SqlClient stellt eine API bereit, die schreibgeschützte Datenermittlungs- und Datenklassifizierungsinformationen verfügbar macht, wenn die zugrunde liegende Quelle das Feature unterstützt. Der Zugriff auf diese Informationen erfolgt über SqlDataReader.

Diese Beispielanwendung zeigt, wie auf die Datenklassifizierungseigenschaften von SqlDataReader zugegriffen wird.

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**Weitere Informationen**  

 [SQL Server-Features und ADO.NET](sql-server-features-adonet.md)