---
title: Planen der Unterstützung von Karten Berichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: df796e2dd4e132164f00716a9cb12f7b498d8984
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108081"
---
# <a name="plan-for-map-report-support"></a>Planen der Unterstützung für Kartenberichte
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]unterstützt Karten Berichte, die räumliche Datenquellen verwenden. Räumliche Daten können aus SQL Server-Datenbanken, aus ESRI-Shape-Dateien oder aus dem Kartenkatalog stammen, der mit Reporting Services oder Berichts-Generator installiert wird. Eine Karte kann auch einen Hintergrund aus Bing-Kartenkacheln anzeigen. Ein Berichtsautor kann einen Bericht erstellen, der dynamische, zur Laufzeit abgerufene oder statische, in die Berichtsdefinition eingebettete räumliche Daten oder Bing-Kartenkacheln angibt.  
  
## <a name="support-for-bing-maps"></a>Unterstützung von Bing-Karten  
 Karten können eine Hintergrundebene einschließen, die Bing-Kartenkacheln anzeigt. Um einen veröffentlichten Bericht anzuzeigen, der eine Kartenkachelebene aufweist, muss der Berichtsserver so konfiguriert werden, dass er Kacheln aus Bing Maps Web Services abruft. Weitere Informationen finden Sie unter [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).  
  
 Berichtsautoren können in jedem Bericht angeben, ob eine Secure Sockets Layer (SSL)-Verbindung verwendet werden soll, um Kacheln vom Kachelserver abzurufen. Zu diesem Zweck müssen Sie im Bereich "Eigenschaften" für die Kachel Ebene die boolesche Eigenschaft "seresecureconnection" auf `true`festlegen.  
  
> [!NOTE]  
>   Weitere Informationen zur Verwendung von Bing-Kartenkacheln im Bericht finden Sie in den [zusätzlichen Nutzungsbedingungen](https://go.microsoft.com/fwlink/?LinkId=151371) und der [Datenschutzerklärung](https://go.microsoft.com/fwlink/?LinkId=151372).  
  
## <a name="report-design-recommendations"></a>Entwurfsempfehlungen für Berichte  
 Um gute Berichtsentwürfe für Kartenberichte zu erstellen, muss der Berichtsautor die Vor- und Nachteile statischer und dynamischer räumlicher Daten bewerten und ein Gleichgewicht finden, das für die Berichtsbenutzer von Vorteil ist. Eingebettete Kartenelemente können die Größe der Berichtsdefinition bedeutend erhöhen, aber reduzieren die Zeit, die erforderlich ist, um den Kartenbericht anzuzeigen. Dynamische Kartenelemente verringern die Größe der Berichtsdefinition, erhöhen jedoch die Zeit, die zum Verarbeiten und Anzeigen der Karte erforderlich ist. Der Berichtsautor muss das richtige Gleichgewicht zwischen diesen entgegengesetzten Aspekten finden.  
  
 Wenn die Größe der Berichtsdefinitionen eine Rolle spielt, können Sie als Berichtsserveradministrator die Berichtsautoren auffordern, weniger räumliche Daten in den Berichtsdefinitionen zu verwenden.  
  
 Unter den folgenden Bedingungen werden Kartenelemente in die Berichtsdefinition eingebettet:  
  
-   Wenn der Bericht erstellt wird, befindet sich die Datenquelle der räumlichen Daten auf dem lokalen Dateisystem. Dies schließt räumliche Daten aus dem Kartenkatalog sowie aus ESRI-Shape-Dateien ein, die lokal installiert wurden. Standardmäßig betten der Karten-Assistent und der Kartenebenen-Assistent räumliche Daten aus Datenquellen im lokalen Dateisystem ein.  
  
-   Der Berichtsautor wählt die Option aus, räumliche Daten manuell in den Bericht einzubetten.  
  
 Um die Größe von Berichtsdefinitionen zu reduzieren, die Karten enthalten, können Berichtsautoren mindestens eine der folgenden Optionen verwenden:  
  
-   Fügen Sie dem [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Berichts Server Projekt aus Berichts-Designer in räumliche Datenquellen hinzu, die ESRI-Shape-Dateien sind. Wenn Sie das Projekt bereitstellen, werden die ESRI-Shape-Dateien zusätzlich zum Bericht auf dem Berichtsserver veröffentlicht. Beim Ausführen des Karten-Assistenten kann der Berichtsautor eine räumliche Datenquelle aus dem Berichtsserverprojekt angeben, und die Kartenelemente werden standardmäßig nicht in die Berichtsdefinitionen eingebettet.  
  
-   Fügen Sie in Berichts-Generator räumliche Datenquellen hinzu, die ESRI-Shape-Dateien sind, indem Sie Shape-Dateien vom Berichts Server auswählen. Beim Ausführen des Karten-Assistenten kann der Berichtsautor zu einer räumlichen Datenquelle auf dem Berichtsserver navigieren und sie auswählen, und die Kartenelemente werden standardmäßig nicht in die Berichtsdefinitionen eingebettet.  
  
-   Wenn Kartendaten eingebettet sein müssen, passen Sie den Viewport-Mittelpunkt und die Zoomstufe an, um nur die Kartendaten einzuschließen, die für den Bericht benötigt werden.  
  
 Weitere Informationen finden Sie unter [&#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei Berichten: Kartenberichte &#40;Berichts-Generator und SSRS&#41;](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
