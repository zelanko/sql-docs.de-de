---
title: Multiple Active Result Sets (MARS)
description: In diesem Artikel wird beschrieben, wie mehrere SqlDataReader-Instanzen in einer Verbindung geöffnet werden, wenn jede einzelne SqlDataReader-Instanz von einem separaten Befehl gestartet wurde.
ms.date: 08/15/2019
ms.assetid: c90ef863-bac7-44cf-adc1-f05c36fcf57d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 4475e4b8a71b4abcf4e1c2324a49e03a8bb64fbb
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896670"
---
# <a name="multiple-active-result-sets-mars"></a>Multiple Active Result Sets (MARS)

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

MARS (mehrere aktive Resultsets) ist ein Feature, mit dem mehrere Batches über eine Verbindung ausgeführt werden können. In früheren Versionen konnte nur ein Batch für eine einzelne Verbindung ausgeführt werden. Wenn mehrere Batches mit MARS ausgeführt werden, impliziert das nicht die gleichzeitige Ausführung von Vorgängen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Aktivieren mehrerer aktiver Resultsets](enable-multiple-active-result-sets.md)  
Enthält eine Erläuterung zum Verwenden von MARS mit SQL Server.  
  
[Bearbeiten von Daten](manipulate-data.md)  
Stellt Beispiele zum Programmieren von MARS-Anwendungen bereit  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
[Asynchrone Vorgänge](asynchronous-operations.md)  
Bietet ausführliche Informationen zur Verwendung der neuen asynchronen Features in .NET  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
