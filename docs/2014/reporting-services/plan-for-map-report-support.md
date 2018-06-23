---
title: Planen der Unterstützung für Kartenberichte | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
caps.latest.revision: 10
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: cf56a62b3ef129d9d725aa54d05544f776d4f6ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048006"
---
# <a name="plan-for-map-report-support"></a>Planen der Unterstützung für Kartenberichte
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] unterstützt kartenberichte, die räumliche Datenquellen verwenden. Räumliche Daten können aus SQL Server-Datenbanken, aus ESRI-Shape-Dateien oder aus dem Kartenkatalog stammen, der mit Reporting Services oder Berichts-Generator installiert wird. Eine Karte kann auch einen Hintergrund aus Bing-Kartenkacheln anzeigen. Ein Berichtsautor kann einen Bericht erstellen, der angibt, räumliche Daten oder Bing-kartenkacheln als dynamische und zur Laufzeit abgerufene oder als statische und in die Berichtsdefinition eingebettet.  
  
## <a name="support-for-bing-maps"></a>Unterstützung von Bing-Karten  
 Karten können eine Hintergrundebene einschließen, die Bing-Kartenkacheln anzeigt. Um einen veröffentlichten Bericht anzuzeigen, der eine Kartenkachelebene aufweist, muss der Berichtsserver so konfiguriert werden, dass er Kacheln aus Bing Maps Web Services abruft. Weitere Informationen finden Sie unter [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).  
  
 Berichtsautoren können in jedem Bericht angeben, ob eine Secure Sockets Layer (SSL)-Verbindung verwendet werden soll, um Kacheln vom Kachelserver abzurufen. Klicken Sie dazu im Bereich "Eigenschaften" für die Kachelebene müssen sie festlegen, die boolesche Eigenschaft UseSecureConnection auf `true`.  
  
> [!NOTE]  
>  Weitere Informationen zur Verwendung von Bing-Kartenkacheln im Bericht finden Sie in den [zusätzlichen Nutzungsbedingungen](http://go.microsoft.com/fwlink/?LinkId=151371) und der [Datenschutzerklärung](http://go.microsoft.com/fwlink/?LinkId=151372).  
  
## <a name="report-design-recommendations"></a>Entwurfsempfehlungen für Berichte  
 Um gute Berichtsentwürfe für Kartenberichte zu erstellen, muss der Berichtsautor die Vor- und Nachteile statischer und dynamischer räumlicher Daten bewerten und ein Gleichgewicht finden, das für die Berichtsbenutzer von Vorteil ist. Eingebettete Kartenelemente können die Größe der Berichtsdefinition bedeutend erhöhen, aber reduzieren die Zeit, die erforderlich ist, um den Kartenbericht anzuzeigen. Dynamische kartenelemente verringern die Größe der Berichtsdefinition, aber erhöhen die Zeit, die zum Verarbeiten und Anzeigen der Zuordnung erforderlich ist. Der Berichtsautor muss das richtige Gleichgewicht zwischen diesen entgegengesetzten Aspekten finden.  
  
 Wenn die Größe der Berichtsdefinitionen eine Rolle spielt, können Sie als Berichtsserveradministrator die Berichtsautoren auffordern, weniger räumliche Daten in den Berichtsdefinitionen zu verwenden.  
  
 Unter den folgenden Bedingungen werden Kartenelemente in die Berichtsdefinition eingebettet:  
  
-   Wenn der Bericht erstellt wird, befindet sich die Datenquelle der räumlichen Daten auf dem lokalen Dateisystem. Dies schließt räumliche Daten aus dem Kartenkatalog sowie aus ESRI-Shape-Dateien ein, die lokal installiert wurden. Standardmäßig betten der Karten-Assistent und der Kartenebenen-Assistent räumliche Daten aus Datenquellen im lokalen Dateisystem ein.  
  
-   Der Berichtsautor wählt die Option aus, räumliche Daten manuell in den Bericht einzubetten.  
  
 Um die Größe von Berichtsdefinitionen zu reduzieren, die Karten enthalten, können Berichtsautoren mindestens eine der folgenden Optionen verwenden:  
  
-   Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], fügen Sie räumliche Datenquellen, die dem Berichtsserverprojekt ESRI-Shape-Dateien sind. Wenn Sie das Projekt bereitstellen, werden die ESRI-Shape-Dateien zusätzlich zum Bericht auf dem Berichtsserver veröffentlicht. Beim Ausführen des Karten-Assistenten kann der Berichtsautor eine räumliche Datenquelle aus dem Berichtsserverprojekt angeben, und die Kartenelemente werden standardmäßig nicht in die Berichtsdefinitionen eingebettet.  
  
-   Fügen Sie räumliche Datenquellen, die ESRI-Shape-Dateien sind dazu-Shape-Dateien vom Berichtsserver aus Berichts-Generator hinzu. Beim Ausführen des Karten-Assistenten kann der Berichtsautor zu einer räumlichen Datenquelle auf dem Berichtsserver navigieren und sie auswählen, und die Kartenelemente werden standardmäßig nicht in die Berichtsdefinitionen eingebettet.  
  
-   Wenn Kartendaten eingebettet sein müssen, passen Sie den Viewport-Mittelpunkt und die Zoomstufe an, um nur die Kartendaten einzuschließen, die für den Bericht benötigt werden.  
  
 Weitere Informationen [Maps &#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei Berichten: Ordnen Sie Berichte &#40;Berichts-Generator und SSRS&#41;](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  