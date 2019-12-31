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
ms.openlocfilehash: 005fe3d14a7314f7339157064b248a81044a1dfb
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401217"
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
  
Das Abrufen häufiger Abfragen ist akzeptabel, aber das Abrufen von zu häufig kann die [sys. dm_pdw_nodes_exec_requests](https://msdn.microsoft.com/library/ms177648(v=sql11).aspx) -DMV überladen.  Ein zu häufiges Abrufen kann es Benutzern erschweren, Probleme mit der Abfrageleistung zu diagnostizieren, wenn Sie sich schnell aus der Sicht auslagern.  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Geräteüberwachung &#40;Analytics-Platt Form System&#41;](appliance-monitoring.md)  
  
