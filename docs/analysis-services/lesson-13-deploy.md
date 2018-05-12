---
title: 'Lektion 14: Bereitstellen | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 533b6197c72d03876b928f4024fc5eb4fb0f2fc0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="lesson-13-deploy"></a>Lektion 13: Bereitstellen
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion Konfigurieren Sie Bereitstellungseigenschaften; Angeben einer lokalen oder Azure-Server-Instanz und einen Namen für das Modell. Sie stellen das Modell dann zu dieser Instanz bereit. Nachdem das Modell bereitgestellt wird, können Benutzer das Herstellen einer Verbindung mit einer berichterstellungsclientanwendung. Weitere Informationen zur Bereitstellung finden Sie unter [tabellenmodelllösungsbereitstellung](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md) und [Bereitstellung in Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy).  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **5 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion, Sie sollten haben die vorherige Lektion abgeschlossen: [Lektion 12: Analysieren in Excel](../analysis-services/lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Bereitstellen des Modells  
  
#### <a name="to-configure-deployment-properties"></a>So konfigurieren Sie Bereitstellungseigenschaften  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AW Internet Sales** Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  In der **Eigenschaftenseiten des AW Internet Sales** Dialogfeld unter **Bereitstellungsserver**in der **Server** -Eigenschaft, geben Sie den Namen des Azure Analysis Services-Servers oder einer einer lokalen Serverinstanz im tabellarischen Modus ausgeführt wird. Dadurch werden die Server-Instanz, auf der das Modell bereitgestellt wird.  

    ![AAS-bereitstellen-Deployment-Server-Eigenschaft](../analysis-services/media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > Sie benötigen Administratorberechtigungen auf dem remote Analysis Services-Instanz im-Auftrag auf darauf bereitstellen.  
  
3.  In der **Datenbank** Eigenschaft **Adventure Works-Internetverkäufe**.  
  
4.  In der **Modellname** Eigenschaft **Adventure Works Internet Sales Model**.  
  
5.  Überprüfen Sie die Auswahl, und klicken Sie anschließend auf **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>So stellen Sie das Tabellenmodell für Adventure Works-Internetverkäufe bereit  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AW Internet Sales** Projekt > **erstellen**.  

2.  Mit der rechten Maustaste die **AW Internet Sales** Projekt > **bereitstellen**.

    Beim Bereitstellen auf Azure Analysis Services werden wahrscheinlich Sie aufgefordert, Ihr Konto einzugeben. Geben Sie Ihre Organisations-Konto und Kennwort, z. B. nancy@adventureworks.com. Dieses Konto muss in "Administratoren" auf der Serverinstanz sein.
  
    Das Dialogfeld für die Bereitstellung öffnet sich und zeigt den Bereitstellungsstatus der Metadaten sowie jede im Modell enthaltene Tabelle an.  
    
    ![AAS-bereitstellen-status](../analysis-services/media/aas-deploy-status.png)
  
3. Wenn die Bereitstellung erfolgreich abgeschlossen wurde, fahren Sie fort, und klicken Sie auf **Schließen**.  
  
## <a name="conclusion"></a>Fazit  
Gratulation! Sie sind nicht mehr benötigen, erstellen und Bereitstellen von Ihrem ersten tabellarischen Analysis Services-Modell. Mit diesem Lernprogramm wurden Sie durch die häufigsten Aufgaben zur Erstellung eines Tabellenmodells geführt. Nach der Bereitstellung des Adventure Works-Internetverkaufsmodells können Sie nun mit SQL Server Management Studio das Modell verwalten und Prozessskripts sowie einen Sicherungsplan erstellen. Benutzer können jetzt auch mit dem Modell mithilfe einer Clientanwendung zur berichtserstellung wie Microsoft Excel oder Power BI eine Verbindung herstellen.  

![als-tabellarische-lesson13-ssms](../analysis-services/media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>Siehe auch  
[DirectQuery-Modus](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Tabellenmodell-Datenbanken](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>Wie geht es weiter?
*  [Ergänzende Lektion - Implementieren von dynamischer Sicherheit mithilfe von Zeilenfiltern](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md).

*  [Ergänzende Lektion: Konfigurieren von Berichterstellungseigenschaften für Power View-Berichte](../analysis-services/supplemental-lesson-configure-reporting-properties-for-power-view-reports.md).
