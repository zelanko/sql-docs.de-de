---
title: Partitionen und DirectQuery-Modus (SSAS – tabellarisch) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f179ba9-6efb-46ae-90e5-945bbfddb719
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6153a5975dd342bfabb00b7f964ee04d6941a363
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150434"
---
# <a name="partitions-and-directquery-mode-ssas-tabular"></a>Partitionen und DirectQuery-Modus (SSAS – tabellarisch)
  In diesem Abschnitt wird erläutert, wie Partitionen in DirectQuery-Modellen verwendet werden. Allgemeinere Informationen zu Partitionen in Tabellenmodellen finden Sie unter [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).  
  
 Anleitungen zum Ändern der Partition, die verwendet wird oder Anzeigen von Informationen zur Partition finden Sie unter [Ändern der DirectQuery-Partition &#40;SSAS – tabellarisch&#41;](../change-the-directquery-partition-ssas-tabular.md).  
  
## <a name="using-partitions-in-directquery-mode"></a>Verwenden von Partitionen im DirectQuery-Modus  
 Für jede Tabelle müssen Sie eine einzelne Partition angeben, die als DirectQuery-Datenquelle verwendet werden soll.  Wenn mehrere Partitionen vorhanden sind, wenn Sie das Modell wechseln, um den DirectQuery-Modus zu aktivieren, wird die erste Partition, die in der Tabelle erstellt wurde, standardmäßig als DirectQuery-Partition gekennzeichnet. Dies kann später mit dem Partitions-Manager in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]geändert werden.  
  
 Warum soll im DirectQuery-Modus nur eine einzelne Partition zulässig sein?  
  
 In Tabellenmodellen werden (ebenso wie in OLAP-Modellen) die Partitionen einer Tabelle von SQL-Abfragen definiert. Der Entwickler, der die Partitionsdefinition erstellt, muss gewährleisten, dass sich Partitionen nicht überschneiden. Über Analysis Services wird nicht überprüft, ob Datensätze zu einer oder mehreren Partitionen gehören.  
  
 Partitionen in einem zwischengespeicherten Tabellenmodell verhalten sich ebenso. Wenn Sie ein Modell im Arbeitsspeicher verwenden, während auf den Cache zugegriffen wird, werden DAX-Formeln für jede Partition ausgewertet, und die Ergebnisse werden kombiniert. Wenn jedoch bei einem Tabellenmodell der DirectQuery-Modus verwendet wird, ist es nicht möglich, mehrere Partitionen auszuwerten, die Ergebnisse zu kombinieren und sie zum Senden an den relationalen Datenspeicher in eine SQL-Anweisung zu konvertieren. Dies könnte zu einem nicht akzeptablen Leistungsverlust sowie zu möglichen Ungenauigkeiten führen, wenn die Ergebnisse aggregiert werden.  
  
 Aus diesem Grund verwendet der Server für im DirectQuery-Modus beantwortete Abfragen eine einzelne Partition, die als primäre Partition für DirectQuery-Zugriff markiert wurde und als *DirectQuery-Partition*bezeichnet wird.  Die in der Definition dieser Partition angegebene SQL-Abfrage definiert den vollständigen Satz der Daten, die zur Beantwortung von Abfragen im DirectQuery-Modus verwendet werden können.  
  
 Wenn Sie eine Partition nicht explizit definieren, gibt die Engine lediglich eine SQL-Abfrage an die gesamte relationale Datenquelle aus, führt alle satzbasierten Vorgänge aus, die gemäß DAX-Formel vorgeschrieben sind, und gibt die Abfrageergebnisse zurück.  
  
 Wenn Sie mehrere Partitionen in einer Tabelle haben und Sie eine Partition als DirectQuery-Partition auswählen, werden alle anderen Partitionen standardmäßig als nur für arbeitsspeicherinterne Verwendung vorgesehen markiert.  
  
## <a name="partitions-in-cached-models-and-in-directquery-models"></a>Partitionen in zwischengespeicherten Modellen und DirectQuery-Modellen  
 Wenn Sie eine DirectQuery-Partition konfigurieren, müssen Sie Verarbeitungsoptionen für die Partition angeben.  
  
 Zwei Verarbeitungsoptionen stehen für die DirectQuery-Partition zur Verfügung. Um diese Eigenschaft festzulegen, verwenden Sie den **Partitions-Manager** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], und wählen Sie die Eigenschaft **Verarbeitungsoption** aus. In der folgenden Tabelle sind die Werte dieser Eigenschaft aufgeführt. Außerdem sind die Effekte jedes einzelnen Werts für den Fall beschrieben, dass ein Wert mit der DirectQueryUsage-Eigenschaft zur Verbindungszeichenfolge kombiniert wird:  
  
|**DirectQueryUsage** Eigenschaft|Eigenschaft**Verarbeitungsoption** |Hinweise|  
|-----------------------------------|------------------------------------|-----------|  
|DirectQuery|Kein Verarbeiten dieser Partition|Wenn das Modell ausschließlich DirectQuery verwendet, ist eine Verarbeitung niemals notwendig.<br /><br /> In Hybridmodellen können Sie die DirectQuery-Partition so konfigurieren, dass sie niemals verarbeitet wird. Beispiel: Wenn Sie ein sehr großes Dataset verwenden und dem Cache nicht die vollständigen Ergebnisse hinzufügen möchten, können Sie angeben, dass die DirectQuery-Partition die Vereinigung der Ergebnisse für alle anderen Partitionen in der Tabelle enthalten und dass niemals eine Verarbeitung stattfinden soll. Abfragen, die an die relationale Quelle gerichtet werden, sind nicht betroffen, und in Abfragen für zwischengespeicherte Daten werden Daten aus den anderen Partitionen kombiniert.|  
|InMemory mit DirectQuery|Verarbeitung von Partitionen zulassen|Wenn beim Modell der hybride Modus verwendet wird, sollten Sie für Abfragen für die speicherinterne Datenquelle und für Abfragen für die DirectQuery-Datenquelle die gleiche Partition verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;SSAS – tabellarisch&#41;](partitions-ssas-tabular.md)  
  
  