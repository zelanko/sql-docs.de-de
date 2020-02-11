---
title: Festlegen von Timeoutwerten für die Verarbeitung von Berichten und freigegebenen Datasets (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time-outs [Reporting Services]
- query time-outs [Reporting Services]
- report processing [Reporting Services], time-outs
- report execution time-outs [Reporting Services]
ms.assetid: 0f9dc61d-d03c-4bbf-8090-7a53844350f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fdbca5818e3430c0445444f3fb98b426e5f8a79c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66103212"
---
# <a name="setting-time-out-values-for-report-and-shared-dataset-processing-ssrs"></a>Festlegen von Timeoutwerten für die Verarbeitung von Berichten und freigegebenen Datasets (SSRS)
  Mithilfe von Timeoutwerten können Sie Grenzwerte für die Verwendung der Systemressourcen festlegen. Der Berichtsserver unterstützt die folgenden beiden Timeoutwerte:  
  
-   Ein Abfragetimeoutwert für ein eingebettetes Dataset gibt an, wie viele Sekunden der Berichtsserver auf eine Antwort von der Datenbank wartet. Dieser Wert wird in einem Bericht definiert.  
  
-   Ein Abfragetimeoutwert für ein freigegebenes Dataset gibt an, wie viele Sekunden der Berichtsserver auf eine Antwort von der Datenbank wartet. Dieser Wert ist Teil der Definition des freigegebenen Datasets und kann geändert werden, wenn Sie das freigegebene Dataset auf dem Berichtsserver verwalten.  
  
-   Ein Timeoutwert für die Berichtsausführung gibt an, wie viele Sekunden diese Berichtsverarbeitung maximal dauern darf, bevor sie beendet wird. Dieser Wert wird auf Systemebene definiert. Sie können diesen Wert für die jeweiligen Berichte anpassen.  
  
 Die meisten Timeoutfehler treten während der Abfrageverarbeitung auf. Verwenden Sie beim Auftreten von Timeoutfehlern einen höheren Abfragetimeoutwert. Stellen Sie sicher, dass Sie den Timeout Wert für die Berichts Ausführung so anpassen, dass er größer als der Abfrage Timeout Wert ist. Der Zeitraum muss ausreichen, um sowohl die Abfrage-als auch die Berichts Verarbeitung abzuschließen.  
  
## <a name="setting-a-query-time-out-for-an-embedded-dataset-in-a-report"></a>Festlegen eines Abfragetimeouts für ein eingebettetes Dataset in einem Bericht  
 Abfragetimeoutwerte werden im Rahmen der Erstellung eines Berichts beim Definieren eines eingebetteten Datasets angegeben. Der Timeoutwert wird zusammen mit dem Bericht im `Timeout`-Element der Berichtsdefinition gespeichert. Standardmäßig ist dieser Wert auf 30 Sekunden festgelegt. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
 Benutzer mit der Berechtigung zum Ändern der Eigenschaften eines veröffentlichten Berichts können diesen Wert zurücksetzen, indem sie die Definitionsdatei des Berichts bearbeiten.  
  
 Einen Abfragetimeoutwert können Sie auch für datengesteuerte Abonnements angeben. Der Wert für das Abfragetimeout wird auf den Seiten für die datengesteuerten Abonnements festgelegt. Der angegebene Wert bestimmt, wie lange der Berichtsserver beim Abrufen von Daten aus der Abonnentendatenquelle auf den Abschluss der Abfrageverarbeitung wartet.  
  
## <a name="setting-a-query-time-out-for-a-shared-dataset"></a>Festlegen eines Abfragetimeouts für einen freigegebenes Dataset  
 Abfragetimeoutwerte werden auf dem Berichtsserver in Sekunden angegeben, wenn Sie ein freigegebenes Dataset erstellen oder verwalten. Standardmäßig wird dieser Wert auf 0 Sekunden festgelegt, was bedeutet, dass kein Timeoutwert vorhanden ist. Weitere Informationen finden Sie unter [Verwalten von freigegebenen Datasets](../report-data/manage-shared-datasets.md).  
  
## <a name="setting-a-report-execution-time-out"></a>Festlegen eines Timeoutwerts für die Berichtsausführung  
 Sie können einen Timeoutwert für die Berichtsausführung festlegen, um die Verarbeitungszeit des Berichtsservers für einen Bericht zu begrenzen. Timeoutwerte für die Berichtsausführung können im Berichts-Manager angegeben werden. Sie können auf der Seite Siteeinstellungen für alle Berichte einen Standardwert festlegen und diesen Wert später auf der Eigenschaftenseite Ausführung für einen speziellen Bericht überschreiben. Standardmäßig ist der Wert auf 1800 Sekunden festgelegt. Weitere Informationen finden Sie unter [Festlegen von Berichtsverarbeitungseigenschaften](set-report-processing-properties.md).  
  
## <a name="how-report-execution-time-out-values-are-evaluated"></a>Auswerten von Timeoutwerten für die Berichtsausführung  
 Der Berichtsserver wertet Aufträge, die ausgeführt werden,  in Zeitabständen von 60 Sekunden aus. Alle 60  Sekunden vergleicht der Berichtsserver die tatsächliche Verarbeitungszeit mit dem Timeoutwert für die Berichtsausführung. Falls die Verarbeitungszeit für einen Bericht den Timeoutwert für die Berichtsausführung übersteigt, wird die Berichtsverarbeitung angehalten.  
  
 Beachten Sie Folgendes: Wenn ein Timeoutwert unter 60 Sekunden angegeben wird, kann der Bericht vollständig ausgeführt werden, falls die Verarbeitung während der Ruhezeit des Zyklus beginnt und endet, in der der Berichtsserver die ausgeführten Aufträge nicht auswertet. Wenn Sie z. B. einen Timeoutwert von 10 Sekunden für einen Bericht festlegen, dessen Ausführung 20 Sekunden dauert, wird der Bericht vollständig verarbeitet, falls die Berichtsausführung früh im 60 Sekunden-Zyklus beginnt.  
  
> [!NOTE]  
>  Sie können die Einstellung `RunningRequestsDbCycle` in der Datei RSReportServer.config festlegen, um die Häufigkeit zu ändern, mit der Aufträge, die ausgeführt werden, ausgewertet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Verarbeitungsoptionen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)   
 [Reporting Services Berichts Server &#40;einheitlicher Modus&#41;](reporting-services-report-server-native-mode.md)   
 [Verwalten eines ausgeführten Prozesses](../subscriptions/manage-a-running-process.md)   
 [Berichts-Manager (einheitlicher SSRS-Modus)](../report-manager-ssrs-native-mode.md)  
  
  
