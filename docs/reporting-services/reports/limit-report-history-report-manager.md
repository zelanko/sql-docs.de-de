---
title: Einschränken des Berichtsverlaufs – Reporting Services | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie den Berichtsverlauf für einen Berichtsserver konfigurieren. Außerdem erfahren Sie, wie Sie den Berichtsverlauf für einen bestimmten Bericht konfigurieren.
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d01a008e00d2effccb109555799bbe6d55baf1e3
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466571"
---
# <a name="limit-report-history---reporting-services"></a>Einschränken des Berichtsverlaufs – Reporting Services
  Der Berichtsverlauf stellt eine Auflistung von Berichtsmomentaufnahmen dar, die Sie im Laufe der Zeit erstellen. Sie können den Berichtsverlauf nach Bedarf erstellen oder aber anhand eines Zeitplans festlegen, wie oft eine Momentaufnahme erstellt und dem Berichtsverlauf hinzugefügt wird.  
  
 Der Berichtsverlauf wird in der Berichtsserverdatenbank gespeichert. Wenn Berichtsmomentaufnahmen eine große Datenmenge enthalten, können Sie den Berichtsverlauf einschränken, um die Auswirkungen der Beibehaltung der Momentaufnahmen auf die Datenbankgröße zu minimieren.  

::: moniker range="=sql-server-2016"
  
## <a name="to-configure-report-history-for-a-report-server"></a>So konfigurieren Sie den Berichtsverlauf für einen Berichtsserver  
  
1.  Klicken Sie im Berichts-Manager auf der globalen Symbolleiste auf **Siteeinstellungen** .  
  
2.  Wählen Sie **Beliebig viele Momentaufnahmen im Berichtsverlauf speichern** aus, wenn Sie alle Berichtsverläufe unbegrenzt lange aufbewahren möchten. Wählen Sie andernfalls **Max. Anzahl von Kopien des Berichtsverlaufs** aus, um die maximale Anzahl von Momentaufnahmen anzugeben, die für einen bestimmten Bericht aufbewahrt werden können.  
  
3.  Klicken Sie auf **Anwenden**.  
  
## <a name="to-configure-report-history-for-a-specific-report"></a>So konfigurieren Sie den Berichtsverlauf für einen bestimmten Bericht  
  
1.  Navigieren Sie im Berichts-Manager zu dem Bericht, dessen Verlauf Sie konfigurieren möchten, und öffnen Sie ihn, indem Sie auf ihn klicken.  
  
2.  Klicken Sie auf die Registerkarte **Eigenschaften**.  
  
3.  Klicken Sie auf die Registerkarte **Verlauf** .  
  
4.  Wählen Sie die Optionen für Ihren Bericht aus, und klicken Sie auf **Anwenden**. Weitere Informationen zu den einzelnen Optionen finden Sie unter [Momentaufnahmeoptionen Eigenschaftenseite (Berichts-Manager)](/previous-versions/sql/sql-server-2016/ms189952(v=sql.130)).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen einer Momentaufnahme zum Berichtsverlauf &#40;Berichts-Manager&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Berichts-Manager (einheitlicher SSRS-Modus)](../web-portal-ssrs-native-mode.md)  

::: moniker-end

::: moniker range=">=sql-server-2017"

## <a name="to-configure-report-history-for-a-report-server"></a>So konfigurieren Sie den Berichtsverlauf für einen Berichtsserver  
  
1.  Klicken Sie im Webportal auf der globalen Symbolleiste auf **Siteeinstellungen**.  
  
2.  Wählen Sie **Beliebig viele Momentaufnahmen im Berichtsverlauf speichern** aus, wenn Sie alle Berichtsverläufe unbegrenzt lange aufbewahren möchten. Wählen Sie andernfalls **Max. Anzahl von Kopien des Berichtsverlaufs** aus, um die maximale Anzahl von Momentaufnahmen anzugeben, die für einen bestimmten Bericht aufbewahrt werden können.  
  
3.  Klicken Sie auf **Anwenden**.  
  
## <a name="to-configure-report-history-for-a-specific-report"></a>So konfigurieren Sie den Berichtsverlauf für einen bestimmten Bericht  
  
1.  Navigieren Sie im Webportal zu dem Bericht, dessen Verlauf Sie konfigurieren möchten, und öffnen Sie ihn, indem Sie auf diesen klicken.  
  
2.  Klicken Sie auf die Registerkarte **Eigenschaften**.  
  
3.  Klicken Sie auf die Registerkarte **Verlauf** .  
  
4.  Wählen Sie die Optionen für Ihren Bericht aus, und klicken Sie auf **Anwenden**. Weitere Informationen zu den einzelnen Optionen finden Sie unter [Snapshot Options Properties Page (Momentaufnahmeoptionen (Eigenschaftenseite))](/previous-versions/sql/sql-server-2016/ms189952(v=sql.130)).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Add a Snapshot to Report History (Hinzufügen einer Momentaufnahme zum Berichtsverlauf)](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   

::: moniker-end
