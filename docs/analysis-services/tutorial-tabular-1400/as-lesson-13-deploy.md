---
title: 'Analysis Services-Tutorial – Lektion 13: Bereitstellen | Microsoft-Dokumentation'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ed155c0d3621c59e844e30d10dc7117e587a8f9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37973082"
---
# <a name="deploy"></a>Bereitstellen

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion Konfigurieren Sie Bereitstellungseigenschaften; ein Server für die Bereitstellung und einen Namen für das Modell angeben. Klicken Sie dann bereitgestellt das Modell mit dem Server. Nachdem das Modell bereitgestellt wurde, können Benutzer das Herstellen einer Verbindung mit einer Clientanwendung zur berichtserstellung. Weitere Informationen finden Sie unter [bereitstellen an Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy) und [Bereitstellung von tabellenmodelllösungen](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **5 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion an, Sie sollten die vorherige Lektion abgeschlossen haben: [Lektion 12: Analysieren in Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md).  

> [!IMPORTANT]  
> Wenn Sie mit Azure Analysis Services bereitstellen zu können, benötigen Sie [Administratorberechtigungen](https://docs.microsoft.com/azure/analysis-services/analysis-services-server-admins) auf dem Server.  

> [!IMPORTANT]  
> Wenn Sie die AdventureWorksDW-Beispieldatenbank auf einer lokalen SQL Server installiert werden soll, und Sie Ihr Modell mit einem Azure Analysis Services-Server Bereitstellen einer [On-Premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) ist erforderlich.
  
## <a name="deploy-the-model"></a>Bereitstellen des Modells  
  
#### <a name="to-configure-deployment-properties"></a>So konfigurieren Sie Bereitstellungseigenschaften  

  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AW-Internetverkäufe** Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  In der **Eigenschaftenseiten des AW Internet Sales** Dialogfeld **Bereitstellungsserver**in die **Server** -Eigenschaft, geben Sie den vollständigen Servernamen. Wenn Sie eine Verbindung mit Azure Analysis Services herstellen möchten, muss Servernamen enthalten die vollständige URL an.

    ![als lesson13-bereitstellen-Eigenschaft](../tutorial-tabular-1400/media/as-lesson13-deploy-property.png)
  
3.  In der **Datenbank** Eigenschaft **Adventure Works Internet Sales**.  
  
4.  In der **Modellname** Eigenschaft **Adventure Works Internet Sales Model**.  
  
5.  Überprüfen Sie die Auswahl, und klicken Sie anschließend auf **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales"></a>Die Adventure Works Internet Sales bereitstellen
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AW-Internetverkäufe** Projekt > **erstellen**.  

2.  Mit der rechten Maustaste die **AW-Internetverkäufe** Projekt > **bereitstellen**.

    Wenn Sie mit Azure Analysis Services bereitstellen, werden Sie möglicherweise aufgefordert, Ihre Kontodaten einzugeben. Geben Sie Ihr organisationskonto und das Kennwort ein, z. B. nancy@adventureworks.com. Dieses Konto muss Administrator auf dem Server sein.
  
    Das Dialogfeld "Deploy" wird angezeigt und zeigt den Bereitstellungsstatus der Metadaten und jede im Modell enthaltene Tabelle an.  
    
    ![als-lesson13-bereitstellen-status](../tutorial-tabular-1400/media/as-lesson13-deploy-status.png)
  
3. Wenn die Bereitstellung erfolgreich abgeschlossen wurde, fahren Sie fort, und klicken Sie auf **Schließen**.  
  

In dieser Lektion wird die am häufigsten verwendete und einfachste Methode zum Bereitstellen eines tabellarischen Modells über SSDT beschrieben. Erweiterte Bereitstellungsoptionen wie etwa der Bereitstellungs-Assistent oder die Automatisierung mit XMLA und AMO bieten größere Flexibilität, Konsistenz und geplante Bereitstellungen. Weitere Informationen finden Sie unter [Bereitstellung von tabellenmodelllösungen](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).

## <a name="conclusion"></a>Fazit  
Gratulation! Sie sind fertig, Erstellung und Bereitstellung Ihres ersten tabellarischen Analysis Services-Modells. Mit diesem Lernprogramm wurden Sie durch die häufigsten Aufgaben zur Erstellung eines Tabellenmodells geführt. Nach der Bereitstellung des Adventure Works-Internetverkaufsmodells können Sie nun mit SQL Server Management Studio das Modell verwalten und Prozessskripts sowie einen Sicherungsplan erstellen. Benutzer können jetzt auch mit dem Modell mithilfe einer Clientanwendung zur berichtserstellung wie Microsoft Excel oder Power BI eine Verbindung herstellen.  

![Ssms als lesson13](../tutorial-tabular-1400/media/as-lesson13-ssms.png)
  
  
  
## <a name="whats-next"></a>Wie geht es weiter?
[Herstellen einer Verbindung mit Power BI Desktop](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect-pbi)   
[Ergänzende Lektion – dynamische Sicherheit](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)   
[Ergänzende Lektion – Detailzeilen](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)   
[Ergänzende Lektion – unregelmäßige Hierarchien](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)   
