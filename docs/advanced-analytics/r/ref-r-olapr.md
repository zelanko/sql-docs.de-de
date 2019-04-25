---
title: 'OlapR R - Funktionsbibliothek: SQL Server Machine Learning Services'
description: Einführung in die OlapR-Funktionsbibliothek in SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services mit R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e5419900b8ba573ec0658a5022be68105b0b8607
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641853"
---
# <a name="olapr-r-library-in-sql-server"></a>OlapR (R-Bibliothek in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**OlapR** ist eine Microsoft-Bibliothek von R-Funktionen, die für die MDX-Abfragen für einen SQL Server Analysis Services-OLAP-Cube verwendet. Vorgänge für alle MDX-Funktionen nicht unterstützt, aber Sie können Abfragen, die dem Slice, aufteilen, Drilldown, Rollup und Pivotieren von Dimensionen erstellen. 

Dieses Paket ist nicht in einer R-Sitzung geladen. Führen Sie den folgenden Befehl zum Laden der Bibliothek.

```R
library(olapR)
```

Sie können diese Bibliothek für Verbindungen mit einem Analysis Services-OLAP-Cube auf allen unterstützten Versionen von SQL Server verwenden. Verbindungen mit einem tabellarischen Modell werden zu diesem Zeitpunkt nicht unterstützt.

## <a name="package-version"></a>Paketversion

Aktuelle Version ist 1.0.0 in allen nur-Windows-Produkten und lädt Sie herunter, die Bibliothek bereitstellt.

## <a name="full-reference-documentation"></a>Vollständige Referenz-Dokumentation

Die **Olapr** Bibliothek wird in mehreren Microsoft-Produkte verteilt, aber wird, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die Funktionen identisch sind, [Dokumentation für einzelne Sqlrutils-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) in nur einem Ort unter veröffentlicht wird die [R Verweis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server. Sollten Sie jede Produkt-spezifische Verhalten vorhanden ist, wird Diskrepanzen auf der Hilfeseite für die Funktion angegeben.

## <a name="availability-and-location"></a>Verfügbarkeit und den Speicherort

Dieses Paket wird in der folgenden Produkte sowie auf mehrere VM-Images in Azure bereitgestellt. Speicherort des Pakets variiert entsprechend.

Produkt | Speicherort |
--------|----------|
SQL Server 2017 Machine Learning Services (mit R-Integration) | C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Programme\Microsoft Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\library |
Data Science-VM (in Azure) | C:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\library |
SQL Server-Computers (in Azure) <sup>1</sup> | C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> R-Integration ist in SQL Server optional. Wenn Sie die Machine Learning oder R-Funktion während der Konfiguration des virtuellen Computers hinzufügen, wird die OlapR-Bibliothek installiert werden.


## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Erstellen von MDX-Abfragen mit olapR](how-to-create-mdx-queries-using-olapr.md)
