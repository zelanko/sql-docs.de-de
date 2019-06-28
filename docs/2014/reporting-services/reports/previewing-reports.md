---
title: Anzeigen von Berichten in der Vorschau
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 21928cd6637815000983e8a0fe05aa4e77d1c216
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412971"
---
# <a name="preview-reports-in-sql-server-reporting-services-ssrs"></a>Vorschauberichte in SQL Server Reporting Services (SSRS)

  Wenn Sie einen Bericht entwerfen, sollten Sie ihn anzeigen, bevor Sie ihn in einer Produktionsumgebung veröffentlichen. Dazu gibt es mehrere Möglichkeiten: Sie können im Berichts-Designer in den Vorschaumodus wechseln, im Berichts-Designer das Vorschaufenster verwenden oder den Bericht auf einem Berichtsserver in einer Testumgebung veröffentlichen.  
  
> [!NOTE]  
> Wenn Sie eine Vorschau für einen Bericht anzeigen, werden die Daten für den Bericht auf dem lokalen Computer in einer Datei zwischengespeichert. Wenn Sie für denselben Bericht erneut eine Vorschau anzeigen, indem Sie dieselbe Abfrage und dieselben Parameter und Anmeldeinformationen verwenden, ruft der Berichts-Designer die zwischengespeicherte Kopie ab, anstatt die Abfrage erneut auszuführen. Die Datendatei wird in demselben Verzeichnis wie die Berichtsdefinitionsdatei unter dem Namen „ *\<Berichtsname>* .rdl.data“ gespeichert. Die Datei wird nicht gelöscht, wenn Sie den Berichts-Designer schließen.  
  
## <a name="preview-mode"></a>Vorschaumodus

 Sie können die Vorschau ein Berichts im Berichts-Designer anzeigen, indem Sie auf **Vorschau**. Dadurch wird der Bericht lokal mit derselben Berichtsverarbeitungs- und Renderingfunktionalität ausgeführt, die auf dem Berichtsserver zur Verfügung steht. Der Bericht wird als interaktives Bild angezeigt, in dem Sie Parameter auswählen, auf Links klicken, die Dokumentstruktur anzeigen und ausgeblendete Bereiche des Berichts erweitern bzw. reduzieren können. Darüber hinaus können Sie den Bericht in jedes installierte Renderingformat exportieren.  
  
## <a name="standalone-preview"></a>Eigenständige Vorschau

 Sie können auch das Berichtsprojekt in einer Debugkonfiguration ausführen, um eine Vorschau des Berichts anzuzeigen, zum Beispiel zum Debuggen von benutzerdefinierten Assemblys, die Sie geschrieben haben. Ein Berichtsprojekt kann auf drei Arten ausgeführt werden:  
  
- Durch Klicken auf **starten** auf die **Debuggen** Menü.  
  
- Durch Klicken auf die **starten** Schaltfläche der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Standardsymbolleiste.  
  
- Durch Drücken von F5.  
  
 Falls Sie eine Projektkonfiguration verwenden, die zwar den Bericht erstellt, aber nicht bereitstellt, wird der in der `StartItem`-Eigenschaft angegebene Bericht der aktuellen Konfiguration in einem separaten Vorschaufenster geöffnet. Im Vorschaufenster wird der Bericht genauso und mit derselben Funktionalität angezeigt wie im Vorschaumodus.  
  
> [!NOTE]  
> Vor dem Debuggen eines Berichts müssen Sie ein Startelement festlegen. Wenn ein Startelement festlegen möchten, im Projektmappen-Explorer das Berichtsprojekt, klicken Sie auf **Eigenschaften**, und klicken Sie dann im `StartItem`, wählen Sie den Namen des Berichts angezeigt.  
  
 Wenn Sie einen bestimmten Bericht in der Vorschau anzeigen möchten, der nicht als Startelement für das Projekt festgelegt ist, wählen Sie eine Konfiguration aus, die den Bericht zwar erstellt, jedoch nicht bereitstellt (z.B. die DebugLocal-Konfiguration). Klicken Sie dann mit der rechten Maustaste auf den Bericht, und klicken Sie anschließend auf **Ausführen**. Sie müssen eine Konfiguration auswählen, die den Bericht nicht bereitstellt. Andernfalls wird der Bericht auf dem Berichtsserver veröffentlicht und nicht lokal in einem Vorschaufenster angezeigt.  
  
## <a name="print-preview"></a>Seitenansicht

 Wenn Sie einen Bericht zum ersten Mal im Vorschaumodus oder im Vorschaufenster anzeigen, gleicht die Anzeige des Berichts einem per HTML-Renderingerweiterung erstellten Bericht. Die Vorschau ist kein HTML-Code, das Layout und die Paginierung des Berichts gleichen jedoch der HTML-Ausgabe.  
  
 Sie können die Ansicht ändern und einen gedruckten Bericht darstellen, indem Sie zur Seitenansicht wechseln. Klicken Sie auf der Vorschausymbolleiste auf die Schaltfläche **Seitenansicht** . Der Bericht wird so angezeigt, wie er auf einer physischen Seite dargestellt werde würde. Diese Ansicht gleicht der Ausgabe durch die Bild- und PDF-Renderingerweiterung. Die Seitenansicht ist keine Bild- oder PDF-Datei, das Layout und die Paginierung des Berichts gleichen jedoch der Ausgabe in diesen Formaten.  
  
## <a name="publish-to-a-test-server"></a>Veröffentlichen auf einem Testserver

 Ferner können Sie Berichte durch Veröffentlichen auf einem Testserver testen. Das Veröffentlichen eines Berichts auf einem Testserver unterscheidet sich nicht vom Veröffentlichen auf einem Produktionsserver. Informationen zum Veröffentlichen eines Berichts finden Sie unter [Veröffentlichen von Berichten auf einem Berichtsserver](publishing-reports-to-a-report-server.md).  
  
## <a name="next-steps"></a>Nächste Schritte

 - [Drucken von Berichten (Berichts-Generator und SSRS)](../report-builder/print-reports-report-builder-and-ssrs.md)
 - [Drucken eines Berichts &#40;Berichts-Generator und SSRS&#41;](../report-builder/print-a-report-report-builder-and-ssrs.md)
 - [Veröffentlichen von Berichten](../publish-reports.md)
 - [Verwenden benutzerdefinierter Assemblys mit Berichten](../custom-assemblies/using-custom-assemblies-with-reports.md)