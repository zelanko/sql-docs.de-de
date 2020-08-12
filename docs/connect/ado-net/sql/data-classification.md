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
ms.openlocfilehash: 27b9c232fe785d3c016848f3bb952236b8e7cd75
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2020
ms.locfileid: "85110124"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>Datenermittlung und -klassifizierung in SqlClient

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Bei der [Datenermittlung und -klassifizierung](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-2017) handelt es sich um mehrere erweiterte Dienste für die Ermittlung, Klassifizierung, Bezeichnung und Berichterstellung für vertrauliche Daten in Ihren Datenbanken. SqlClient stellt eine API bereit, die schreibgeschützte Datenermittlungs- und Datenklassifizierungsinformationen verfügbar macht, wenn die zugrunde liegende Quelle das Feature unterstützt. Der Zugriff auf diese Informationen erfolgt über SqlDataReader.

Diese Beispielanwendung zeigt, wie auf die Datenklassifizierungseigenschaften von SqlDataReader zugegriffen wird.

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**Weitere Informationen**  

 [SQL Server-Features und ADO.NET](sql-server-features-adonet.md)   
