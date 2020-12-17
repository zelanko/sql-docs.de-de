---
title: R-Paket „olapR“
description: „olapR“ ist ein R-Paket von Microsoft, das für MDX-Abfragen eines SQL Server Analysis Services-OLAP-Cube verwendet wird. Die Funktionen unterstützen nicht alle MDX-Vorgänge, aber Sie können Abfragen erstellen, die Slice, Dice, Drilldown, Rollup und Pivot in Dimensionen erstellen. Das Paket ist in SQL Server Machine Learning Services und SQL Server 2016 R Services enthalten.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: fc9c222bfb1229deea7ef734658b1d3b6b86149d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470801"
---
# <a name="olapr-r-package-in-sql-server-machine-learning-services"></a>„olapR“ (R-Paket in SQL Server Machine Learning Services)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

**olapR** ist ein R-Paket von Microsoft, das für MDX-Abfragen eines SQL Server Analysis Services-OLAP-Cube verwendet wird. Die Funktionen unterstützen nicht alle MDX-Vorgänge, aber Sie können Abfragen erstellen, die Slice, Dice, Drilldown, Rollup und Pivot in Dimensionen erstellen. Das Paket ist in [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) und [SQL Server 2016 R Services](sql-server-r-services.md) enthalten.

Sie können dieses Paket in allen unterstützten Versionen von SQL Server für Verbindungen mit einem Analysis Services-OLAP-Cube verwenden. Verbindungen mit einem tabellarischen Modell werden zurzeit nicht unterstützt.

## <a name="load-package"></a>Laden des Pakets

Das Paket **olapR** wird nicht vorab in eine R-Sitzung geladen. Führen Sie den folgenden Befehl aus, um das Paket zu laden.

```R
library(olapR)
```

## <a name="package-version"></a>Paketversion

1\.0.0 ist die aktuelle Version, die in allen ausschließlich Windows-basierten Produkten und -Downloads enthalten ist, die das Paket bereitstellen.

## <a name="full-reference-documentation"></a>Vollständige Referenzdokumentation

Das Paket **olapR** ist im Lieferumfang von mehreren Microsoft-Produkten enthalten. Die Verwendung ist jedoch immer gleich, unabhängig davon, ob Sie das Paket in SQL Server oder einem anderen Produkt erworben haben. Aus diesem Grund wird die [Dokumentation für einzelne sqlrutils-Funktionen](/machine-learning-server/r-reference/olapr/olapr) nur an einer Stelle in der [R-Referenz](/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server veröffentlicht. Abweichungen durch produktspezifisches Verhalten finden Sie ggf. auf der Hilfeseite der Funktion.

## <a name="availability-and-location"></a>Verfügbarkeit und Speicherort

Dieses Paket wird in den folgenden Produkten sowie in mehreren VM-Images in Azure bereitgestellt. Der Speicherort des Pakets variiert entsprechend.

Produkt | Standort |
--------|----------|
SQL Server Machine Learning Services (mit R-Integration) | C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R-Server) | C:\Programme\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Programme\Microsoft\R Client\R_SERVER\library |
Data Science Virtual Machine (in Azure) | C:\Programme\Microsoft\R Client\R_SERVER\library |
Data Science Virtual Machine (in Azure) <sup>1</sup> | C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> R-Integration ist in SQL Server optional. Das Paket „olapR“ wird installiert, wenn Sie während der VM-Konfiguration das Machine Learning- oder das R-Feature hinzufügen.


## <a name="see-also"></a>Weitere Informationen

[Erstellen von MDX-Abfragen mit olapR](how-to-create-mdx-queries-using-olapr.md)