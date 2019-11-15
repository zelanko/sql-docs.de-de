---
title: olapR-Funktionsbibliothek für R
description: Einführung in die olapR-Funktionsbibliothek in SQL Server 2016 R Services und SQL Server Machine Learning Services mit R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 507bd04140880a3c15f1e72eed49c29ade56769c
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715007"
---
# <a name="olapr-r-library-in-sql-server"></a>olapR (R-Bibliothek in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**olapR** ist eine Microsoft-Bibliothek mit R-Funktionen, die für MDX-Abfragen eines SQL Server Analysis Services-OLAP-Cube verwendet werden können. Die Funktionen unterstützen nicht alle MDX-Vorgänge, aber Sie können Abfragen erstellen, die Slice, Dice, Drilldown, Rollup und Pivot in Dimensionen erstellen. 

Dieses Paket ist nicht vorab in eine R-Sitzung geladen. Führen Sie zum Laden der Bibliothek den folgenden Befehl aus.

```R
library(olapR)
```

Sie können diese Bibliothek für Verbindungen mit einem Analysis Services-OLAP-Cube auf allen unterstützten Versionen von SQL Server verwenden. Verbindungen mit einem tabellarischen Modell werden zurzeit nicht unterstützt.

## <a name="package-version"></a>Paketversion

Die aktuelle Version ist 1.0.0 in allen ausschließlich Windows-basierten Produkten und -Downloads, die die Bibliothek bereitstellen.

## <a name="full-reference-documentation"></a>Vollständige Referenzdokumentation

Die **olapR**-Bibliothek wird in mehreren Microsoft-Produkten bereitgestellt. Die Verwendung ist jedoch immer identisch, unabhängig davon, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt abrufen. Aus diesem Grund wird die [Dokumentation für einzelne sqlrutils-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) nur an einer Stelle in der [R-Referenz](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server veröffentlicht. Abweichungen durch produktspezifisches Verhalten finden Sie ggf. auf der Hilfeseite der Funktion.

## <a name="availability-and-location"></a>Verfügbarkeit und Speicherort

Dieses Paket wird in den folgenden Produkten sowie in mehreren VM-Images in Azure bereitgestellt. Der Speicherort des Pakets variiert entsprechend.

Product | Speicherort |
--------|----------|
SQL Server Machine Learning Services (mit R-Integration) | C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R-Server) | C:\Programme\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Programme\Microsoft\R Client\R_SERVER\library |
Data Science Virtual Machine (in Azure) | C:\Programme\Microsoft\R Client\R_SERVER\library |
Data Science Virtual Machine (in Azure) <sup>1</sup> | C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> R-Integration ist in SQL Server optional. Die olapR-Bibliothek wird installiert, wenn Sie während der VM-Konfiguration die Machine Learning- oder R-Funktion hinzufügen.


## <a name="see-also"></a>Siehe auch

[Erstellen von MDX-Abfragen mit olapR](how-to-create-mdx-queries-using-olapr.md)
