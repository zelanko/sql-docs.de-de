---
title: Bestimmen der abrufhäufigkeit - Analytics Platform System | Microsoft-Dokumentation
description: In diesem Artikel erläutert das Abrufintervall für Analytics Platform System appliancewarnungen zu ermitteln.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: eec9e3e211c68b7f56fe6829a70064317b96e646
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63221989"
---
# <a name="determine-polling-frequency"></a>Bestimmen der Abrufhäufigkeit
In diesem Artikel erläutert das Abrufintervall für Analytics Platform System appliancewarnungen zu ermitteln.  
  
## <a name="to-determine-the-polling-frequency"></a>Bestimmen der Abrufhäufigkeit  
Da PDW derzeit proaktive Benachrichtigungen nicht unterstützt, wenn Warnungen auftreten, muss die Lösung für die Appliance DLLs fortlaufend abzurufen.  Intern fragt PDW die Komponenten in verschiedenen Intervallen ab:  
  
-   Cluster - 60 Sekunden  
  
-   Takt - 60 Sekunden  
  
-   Alle anderen Komponenten – fünf Minuten  
  
-   Leistungsindikatoren: drei Sekunden  
  
Ein bestimmtes Intervall für den Abruf von Warnungen, die auch von System Center verwendet wird, ist **alle 15 Minuten**.  Natürlich können Sie mehr oder weniger häufig Abfragen, aber es wird nicht empfohlen, weniger als alle sechs Stunden abrufen.  
  
Häufigeres ist akzeptabel, jedoch zu häufig Abfragen überlasten kann die [sys.dm_pdw_nodes_exec_requests](https://msdn.microsoft.com/library/ms177648(v=sql11).aspx) DMV.  Abruf zu häufig ist es schwer für Benutzer, um die abfrageleistung zu diagnostizieren Probleme bei deren schnell wird nicht aus der Sicht.  
  
## <a name="see-also"></a>Siehe auch  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Applianceüberwachung &#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
