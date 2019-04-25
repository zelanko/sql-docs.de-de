---
title: Überwachen mit SCOM - Analytics Platform System | Microsoft-Dokumentation
description: Verwenden Sie System Center Operations Manager (SCOM), um das Analytics Platform System (APS)-Gerät zu überwachen.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3c43734dbd7ef1a766f3f1258f97565ab82e175d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62639847"
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>Überwachung mit System Center Operationsmanager – Analytics Platform System
Verwenden Sie System Center Operations Manager (SCOM), um das Analytics Platform System (APS)-Gerät zu überwachen.
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
  
1.  System Center Operationsmanager 2007 R2, 2012 oder 2012 SP1 muss installiert und ausgeführt werden.  
  
2.  SQL Server 2008 R2 Native Client oder SQL Server 2012 Native Client muss installiert sein.  
  
3.  Die Management Packs zum Überwachen von SQL Server PDW müssen installiert, nicht importiert und konfiguriert werden. Verwenden Sie die folgenden Artikel Anweisungen zum Ausführen dieser Aufgaben.  
  
    -   [Die SCOM-Management Packs &#40;Analytics Platform System&#41;](install-the-scom-management-packs.md)  
  
    -   [Importieren des SCOM Management Packs für PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Konfiguration von SCOM zum Überwachen von Analytics-Plattformsystem &#40;Analytics Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>Zum Überwachen von SQLServer PDW mit SCOM  
Klicken Sie nach dem Konfigurieren der SCOM-Management Packs, klicken Sie auf die Überwachung im Bereich von SCOM, und zeigen **SQL Server-Appliance** und dann **Microsoft SQL Server Parallel Data Warehouse**. Unter Microsoft SQL Server Parallel Data Warehouse gibt es vier Möglichkeiten zur Auswahl: Warnungen, Geräte, Gerät-Diagramm und Knoten.  
  
### <a name="alerts"></a>Benachrichtigungen  
Warnungen sind, finden Sie auf die aktuelle Warnungen verwalten.  
  
![Alerts](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>Appliances  
Geräte sind, in dem Sie die aktuell ermittelte und überwachte SQL Server PDW-Geräte in Ihrer Umgebung finden. Wenn ein Gerät sich hier nicht angezeigt, und Sie die ODBC-Verbindung für sie erstellt haben, klicken Sie dann möglicherweise ein Problem mit Ihrem Konto von PDWWatcher. Wenn sie als "nicht überwacht" angezeigt, liegt möglicherweise ein Problem mit Ihrem Konto PDWMonitor. Seien Sie geduldig, da in SCOM werden keine Änderungen in Echtzeit vornehmen, aber überprüft in regelmäßigen Abständen auf neue Geräte überwachen und sendet in regelmäßigen Abständen Abfragen an die Geräte für die Überwachung.  
  
![Appliances](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>Anwendungsdiagramm  
Die Geräte-Diagrammseite ist, in dem Sie einen Blick auf die Integrität Ihres Geräts mit einer Strukturansicht finden:  
  
![Anwendungsdiagramm](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>Knoten  
Schließlich können mit die Ansicht Knoten Sie die Integrität Ihres Geräts über jeden Knoten finden Sie unter:  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>Siehe auch  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Grundlegendes zu Verwaltungskonsolenwarnungen &#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md)  
  
