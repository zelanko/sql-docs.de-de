---
title: 'Lektion 13: Bereitstellen von | Microsoft-Dokumentation'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c20a0367612aee48c1a58e9cde8ba1a44d3fafc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404802"
---
# <a name="lesson-13-deploy"></a>Lektion 13: Bereitstellen
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion Konfigurieren Sie Bereitstellungseigenschaften; Angeben einer lokalen oder Azure-Server-Instanz und einen Namen für das Modell. Sie stellen das Modell dann zu dieser Instanz bereit. Nachdem das Modell bereitgestellt wurde, können Benutzer das Herstellen einer Verbindung mit einer Clientanwendung zur berichtserstellung. Weitere Informationen zur Bereitstellung finden Sie unter [Bereitstellung von tabellenmodelllösungen](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md) und [bereitstellen an Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy).  
  
Geschätzte Zeit zum Abschließen dieser Lektion: **5 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 12: In Excel analysieren](lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Bereitstellen des Modells  
  
#### <a name="to-configure-deployment-properties"></a>So konfigurieren Sie Bereitstellungseigenschaften  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AW-Internetverkäufe** Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  In der **Eigenschaftenseiten des AW Internet Sales** Dialogfeld **Bereitstellungsserver**in die **Server** -Eigenschaft, geben Sie den Namen eines Azure Analysis Services-Servers oder einer lokale Server-Instanz im tabellarischen Modus ausgeführt. Dadurch werden die Server-Instanz, die, der das Modell bereitgestellt wird.  

    ![aas-deploy-deployment-server-property](media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > Sie müssen über Administratorberechtigungen verfügen, auf dem remote Analysis Services-Instanz im-Auftrag, um dort Modelle bereitstellen.  
  
3.  In der **Datenbank** Eigenschaft **Adventure Works Internet Sales**.  
  
4.  In der **Modellname** Eigenschaft **Adventure Works Internet Sales Model**.  
  
5.  Überprüfen Sie die Auswahl, und klicken Sie anschließend auf **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>So stellen Sie das Tabellenmodell für Adventure Works-Internetverkäufe bereit  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AW-Internetverkäufe** Projekt > **erstellen**.  

2.  Mit der rechten Maustaste die **AW-Internetverkäufe** Projekt > **bereitstellen**.

    Bei der Bereitstellung in Azure Analysis Services werden Sie wahrscheinlich aufgefordert, Ihre Kontodaten einzugeben. Geben Sie Ihr organisationskonto und das Kennwort, z. B. nancy@adventureworks.com. Dieses Konto muss Administrator auf der Serverinstanz sein.
  
    Das Dialogfeld für die Bereitstellung öffnet sich und zeigt den Bereitstellungsstatus der Metadaten sowie jede im Modell enthaltene Tabelle an.  
    
    ![aas-deploy-status](media/aas-deploy-status.png)
  
3. Wenn die Bereitstellung erfolgreich abgeschlossen wurde, fahren Sie fort, und klicken Sie auf **Schließen**.  
  
## <a name="conclusion"></a>Schlussbemerkung  
Herzlichen Glückwunsch! Sie sind fertig, Erstellung und Bereitstellung Ihres ersten tabellarischen Analysis Services-Modells. Mit diesem Lernprogramm wurden Sie durch die häufigsten Aufgaben zur Erstellung eines Tabellenmodells geführt. Nach der Bereitstellung des Adventure Works-Internetverkaufsmodells können Sie nun mit SQL Server Management Studio das Modell verwalten und Prozessskripts sowie einen Sicherungsplan erstellen. Benutzer können jetzt auch mit dem Modell mithilfe einer Clientanwendung zur berichtserstellung wie Microsoft Excel oder Power BI eine Verbindung herstellen.  

![as-tabular-lesson13-ssms](media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>Siehe auch  
[DirectQuery-Modus](../tabular-models/directquery-mode-ssas-tabular.md)  
[Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften](../tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Tabellarische Modelldatenbanken](../tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>Wie geht es weiter?
*  [Ergänzende Lektion – Implementieren von dynamischer Sicherheit mithilfe von Zeilenfiltern](supplemental-lesson-implement-dynamic-security-by-using-row-filters.md).

*  [Ergänzende Lektion: Konfigurieren von Berichterstellungseigenschaften für Power View-Berichte](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md).
