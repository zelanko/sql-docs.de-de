---
title: Data Mining-Lernprogramm für Fortgeschrittene (Analysis Services-Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 404b31d5-27f4-4875-bd60-7b2b8613eb1b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4c244701d8a58765061ef3bde1f918c8be5a941d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63017181"
---
# <a name="intermediate-data-mining-tutorial-analysis-services---data-mining"></a>Data Mining-Lernprogramm für Fortgeschrittene (Analysis Services - Data Mining)
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet eine integrierte Umgebung zum Erstellen von und arbeiten mit Data Mining Modellen. Sie können ohne Weiteres eine Bindung an Datenquellen herstellen, mehrere Modelle für die gleichen Daten erstellen und testen und Modelle für Vorhersageanalysen bereitstellen.  
  
 Im Lernprogramm zu Data Mining-Grundlagen haben Sie gelernt, mit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] eine Data Mining-Lösung zu erstellen. Außerdem haben Sie drei Modelle für eine Targeted Mailing-Kampagne erstellt, um das Kaufverhalten von Kunden zu analysieren und potenzielle Kunden anzusprechen.  
  
 Das Lernprogramm für Fortgeschrittene baut auf diesen Erfahrungen auf. Ferner werden mehrere neue Szenarien, einschließlich allgemeiner Geschäftsanforderungen wie Forecasting und Market Basket-Analysen, vorgestellt. Sie lernen, ein Zeitreihenmodell, ein Zuordnungsmodell sowie ein Sequenzclustermodell zu erstellen. Schließlich erfahren Sie, wie Sie mit einem neuronalen Netzwerk Korrelationen in Daten untersuchen und mithilfe der logistischen Regression Vorhersagen treffen.  
  
 Die Lektionen sind unabhängig voneinander und können separat abgeschlossen werden.  
  
 Für das folgende Lernprogramm sollten Sie mit den Data Mining-Tools sowie den Miningmodell-Viewern vertraut sein, die im Lernprogramm zu Data Mining-Grundlagen vorgestellt wurden.  
  
 In allen Szenarien wird die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-Datenquelle verwendet. Sie erstellen jedoch verschiedene Datenquellensichten für verschiedene Szenarien. Sie können die Lektionen in beliebiger Reihenfolge absolvieren; die Datenquelle muss allerdings zuerst erstellt werden.  
  
## <a name="lesson-scenarios"></a>Lektionsszenarien  
 Nachdem Sie sich erfolgreich mit der Targeted Mailing-Kampagne beschäftigt haben, wurden Sie gebeten, Ihre Data Mining-Kenntnisse in die Entwicklung mehrerer neuer Modelle für die Unternehmensplanung einfließen zu lassen. Dabei handelt es sich um die folgenden Aufgaben:  
  
-   **Vorhersagen:** Sie erstellen ein *Zeitreihen* Modell, um die Umsätze von Produkten in unterschiedlichen Regionen auf der ganzen Welt vorherzusagen. Sie entwickeln einzelne Modelle für jede Region und erfahren, wie *Kreuz Vorhersagen*verwendet werden.  
  
-   **Market Basket-Analyse:** Sie erstellen ein Zuordnungs *Modell*, um Gruppierungen von Produkten zu analysieren, die während der Besuche auf [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] der e-Commerce-Website erworben werden. Auf Grundlage dieses Market Basket-Modells können Sie Kunden Produkte empfehlen.  
  
-   **Sequenzanalyse:** Sie erstellen ein *Sequence Clustering-Modell*, um die Reihenfolge zu analysieren, in der Kunden Produkte kaufen. Auf Grundlage dieses Modells können Sie Änderungen im Websitedesign vornehmen oder neue Produkte anbieten.  
  
-   **Faktoranalyse:** Sie verwenden ein *neuronales Netzwerk* Modell, um die möglichen Ursachen für eine schlechte Dienst Qualität in Callcenterdaten zu untersuchen. Basierend auf den Erkenntnissen aus dem vorläufigen Modell erstellen Sie ein *logistisches Regressionsmodell* , um Strategien zur Verbesserung der Kundenfreundlichkeit vorherzusagen.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie Sie verschiedene Typen von Data Mining-Algorithmen anlegen und mit diesen arbeiten. Dieses Lernprogramm ist in die folgenden Lektionen aufgeteilt:  
  
 [Lektion 1: Erstellen der Data Mining-Lösung für fortgeschrittene &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
 In dieser Lektion erstellen Sie ein neues Projekt auf Basis der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-Datenbank zur Unterstützung mehrerer neuer Datenquellensichten und zahlreicher weiterer Miningmodelle.  
  
 [Lektion 2: Erstellung eines Vorhersage Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
 In dieser Lektion erstellen Sie ein Mining Modell, das als Teil eines Vorhersage Szenarios verwendet werden kann. Sie werden auch Mining Modelle untersuchen, die mit dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus erstellt wurden.  
  
 Zunächst erstellen Sie Modelle für einzelne Regionen und anschließend ein allgemeines Modell für Kreuzvorhersagen.  
  
 [Lektion 3: aufbauen eines Market Basket-Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
 In dieser Lektion fügen Sie eine neue Datenquellensicht hinzu und lernen, mit geschachtelten Tabellen und geschachtelten Schlüsseln zu arbeiten. Auf der Grundlage dieser Daten legen Sie ein Miningmodell an, das in einem Market Basket-Szenario verwendet werden kann. Sie werden auch Mining Modelle untersuchen, die mit dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus erstellt wurden.  
  
 [Lektion 4: Entwickeln eines Sequence Clustering-Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
 In dieser Lektion lernen Sie, ein Miningmodell anzulegen, das in einem Sequenzclusterszenario verwendet werden kann. Sie lernen, wie Sie Miningmodelle prüfen, die mit dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus erstellt wurden.  
  
 [Lektion 5: aufbauen von neuronalen Netzwerk-und logistischen Regressionsmodellen &#40;Data&#41;Mining-Lernprogramms](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
 In dieser Lektion erstellen Sie mehrere zugehörige Miningmodelle mithilfe der Microsoft Neural Network- und Microsoft Logistic Regression-Algorithmen. Sie erfahren zudem, wie Sie mithilfe von Datenquellensichten Daten untersuchen, die den Modellen zugrunde liegen.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Stellen Sie sicher, dass Folgendes installiert ist:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank.  
  
 Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert. Um die offiziellen Datenbanken für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu installieren, rufen Sie die Seite [Microsoft SQL-Beispiel Datenbanken](https://go.microsoft.com/fwlink/?LinkId=88417) auf, und wählen Sie die entsprechende Version der-Beispieldatenbank aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Tutorial zu Bike Buyer DMX](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [Market Basket DMX-Lernprogramm](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
  
