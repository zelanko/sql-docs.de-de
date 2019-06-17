---
title: Drillthroughberichte (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 938a6450-67c1-4eef-80b4-8fdaefeed584
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 63119bf6d8ba4e9d907b9c6cdfb6bfe0b7765941
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66105943"
---
# <a name="drillthrough-reports-report-builder-and-ssrs"></a>Drillthroughberichte (Berichts-Generator und SSRS)
  Ein Drillthroughbericht ist ein Bericht, der geöffnet werden kann, indem der Benutzer auf einen Link in einem anderen Bericht klickt. Drillthroughberichte enthalten in der Regel Details zu einem Element im ursprünglichen Zusammenfassungsbericht. In dieser Abbildung enthält der Verkaufszusammenfassungsbericht z. B. Verkaufsaufträge und Gesamtbeträge. Wenn ein Benutzer auf eine Auftragsnummer in der Zusammenfassungsliste klickt, wird ein weiterer Bericht mit Details zu der Bestellung geöffnet.  
  
 ![Rs_DrillThru](../media/rs-drillthru.gif "Rs_DrillThru")  
  
 Die Daten im Drillthroughbericht werden erst abgerufen, wenn der Benutzer im Hauptbericht auf den Link zum Öffnen des Drillthroughberichts klickt. Wenn die Daten für den Drillthroughbericht zur gleichen Zeit abgerufen werden sollen wie die Daten für den Hauptbericht, können Sie einen Unterbericht verwenden. Weitere Informationen finden Sie unter [Unterberichte (Berichts-Generator und SSRS)](subreports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Wenn Sie in Berichts-Generator arbeiten, müssen Sie mit einem Berichtsserver verbunden sein, um den Drillthroughbericht anzuzeigen, der über den Drillthroughlink im Hauptbericht geöffnet wird.  
  
 Kurze Anweisungen zu Drillthroughberichten finden Sie unter [Tutorial: Erstellen von Drillthrough- und Hauptberichten &#40;Berichts-Generator&#41;](../tutorial-creating-drillthrough-and-main-reports-report-builder.md) Drillthroughbericht ist auch in zwei Business Intelligence-Lösungen, wichtige [BI-Berichterstellung: Berichts- und Abonnementszenario](https://technet.microsoft.com/bi/ff769487.aspx) und [Unternehmensdashboards: Vertriebs-Lösung](https://technet.microsoft.com/bi/ff643005.aspx)  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="parameters-in-drillthrough-reports"></a>Parameter in Drillthroughberichten  
 Üblicherweise enthält ein Drillthroughbericht Parameter, die durch den Zusammenfassungsbericht an ihn übergeben werden. Im Beispiel mit dem Sales-Bericht enthält der zusammenfassende Bericht in einem Textfeld einer Tabellenzelle das Feld [OrderNumber], also Bestellnummer. Der Drillthroughbericht enthält einen Parameter, der als Wert die Bestellnummer verwendet. Wenn Sie den Link zum Drillthroughbericht für das Textfeld für [OrderNumber] festlegen, legen Sie auch den Parameter für den Zielbericht auf [OrderNumber] fest. Wenn der Benutzer im Zusammenfassungsbericht auf eine Auftragsnummer klickt, wird der Zieldetailbericht mit den Informationen für die jeweilige Auftragsnummer angezeigt. Anleitungen zum Anpassen von Drillthroughberichten auf der Basis von Parameterwerten finden Sie unter [Berichtsparameter (Berichts-Generator und Berichts-Designer)](report-parameters-report-builder-and-report-designer.md) und [InScope-Funktion (Berichts-Generator und SSRS)](report-builder-functions-inscope-function.md).  
  
## <a name="designing-the-drillthrough-report"></a>Entwerfen des Drillthroughberichts  
 Zum Erstellen eines Drillthroughberichts müssen Sie den Bericht zuerst entwerfen, bevor Sie die Drillthroughaktion im Hauptbericht erstellen.  
  
 Ein Drillthroughbericht kann ein beliebiger Bericht sein. In der Regel akzeptiert der Drillthroughbericht basierend auf dem Link aus dem Hauptbericht einen oder mehrere Parameter zum Angeben der anzuzeigenden Daten. Wenn der Link aus dem Hauptbericht z. B. für einen Verkaufsauftrag definiert wurde, wird die Verkaufsauftragsnummer an den Drillthroughbericht übergeben.  
  
## <a name="creating-a-drillthrough-action-in-the-main-report"></a>Erstellen einer Drillthroughaktion im Hauptbericht  
 Drillthroughlinks können Textfeldern (einschließlich Text in den Zellen einer Tabelle oder Matrix), Bildern, Diagrammen, Messgeräten und beliebigen anderen Berichtselementen mit einer Eigenschaftenseite "Aktion" hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen einer Drillthroughaktion für einen Bericht (Berichts-Generator und SSRS)](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md).  
  
 Die Drillthroughaktion im Hauptbericht kann als Berichtsaktion oder als URL-Aktion erstellt werden. Im Fall einer Berichtsaktion muss sich der Drillthroughbericht auf dem gleichen Berichtsserver wie der Hauptbericht befinden. Bei einer URL-Aktion muss der Bericht unter der vollqualifizierten URL gespeichert sein. Die zum Angeben eines Berichts verwendete Methode kann abhängig davon variieren, ob es sich um einen Berichtsserver oder eine in einen Berichtsserver integrierte SharePoint-Website handelt. Wenn der Berichtsserver im integrierten SharePoint-Modus konfiguriert ist, werden nur URL-Aktionen unterstützt.  
  
 Weitere Informationen finden Sie unter [Hinzufügen einer Drillthroughaktion für einen Bericht &#40;Berichts-Generator und SSRS&#41;](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md) und [Angeben von Pfaden zu externen Elementen &#40;Berichts-Generator und SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
## <a name="viewing-a-drillthrough-report"></a>Anzeigen eines Drillthroughberichts  
 Wenn Sie einen Zusammenfassungsbericht mit Drillthroughlinks nach seiner Veröffentlichung anzeigen möchten, müssen Sie sicherstellen, dass sich die Drillthroughberichte auf demselben Berichtsserver wie der zusammenfassende Bericht befinden. In jedem Fall benötigt der Benutzer Berechtigungen für den Drillthroughbericht, um ihn anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Drillthrough, Drilldown, Unterberichte und geschachtelte Datenbereiche &#40;Berichts-Generator und SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
