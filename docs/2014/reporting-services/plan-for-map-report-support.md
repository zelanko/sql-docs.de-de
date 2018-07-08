---
title: Planen der Unterstützung für Kartenberichte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
caps.latest.revision: 10
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8bfe76929c3f9b50e59cc276385b815973a0d06c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163751"
---
# <a name="plan-for-map-report-support"></a>Planen der Unterstützung für Kartenberichte
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] unterstützt kartenberichte, die räumliche Datenquellen verwenden. Räumliche Daten können aus SQL Server-Datenbanken, aus ESRI-Shape-Dateien oder aus dem Kartenkatalog stammen, der mit Reporting Services oder Berichts-Generator installiert wird. Eine Karte kann auch einen Hintergrund aus Bing-Kartenkacheln anzeigen. Ein Berichtsautor kann es sich um einen Bericht erstellen, der angibt, räumliche Daten oder Bing-kartenkacheln dynamische und zur Laufzeit abgerufene oder als statische und in der Berichtsdefinition eingebettet.  
  
## <a name="support-for-bing-maps"></a>Unterstützung von Bing-Karten  
 Karten können eine Hintergrundebene einschließen, die Bing-Kartenkacheln anzeigt. Um einen veröffentlichten Bericht anzuzeigen, der eine Kartenkachelebene aufweist, muss der Berichtsserver so konfiguriert werden, dass er Kacheln aus Bing Maps Web Services abruft. Weitere Informationen finden Sie unter [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).  
  
 Berichtsautoren können in jedem Bericht angeben, ob eine Secure Sockets Layer (SSL)-Verbindung verwendet werden soll, um Kacheln vom Kachelserver abzurufen. Klicken Sie hierzu im Bereich "Eigenschaften" für die Kachelebene müssen sie festlegen, die boolesche Eigenschaft UseSecureConnection auf `true`.  
  
> [!NOTE]  
>  Weitere Informationen zur Verwendung von Bing-Kartenkacheln im Bericht finden Sie in den [zusätzlichen Nutzungsbedingungen](http://go.microsoft.com/fwlink/?LinkId=151371) und der [Datenschutzerklärung](http://go.microsoft.com/fwlink/?LinkId=151372).  
  
## <a name="report-design-recommendations"></a>Entwurfsempfehlungen für Berichte  
 Um gute Berichtsentwürfe für Kartenberichte zu erstellen, muss der Berichtsautor die Vor- und Nachteile statischer und dynamischer räumlicher Daten bewerten und ein Gleichgewicht finden, das für die Berichtsbenutzer von Vorteil ist. Eingebettete Kartenelemente können die Größe der Berichtsdefinition bedeutend erhöhen, aber reduzieren die Zeit, die erforderlich ist, um den Kartenbericht anzuzeigen. Dynamische kartenelemente verringern die Größe der Berichtsdefinition, aber erhöhen die Zeit, die zum Verarbeiten und Anzeigen der Karte erforderlich ist. Der Berichtsautor muss das richtige Gleichgewicht zwischen diesen entgegengesetzten Aspekten finden.  
  
 Wenn die Größe der Berichtsdefinitionen eine Rolle spielt, können Sie als Berichtsserveradministrator die Berichtsautoren auffordern, weniger räumliche Daten in den Berichtsdefinitionen zu verwenden.  
  
 Unter den folgenden Bedingungen werden Kartenelemente in die Berichtsdefinition eingebettet:  
  
-   Wenn der Bericht erstellt wird, befindet sich die Datenquelle der räumlichen Daten auf dem lokalen Dateisystem. Dies schließt räumliche Daten aus dem Kartenkatalog sowie aus ESRI-Shape-Dateien ein, die lokal installiert wurden. Standardmäßig betten der Karten-Assistent und der Kartenebenen-Assistent räumliche Daten aus Datenquellen im lokalen Dateisystem ein.  
  
-   Der Berichtsautor wählt die Option aus, räumliche Daten manuell in den Bericht einzubetten.  
  
 Um die Größe von Berichtsdefinitionen zu reduzieren, die Karten enthalten, können Berichtsautoren mindestens eine der folgenden Optionen verwenden:  
  
-   Im Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], fügen Sie räumliche Datenquellen, die dem Berichtsserverprojekt ESRI-Shape-Dateien sind. Wenn Sie das Projekt bereitstellen, werden die ESRI-Shape-Dateien zusätzlich zum Bericht auf dem Berichtsserver veröffentlicht. Beim Ausführen des Karten-Assistenten kann der Berichtsautor eine räumliche Datenquelle aus dem Berichtsserverprojekt angeben, und die Kartenelemente werden standardmäßig nicht in die Berichtsdefinitionen eingebettet.  
  
-   Fügen Sie Berichts-Generator räumliche Datenquellen, die ESRI-Shape-Dateien sind dazu-Shape-Dateien auf dem Berichtsserver ein. Beim Ausführen des Karten-Assistenten kann der Berichtsautor zu einer räumlichen Datenquelle auf dem Berichtsserver navigieren und sie auswählen, und die Kartenelemente werden standardmäßig nicht in die Berichtsdefinitionen eingebettet.  
  
-   Wenn Kartendaten eingebettet sein müssen, passen Sie den Viewport-Mittelpunkt und die Zoomstufe an, um nur die Kartendaten einzuschließen, die für den Bericht benötigt werden.  
  
 Weitere Informationen [Maps &#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei Berichten: Kartenberichte &#40;Berichts-Generator und SSRS&#41;](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
