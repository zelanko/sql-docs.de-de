---
title: Herstellen einer Verbindung mit einer Datenquelle
description: Erfahren Sie mehr über Verbindungsobjekte, die zum Herstellen einer Verbindung mit Datenquellen in ADO.NET verwendet werden. Das von Ihnen gewählte „Connection“-Objekt hängt vom Typ der Datenquelle ab.
ms.date: 11/13/2020
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 0fdf91c5a4da33b585f10939cd6a801a46b236b3
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761518"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Herstellen einer Verbindung mit einer Datenquelle in ADO.NET

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Im Microsoft SqlClient-Datenanbieter stellen Sie mithilfe eines **Connection**-Objekts die Verbindung mit einer bestimmten Datenquelle her, indem Sie die erforderlichen Authentifizierungsinformationen in einer Verbindungszeichenfolge angeben. Das von Ihnen verwendete **Connection**-Objekt hängt vom Typ der Datenquelle ab.

Der Microsoft SqlClient-Datenanbieter für SQL Server enthält den Typ <xref:Microsoft.Data.SqlClient.SqlConnection>, der von einer <xref:System.Data.Common.DbConnection>-Klasse abgeleitet ist.

## <a name="in-this-section"></a>In diesem Abschnitt  

[Herstellen der Verbindung](establishing-connection.md)\
Beschreibt die Verwendung eines **Connection**-Objekts zum Herstellen einer Verbindung mit einer Datenquelle.

[Verbindungsereignisse](connection-events.md)\
Beschreibt die Verwendung eines **InfoMessage**-Ereignisses zum Abrufen von Informationsmeldungen von einer Datenquelle.

## <a name="see-also"></a>Siehe auch

- [Verbindungszeichenfolgen](connection-strings.md)
- [Verbindungspooling](connection-pooling.md)
- [Befehle und Parameter](commands-parameters.md)
- ["DataAdapters" und "DataReaders"](dataadapters-datareaders.md)
