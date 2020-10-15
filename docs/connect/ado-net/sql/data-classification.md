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
ms.openlocfilehash: 6d82bfd3c49576a35b24f5a04cdc2c03dceeb766
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92081499"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>Datenermittlung und -klassifizierung in SqlClient

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Bei der [Datenermittlung und -klassifizierung](../../../relational-databases/security/sql-data-discovery-and-classification.md) handelt es sich um mehrere erweiterte Dienste für die Ermittlung, Klassifizierung, Bezeichnung und Berichterstellung für vertrauliche Daten in Ihren Datenbanken. SqlClient stellt eine API bereit, die schreibgeschützte Datenermittlungs- und Datenklassifizierungsinformationen verfügbar macht, wenn die zugrunde liegende Quelle das Feature unterstützt. Der Zugriff auf diese Informationen erfolgt über SqlDataReader.

Diese Beispielanwendung zeigt, wie auf die Datenklassifizierungseigenschaften von SqlDataReader zugegriffen wird.

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**Weitere Informationen**  

 [SQL Server-Features und ADO.NET](sql-server-features-adonet.md)