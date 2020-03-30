---
title: Servereigenschaften (Ausführungsseite) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e8259591c54068cde134c98ae405dd77fac6fab4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "65571367"
---
# <a name="server-properties-execution-page"></a>Servereigenschaften (Seite Ausführung)
  Verwenden Sie diese Seite zum Festlegen eines Timeoutwertes für die Berichtsausführung. Dieser Wert gilt für alle Berichte, die von der aktuellen Berichtsserverinstanz verarbeitet werden. Sie können diesen Wert für einzelne Berichte überschreiben. Der von Ihnen angegebene Wert muss die gesamte Berichtsverarbeitung auf dem Berichtsserver berücksichtigen, plus der Abfrageverarbeitung, die auf dem Datenbankserver durchgeführt wird, wenn der Berichtsserver die im Bericht verwendeten Daten abruft.  
  
 Öffnen Sie diese Seite, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten und eine Verbindung mit einer Berichtsserverinstanz herstellen. Klicken Sie mit der rechten Maustaste auf den Namen des Berichtsservers, und wählen Sie anschließend **Eigenschaften**aus. Klicken Sie auf **Ausführung** , um diese Seite zu öffnen.  
  
## <a name="options"></a>Tastatur  
 **Kein Timeout für eine Berichtsausführung**  
 Stellt einem Berichtsserver eine uneingeschränkte Zeitspanne für die Berichtsverarbeitung zur Verfügung.  
  
 **Berichtsausführung auf die folgende Anzahl von Sekunden beschränken**  
 Legt eine Zeitbeschränkung für die Berichtsausführung fest. Diese Zeitspanne beginnt, wenn der Bericht angefordert wird. Wenn diese Zeitspanne endet, bevor der Bericht vollständig verarbeitet wurde, bricht der Berichtsserver den Vorgang und alle in Bearbeitung befindlichen Abfragen externer Datenquellen ab.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Festlegen von Berichtsverarbeitungseigenschaften](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Festlegen von Timeoutwerten für die Verarbeitung von Berichten und freigegebenen Datasets (SSRS)](../../reporting-services/report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)  
  
  
