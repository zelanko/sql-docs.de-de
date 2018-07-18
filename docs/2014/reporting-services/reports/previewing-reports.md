---
title: Ausführen einer Vorschau für Berichte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], previewing reports
- previewing reports [Reporting Services]
- printing previews
- test servers [Reporting Services]
ms.assetid: 85117f6c-828e-45c9-810f-e700d9bfba67
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: afcfb2cf31526f4e8898fafbe72f9492a1848886
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202530"
---
# <a name="previewing-reports"></a>Ausführen einer Vorschau für Berichte
  Wenn Sie einen Bericht entwerfen, sollten Sie ihn anzeigen, bevor Sie ihn in einer Produktionsumgebung veröffentlichen. Dazu gibt es mehrere Möglichkeiten: Sie können im Berichts-Designer in den Vorschaumodus wechseln, im Berichts-Designer das Vorschaufenster verwenden oder den Bericht auf einem Berichtsserver in einer Testumgebung veröffentlichen.  
  
> [!NOTE]  
>  Wenn Sie eine Vorschau für einen Bericht anzeigen, werden die Daten für den Bericht auf dem lokalen Computer in einer Datei zwischengespeichert. Wenn Sie für denselben Bericht erneut eine Vorschau anzeigen, indem Sie dieselbe Abfrage und dieselben Parameter und Anmeldeinformationen verwenden, ruft der Berichts-Designer die zwischengespeicherte Kopie ab, anstatt die Abfrage erneut auszuführen. Die Datendatei wird in demselben Verzeichnis wie die Berichtsdefinitionsdatei unter dem Namen „*\<Berichtsname>*.rdl.data“ gespeichert. Die Datei wird nicht gelöscht, wenn Sie den Berichts-Designer schließen.  
  
## <a name="preview-mode"></a>Vorschaumodus  
 Sie können die Vorschau ein Berichts im Berichts-Designer anzeigen, indem Sie auf **Vorschau**. Dadurch wird der Bericht lokal mit derselben Berichtsverarbeitungs- und Renderingfunktionalität ausgeführt, die auf dem Berichtsserver zur Verfügung steht. Der Bericht wird als interaktives Bild angezeigt, in dem Sie Parameter auswählen, auf Links klicken, die Dokumentstruktur anzeigen und ausgeblendete Bereiche des Berichts erweitern bzw. reduzieren können. Darüber hinaus können Sie den Bericht in jedes installierte Renderingformat exportieren.  
  
## <a name="standalone-preview"></a>Eigenständige Vorschau  
 Sie können auch das Berichtsprojekt in einer Debugkonfiguration ausführen, um eine Vorschau des Berichts anzuzeigen, zum Beispiel zum Debuggen von benutzerdefinierten Assemblys, die Sie geschrieben haben. Ein Berichtsprojekt kann auf drei Arten ausgeführt werden:  
  
-   Durch Klicken auf **starten** auf die **Debuggen** Menü.  
  
-   Durch Klicken auf die **starten** Schaltfläche der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Standardsymbolleiste.  
  
-   Durch Drücken von F5.  
  
 Bei Verwendung einer Projektkonfiguration, die den Bericht erstellt, aber wird nicht bereitgestellt, wird der Bericht, der im angegebenen die `StartItem` -Eigenschaft der aktuellen Konfiguration wird in einem separaten Vorschaufenster geöffnet. Im Vorschaufenster wird der Bericht genauso und mit derselben Funktionalität angezeigt wie im Vorschaumodus.  
  
> [!NOTE]  
>  Vor dem Debuggen eines Berichts müssen Sie ein Startelement festlegen. Wenn ein Startelement festlegen möchten, im Projektmappen-Explorer das Berichtsprojekt, klicken Sie auf **Eigenschaften**, und klicken Sie dann im `StartItem`, wählen Sie den Namen des Berichts angezeigt.  
  
 Wenn Sie einen bestimmten Bericht in der Vorschau anzeigen möchten, der nicht als Startelement für das Projekt festgelegt ist, wählen Sie eine Konfiguration aus, die den Bericht zwar erstellt, jedoch nicht bereitstellt (z.B. die DebugLocal-Konfiguration). Klicken Sie dann mit der rechten Maustaste auf den Bericht, und klicken Sie anschließend auf **Ausführen**. Sie müssen eine Konfiguration auswählen, die den Bericht nicht bereitstellt. Andernfalls wird der Bericht auf dem Berichtsserver veröffentlicht und nicht lokal in einem Vorschaufenster angezeigt.  
  
## <a name="print-preview"></a>Seitenansicht  
 Wenn Sie einen Bericht zum ersten Mal im Vorschaumodus oder im Vorschaufenster anzeigen, gleicht die Anzeige des Berichts einem per HTML-Renderingerweiterung erstellten Bericht. Die Vorschau ist kein HTML-Code, das Layout und die Paginierung des Berichts gleichen jedoch der HTML-Ausgabe.  
  
 Sie können die Ansicht ändern und einen gedruckten Bericht darstellen, indem Sie zur Seitenansicht wechseln. Klicken Sie auf der Vorschausymbolleiste auf die Schaltfläche **Seitenansicht** . Der Bericht wird so angezeigt, wie er auf einer physischen Seite dargestellt werde würde. Diese Ansicht gleicht der Ausgabe durch die Bild- und PDF-Renderingerweiterung. Die Seitenansicht ist keine Bild- oder PDF-Datei, das Layout und die Paginierung des Berichts gleichen jedoch der Ausgabe in diesen Formaten.  
  
## <a name="publishing-to-a-test-server"></a>Veröffentlichen auf einem Testserver  
 Ferner können Sie Berichte durch Veröffentlichen auf einem Testserver testen. Das Veröffentlichen eines Berichts auf einem Testserver unterscheidet sich nicht vom Veröffentlichen auf einem Produktionsserver. Informationen zum Veröffentlichen eines Berichts finden Sie unter [Veröffentlichen von Berichten auf einem Berichtsserver](publishing-reports-to-a-report-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Drucken von Berichten &#40;Berichts-Generator und SSRS&#41;](../report-builder/print-reports-report-builder-and-ssrs.md)   
 [Drucken eines Berichts &#40;Berichts-Generator und SSRS&#41;](../report-builder/print-a-report-report-builder-and-ssrs.md)   
 [Veröffentlichen von Berichten](../publish-reports.md)   
 [Verwenden benutzerdefinierter Assemblys mit Berichten](../custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
