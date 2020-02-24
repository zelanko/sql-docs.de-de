---
title: Berichts-Viewer-Webpart auf einer SharePoint-Website (SSRS) | Microsoft-Dokumentation
ms.date: 02/11/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2ec6a87467f2ec69164827e0a1ce76ad95180377
ms.sourcegitcommit: 49082f9b6b3bc8aaf9ea3f8557f40c9f1b6f3b0b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2020
ms.locfileid: "77256807"
---
# <a name="report-viewer-web-part-on-a-sharepoint-site---reporting-services"></a>Berichts-Viewer-Webpart auf einer SharePoint-Website – Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-and-later](../../includes/ssrs-appliesto-sharepoint-2013-and-later.md)] [!INCLUDE[ssrs-appliesto-not-sharepoint-online](../../includes/ssrs-appliesto-not-sharepoint-online.md)]

Das Berichts-Viewer-Webpart ist ein benutzerdefiniertes Webpart. Mit diesem Webpart können Sie Berichte auf einem Berichtsserver auf einer SharePoint-Website abrufen und drucken. Sie können die Berichte außerdem exportieren und in ihnen navigieren. Das Berichts-Viewer-Webpart ist Berichtsdefinitionsdateien (RDL-Dateien) zugeordnet, die von einem Microsoft SQL Server Reporting Services-Berichtsserver verarbeitet werden. 

Die neuste Version des Berichts-Viewer-Webparts kann außerdem paginierte Berichte warten, die für Power BI-Berichtsserver bereitgestellt werden. Das Webpart funktioniert nicht bei Power BI-Berichten.

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>Gründe für die Wiedereinführung des Berichts-Viewer-Webparts

Das Berichts-Viewer-Webpart war bereits als Bestandteil des Reporting Services-Add-Ins für SharePoint-Produkte verfügbar. Das Webpart war für Berichtsserver im integrierten SharePoint-Modus konzipiert. Die Unterstützung des integrierten SharePoint-Modus wurde nach der Veröffentlichung von SQL Server 2016 eingestellt.

Ab SQL Server 2017 gibt es nur noch einen Installationsmodus für Reporting Services: den **einheitlichen Modus**. Sie könnten alle Typen von Berichten mithilfe eines Seiten-Viewer-Webparts einbetten, der den URL-Parameter *rs:Embed=true* verwendet. Die Funktion zum Einbetten von Berichten in SharePoint-Seiten wurde von Kunden gefordert, und das aktualisierte Berichts-Viewer-Webpart ermöglicht dieses Szenario für paginierte Berichte.

Das Seiten-Viewer-Webpart reicht zwar aus, um einen paginierten Bericht in eine SharePoint-Seite einzubetten, jedoch bietet das aktualisierte Berichts-Viewer-Webpart zusätzliche Funktionen:

* Das Ein-/Ausblenden von bestimmten Symbolleistenschaltflächen
* Das Überschreiben von Berichtsparameterwerten
* Das Verbinden von Filterwebparts mit Berichtsparametern

## <a name="download-the-report-viewer-web-part-solution-package"></a>Das Herunterladen des Projektmappenpakets des Berichts-Viewer-Webparts

Das Berichts-Viewer-Webpart ist im Microsoft Download Center verfügbar.

[Herunterladen des Projektmappenpakets des Berichts-Viewer-Webparts](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

Die aufgelisteten Elemente sind spezifisch für das aktualisierte Berichts-Viewer-Webpart.

* Das Webpart kann nur auf *klassischen* SharePoint-Seiten verwendet werden.
* Das Einbetten von paginierten (RDL-) Berichten wird nur im Berichts-Viewer-Webpart unterstützt. Wenn Sie Power BI-Berichte oder mobile Berichte einbetten möchten, können Sie den URL-Parameter *rs:Embed=true* verwenden.

## <a name="next-steps"></a>Nächste Schritte

Die ersten Schritte mit dem aktualisierten Berichts-Viewer-Webpart werden unter [Bereitstellen des Berichts-Viewer-Webparts auf einer SharePoint-Website](deploy-report-viewer-web-part.md) beschrieben.
