---
title: Remote Tabellen Kopien
description: In diesem Thema wird beschrieben, wie Sie parallele Data Warehouse für die Verwendung der Funktion zum Kopieren von Remote Tabellen zum Kopieren von Tabellen in SMP SQL Server Datenbanken auf nicht-Appliance-Servern
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6c9a0a29b543eb287c7e233d6b1ea77bb2a0d45c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401264"
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>Parallele Data Warehouse für Remote Tabellen Kopien konfigurieren
Hier wird beschrieben, wie Sie SQL Server PDW für die Verwendung der Funktion zum Kopieren von Remote Tabellen zum Kopieren von Tabellen in SMP-SQL Server Datenbanken auf nicht-Appliance-Servern konfigurieren  
  
In diesem Thema wird einer der Konfigurationsschritte zum Konfigurieren der Remote Tabellen Kopie beschrieben. Eine Liste aller Konfigurationsschritte finden Sie unter Kopieren von [Remote Tabellen](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Vorbereitungen  
Um SQL Server PDW für die Verwendung der Remote Tabellen Kopie zu konfigurieren, müssen Sie folgende Schritte ausführen:  
  
-   Sie müssen über ein Analytics Platform System-Administrator Konto verfügen, das sich direkt bei den Knoten " <strong> *appliance_domain*-ad01</strong> " und " <strong> *appliance_domain*-ad02</strong> " anmelden kann.  
  
-   Beachten Sie den Hostnamen oder den IP-Namen des Zielservers.  
  
## <a name="HowToPDW"></a>Konfigurieren von SQL Server PDW für die Remote Tabellen Kopie: Aktualisieren von Hostnamen in DNS  
Die **Create Remote Table** -Anweisung, die für Remote Tabellen Kopien verwendet wird, gibt den Zielserver entweder mit der IP-Adresse oder dem IP-Namen des SMP-Windows-Systems an. Wenn Sie den IP-Namen verwenden möchten, müssen Sie dem DNS-Server Einträge für die erfolgreiche Namensauflösung hinzufügen.  
  
In den folgenden Schritten wird das Aktualisieren des DNS-Servers erläutert.  
  
1.  Melden Sie sich beim aktiven AD-Knoten an (normalerweise <strong> *appliance_domain*-ad01</strong>).  
  
2.  Öffnen Sie den DNS-Manager. Diese befindet sich im **Startmenü** unter " **Verwaltung** ".  
  
3.  Verwenden Sie den DNS-Manager, um den IP-Namen hinzuzufügen.  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Verwenden einer DNS-Weiterleitung zum Auflösen von DNS-Namen, die keine Appliance sind](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
