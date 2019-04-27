---
title: 'Lektion 14: Bereitstellen von | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ea979963906af46a1d032614ad6b398f70ef3483
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62729456"
---
# <a name="lesson-14-deploy"></a>Lektion 14: Bereitstellen
  In dieser Lektion konfigurieren Sie Bereitstellungseigenschaften, wobei Sie eine Bereitstellungsserverinstanz von Analysis Services im Tabellenmodus sowie einen Namen für das bereitgestellte Modell angeben. Sie stellen dann das Modell auf dieser Instanz bereit. Nach der Bereitstellung können Benutzer unter Verwendung einer Clientanwendung zur Berichtserstellung eine Verbindung zum Modell herstellen. Weitere Informationen finden Sie unter [Bereitstellung von Tabellenmodelllösungen &#40;SSAS – tabellarisch&#41;](tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
 Geschätzte Zeit zum Abschließen dieser Lektion: **5 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 13: In Excel analysieren](lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Bereitstellen des Modells  
  
#### <a name="to-configure-deployment-properties"></a>So konfigurieren Sie Bereitstellungseigenschaften  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt für das **Tabellenmodell für die Adventure Works-Internetverkäufe**. Klicken Sie anschließend im Kontextmenü auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld für die **Eigenschaftenseiten des Tabellenmodells für AW-Internetverkäufe** unter **Bereitstellungsserver**in der Eigenschaft **Server** den Namen einer Analysis Services-Instanz ein, die im Tabellenmodus ausgeführt wird. Dies ist die Instanz, auf der das Modell bereitgestellt wird.  
  
    > [!IMPORTANT]  
    >  Sie benötigen für die Bereitstellung auf einer Analysis Services-Remoteinstanz entsprechende Administratorberechtigungen.  
  
3.  Überprüfen Sie die **Abfragemodus** -Eigenschaftensatz auf **In-Memory**.  
  
    > [!NOTE]  
    >  Das in diesem Lernprogramm erstellte Modell wird im DirectQuery-Modus nicht unterstützt.  
  
4.  In der **Datenbank** Eigenschaft `Adventure Works Internet Sales Model`.  
  
5.  In der **Cube** Name- Eigenschaft `Adventure Works Internet Sales Model`.  
  
6.  Überprüfen Sie die Auswahl, und klicken Sie anschließend auf **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>So stellen Sie das Tabellenmodell für Adventure Works-Internetverkäufe bereit  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] auf das Menü **Erstellen** und anschließend auf die **Option zum Bereitstellen des Tabellenmodells für AW-Internetverkäufe**.  
  
     Das Dialogfeld für die Bereitstellung öffnet sich und zeigt den Bereitstellungsstatus der Metadaten sowie jede im Modell enthaltene Tabelle an.  
  
## <a name="conclusion"></a>Schlussbemerkung  
 Herzlichen Glückwunsch! Sie haben die Erstellung und Bereitstellung des ersten Analysis Services-Tabellenmodells abgeschlossen. Mit diesem Lernprogramm wurden Sie durch die häufigsten Aufgaben zur Erstellung eines Tabellenmodells geführt. Nach der Bereitstellung des Adventure Works-Internetverkaufsmodells können Sie nun mit SQL Server Management Studio das Modell verwalten und Prozessskripts sowie einen Sicherungsplan erstellen. Benutzer können mithilfe einer Clientanwendung zur Berichtserstellung wie Microsoft Excel oder [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] eine Verbindung zum Modell herstellen.  
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
 Weitere Informationen zu Tabellenmodelleigenschaften, die [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]-Berichte unterstützen, finden Sie unter [Power View-Berichterstellungseigenschaften &#40;SSAS – tabellarisch&#41;](tabular-models/properties-ssas-tabular.md).  
  
## <a name="see-also"></a>Siehe auch  
 [DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften &#40;SSAS – tabellarisch&#41;](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [Tabellarische Modelldatenbanken &#40;SSAS – tabellarisch&#41;](tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
