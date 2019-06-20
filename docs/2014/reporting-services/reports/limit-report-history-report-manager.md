---
title: Einschränken des Berichtsverlaufs (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
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
manager: kfile
ms.openlocfilehash: fd493fae67e3aa47c5c53cd3ad12d018b0b72f70
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66102641"
---
# <a name="limit-report-history-report-manager"></a>Einschränken des Berichtsverlaufs (Berichts-Manager)
  Der Berichtsverlauf stellt eine Auflistung von Berichtsmomentaufnahmen dar, die Sie im Laufe der Zeit erstellen. Sie können den Berichtsverlauf nach Bedarf erstellen oder aber anhand eines Zeitplans festlegen, wie oft eine Momentaufnahme erstellt und dem Berichtsverlauf hinzugefügt wird.  
  
 Der Berichtsverlauf wird in der Berichtsserverdatenbank gespeichert. Wenn Berichtsmomentaufnahmen eine große Datenmenge enthalten, können Sie den Berichtsverlauf einschränken, um die Auswirkungen der Beibehaltung der Momentaufnahmen auf die Datenbankgröße zu minimieren.  
  
### <a name="to-configure-report-history-for-a-report-server"></a>So konfigurieren Sie den Berichtsverlauf für einen Berichtsserver  
  
1.  Klicken Sie im Berichts-Manager auf der globalen Symbolleiste auf **Siteeinstellungen** .  
  
2.  Wählen Sie **Beliebig viele Momentaufnahmen im Berichtsverlauf speichern** aus, wenn Sie alle Berichtsverläufe unbegrenzt lange aufbewahren möchten. Wählen Sie andernfalls **Max. Anzahl von Kopien des Berichtsverlaufs** aus, um die maximale Anzahl von Momentaufnahmen anzugeben, die für einen bestimmten Bericht aufbewahrt werden können.  
  
3.  Klicken Sie auf **Anwenden**.  
  
### <a name="to-configure-report-history-for-a-specific-report"></a>So konfigurieren Sie den Berichtsverlauf für einen bestimmten Bericht  
  
1.  Navigieren Sie im Berichts-Manager zu dem Bericht, dessen Verlauf Sie konfigurieren möchten, und öffnen Sie ihn, indem Sie auf ihn klicken.  
  
2.  Klicken Sie auf die Registerkarte **Eigenschaften** .  
  
3.  Klicken Sie auf die Registerkarte **Verlauf** .  
  
4.  Wählen Sie die Optionen für Ihren Bericht aus, und klicken Sie auf **Anwenden**. Weitere Informationen zu den einzelnen Optionen finden Sie unter [Momentaufnahmeoptionen Eigenschaftenseite (Berichts-Manager)](../snapshot-options-properties-page-report-manager.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen einer Momentaufnahme zum Berichtsverlauf &#40;Berichts-Manager&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Berichts-Manager (einheitlicher SSRS-Modus)](../report-manager-ssrs-native-mode.md)  
  
  
