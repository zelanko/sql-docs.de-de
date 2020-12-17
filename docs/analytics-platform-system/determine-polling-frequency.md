---
title: Bestimmen der Abrufhäufigkeit
description: In diesem Artikel wird erläutert, wie Sie die Abruf Häufigkeit für Warnungen der Analytics-Platt Form Systemgeräte ermitteln.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ee5c83fee1028b7e165db6dfb8015129c29e4eca
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97641477"
---
# <a name="determine-polling-frequency"></a>Festlegen der Abruf Häufigkeit
In diesem Artikel wird erläutert, wie Sie die Abruf Häufigkeit für Warnungen der Analytics-Platt Form Systemgeräte ermitteln.  
  
## <a name="to-determine-the-polling-frequency"></a>So bestimmen Sie die Abruf Häufigkeit  
Da PDW derzeit keine proaktiven Benachrichtigungen unterstützt, wenn Warnungen auftreten, muss die Überwachungslösung die Geräte-DLLs kontinuierlich Abfragen.  Intern fragt PDW die Komponenten in unterschiedlichen Intervallen ab:  
  
-   Cluster-60 Sekunden  
  
-   Takt-60 Sekunden  
  
-   Alle anderen Komponenten: 5 Minuten  
  
-   Leistungsindikatoren-drei Sekunden  
  
Ein häufiges Intervall zum Abfragen von Warnungen, das auch von System Center verwendet wird, ist **alle 15 Minuten**.  Natürlich können Sie mehr oder weniger häufig Abfragen, aber es wird nicht empfohlen, weniger als alle sechs Stunden abzufragen.  
  
Ein häufiger Abruf ist akzeptabel, aber das Abrufen von zu häufig kann die [sys.dm_pdw_nodes_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) DMV überladen.  Ein zu häufiges Abrufen kann es Benutzern erschweren, Probleme mit der Abfrageleistung zu diagnostizieren, wenn Sie sich schnell aus der Sicht auslagern.  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Geräteüberwachung &#40;Analytics-Platt Form System&#41;](appliance-monitoring.md)  
