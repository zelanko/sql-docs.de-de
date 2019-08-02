---
title: olapr R-Funktionsbibliothek
description: Einführung in die olapr-Funktionsbibliothek in SQL Server 2016 R Services und SQL Server Machine Learning Services mit R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 507bd04140880a3c15f1e72eed49c29ade56769c
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715007"
---
# <a name="olapr-r-library-in-sql-server"></a>olapr (R-Bibliothek in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**olapr** ist eine Microsoft-Bibliothek von R-Funktionen, die für MDX-Abfragen eines SQL Server Analysis Services OLAP-Cubes verwendet werden. Funktionen unterstützen nicht alle MDX-Vorgänge, Sie können jedoch Abfragen erstellen, die in Dimensionen Slice, Würfel, Drilldown, Rollup und Pivot sind. 

Dieses Paket ist nicht vorab in eine R-Sitzung geladen. Führen Sie den folgenden Befehl aus, um die Bibliothek zu laden.

```R
library(olapR)
```

Sie können diese Bibliothek für Verbindungen mit einem Analysis Services OLAP-Cube unter allen unterstützten Versionen von SQL Server verwenden. Verbindungen mit einem tabellarischen Modell werden zurzeit nicht unterstützt.

## <a name="package-version"></a>Paketversion

Die aktuelle Version ist 1.0.0 in allen reinen Windows-Produkten und-Downloads, die die Bibliothek bereitstellen.

## <a name="full-reference-documentation"></a>Vollständige Referenz Dokumentation

Die **olapr** -Bibliothek ist in mehreren Microsoft-Produkten verteilt, aber die Verwendung ist identisch, unabhängig davon, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die-Funktionen identisch sind, wird die [Dokumentation für einzelne sqlrutils-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) nur an einem Speicherort unter der [R-Referenz](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server veröffentlicht. Wenn produktspezifische Verhalten vorhanden sind, werden auf der Hilfeseite der Funktion Abweichungen festgestellt.

## <a name="availability-and-location"></a>Verfügbarkeit und Speicherort

Dieses Paket wird in den folgenden Produkten sowie auf mehreren Images virtueller Computer in Azure bereitgestellt. Der Speicherort des Pakets variiert entsprechend.

Produkt | Speicherort |
--------|----------|
SQL Server Machine Learning Services (mit R-Integration) | C:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R-Dienste | C:\Programme\Microsoft SQL server\mssql13. MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\programme\microsoft\r Client\R_SERVER\library |
Data Science Virtual Machine (in Azure) | C:\programme\microsoft\r Client\R_SERVER\library |
SQL Server virtueller Computer (in Azure) <sup>1</sup> | C:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> R-Integration ist in SQL Server optional. Die olapr-Bibliothek wird bei der VM-Konfiguration installiert, wenn Sie die Machine Learning-oder R-Funktion hinzufügen.


## <a name="see-also"></a>Siehe auch

[Erstellen von MDX-Abfragen mit olapr](how-to-create-mdx-queries-using-olapr.md)
