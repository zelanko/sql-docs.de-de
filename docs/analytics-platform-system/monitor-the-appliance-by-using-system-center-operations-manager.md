---
title: Verwenden von System Center Operations Manager zum Überwachen von APS
description: Verwenden Sie System Center Operations Manager (SCOM), um das Analytics Platform System (APS)-Gerät zu überwachen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 539c18efe43afcf5436c6913c20cab081974b7f5
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86941122"
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>Überwachen mit System Center Operations Manager Analytics Platform System
Verwenden Sie System Center Operations Manager (SCOM), um das Analytics Platform System (APS)-Gerät zu überwachen.
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Voraussetzungen  
  
1.  System Center Operations Manager 2007 R2, 2012 oder 2012 SP1 muss installiert sein und ausgeführt werden.  
  
2.  SQL Server 2008 R2 Native Client oder SQL Server 2012 Native Client muss installiert sein.  
  
3.  Die Management Packs zum Überwachen von SQL Server PDW müssen installiert, importiert und konfiguriert werden. In den folgenden Artikeln finden Sie Anweisungen zum Ausführen dieser Aufgaben.  
  
    -   [Installieren Sie die SCOM-Management Packs &#40;Analytics Platform System&#41;](install-the-scom-management-packs.md)  
  
    -   [Importieren Sie das SCOM-Management Pack für PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Konfigurieren von SCOM zum Überwachen von Analytics Platform System &#40;Analytics Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>So überwachen Sie SQL Server PDW mit SCOM  
Klicken Sie nach dem Konfigurieren der SCOM-Management Packs auf den Überwachungsbereich von SCOM, und führen Sie einen Drilldown zu **SQL Server Appliance** und dann **Microsoft SQL Server parallel Data Warehouse**aus. Unterhalb Microsoft SQL Server parallel Data Warehouse stehen vier Optionen zur Auswahl: Warnungen, Geräte, Geräte Diagramme und Knoten.  
  
### <a name="alerts"></a>Warnungen  
In den Warnungen finden Sie die aktuellen Warnungen, die Sie verwalten können.  
  
![Warnungen](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>Appliances  
In den Geräten finden Sie die derzeit ermittelten und überwachten SQL Server PDW Appliances in Ihrer Umgebung. Wenn ein Gerät hier nicht angezeigt wird und Sie die ODBC-Verbindung dafür erstellt haben, liegt möglicherweise ein Fehler in Ihrem pdwwatcher-Konto vor. Wenn Sie als "nicht überwacht" angezeigt werden, liegt möglicherweise ein Fehler in Ihrem pdwmonitor-Konto vor. Da SCOM keine Änderungen in Echtzeit vornimmt, prüft regelmäßig, ob neue Geräte überwacht werden müssen, und sendet regelmäßig Abfragen zur Überwachung an Appliances.  
  
![Gungs](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>Appliances-Diagramm  
Auf der Seite Appliances-Diagramm können Sie sich die Integrität Ihrer Appliance mit einer Strukturansicht ansehen:  
  
![Anwendungsdiagramm](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>Nodes  
Zum Schluss können Sie in der Ansicht "Knoten" die Integrität Ihrer Appliance über jeden Knoten anzeigen:  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Grundlegendes zu Warnungen der Verwaltungskonsole &#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md)  
  
