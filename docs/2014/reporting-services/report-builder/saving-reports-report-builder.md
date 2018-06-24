---
title: Speichern von Berichten (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59ddc4b8-9517-4d3f-9c88-a07e9907cecb
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e5f14bd16fa44247508ef04bf68d2d02c0503394
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059987"
---
# <a name="saving-reports-report-builder"></a>Speichern von Berichten (Berichts-Generator)
  Im Berichts-Generator können Sie einen Bericht auf einem Berichtsserver, in einer SharePoint-Bibliothek, in einer Dateifreigabe, für die Sie Schreibrechte haben, oder auf dem Computer speichern. Sie können einen Bericht am gleichen Speicherort speichern, an dem Sie ihn geöffnet haben, oder Sie können ihn an einem anderen Speicherort oder unter einem neuen Namen am gleichen Speicherort oder einem anderen Speicherort speichern. Standardmäßig wird ein Bericht an dem Speicherort erneut gespeichert, an dem er geöffnet wurde. Wenn Sie den Bericht speichern, speichern Sie in Wirklichkeit die Berichtsdefinition, in der das Berichtslayout beschrieben wird. Die Daten werden nicht gespeichert. Bei jeder Ausführung des Berichts werden die Berichtsdaten aktualisiert. Sie sind dann wahrscheinlich anders als bei der letzten Ausführung des Berichts.  
  
 Wenn Sie den Bericht zu einem anderen Format speichern oder die Berichtsdefinition mit den Daten speichern möchten, verwenden Sie eine der folgenden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen:  
  
-   Exportieren Sie einen gerenderten Bericht in ein anderes Dateiformat, z. B. in durch Trennzeichen getrennte Dateien (CSV) oder Excel-Arbeitsmappen, und speichern Sie den Bericht in diesem Format. Sie können auch Datenfeeds von Berichten generieren und die Berichtsdaten speichern.  
  
-   Erstellen Sie Berichtsabonnements, um Berichte an eine Dateifreigabe zu übermitteln und dort zu speichern.  
  
-   Speichern Sie Versionen von gerenderten Berichten mithilfe des Berichtsverlaufs als Verlaufskopie.  
  
 Weitere Informationen zum Anzeigen und Verwalten von Berichten direkt auf dem Berichtsserver finden Sie unter [Suchen, Anzeigen und Verwalten von Berichten &#40;Berichts-Generator und SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) und [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../report-server/reporting-services-report-server-native-mode.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-[Onlinedokumentation](http://go.microsoft.com/fwlink/?LinkId=154888) auf msdn.microsoft.com.  
  
##  <a name="SavingReportDefinitions"></a> Speichern von Berichtsdefinitionen  
 Auch wenn Sie Berichte auf dem Computer speichern können, hat das Speichern der Berichte auf einem Berichtsserver viele Vorteile.  
  
 Das Speichern eines Berichts auf einem Berichtsserver hat die folgenden Vorteile:  
  
-   Berichte sind für andere Personen verfügbar, wenn diese über die Zugriffsberechtigung auf den Ordner verfügen, in dem Sie den Bericht gespeichert haben.  
  
-   Berichte können über den Berichts-Manager verwaltet und angezeigt werden.  
  
-   Berichtsressourcen wie Datenquellen, Bilder und Unterberichte werden für einen einfacheren Zugriff an einem Speicherort gespeichert.  
  
-   Berichte können über Abonnements an andere Personen übermittelt werden.  
  
-   Berichte werden in der Berichtsserverdatenbank sicher gespeichert.  
  
-   Die Ausführung von Berichten kann protokolliert werden. Damit stehen Leistungs- und Überwachungsinformationen zur Verfügung.  
  
 Das Speichern eines Berichts auf einem Berichtsserver wird auch als Veröffentlichen eines Berichts bezeichnet. Wenn Sie einen Bericht speichern, speichern Sie nur die Berichtsdefinition. Bei jeder Ausführung des Berichts werden die Berichtsdaten aktualisiert. Sie sind dann wahrscheinlich anders als bei der letzten Ausführung des Berichts. Wenn Sie die Berichtsdefinition zusammen mit den Daten speichern möchten, sollten Sie dazu die Funktion für den Berichtsverlauf verwenden. Mit dieser Funktion können Sie eine Kopie des Berichts mit den darin enthaltenen Daten speichern.  
  

  
##  <a name="ExportingAndSavingReports"></a> Exportieren und Speichern von Berichten  
 Falls Sie nur wenige Berichte archivieren müssen, sollten Sie einen Bericht exportieren und als Datei speichern. Nachdem Sie einen Bericht in eine Anwendung exportiert haben (z. B. PDF oder Excel), können Sie ihn als Datei speichern und in einem geschützten freigegebenen Verzeichnis im Netzwerk platzieren. Oder Sie laden eine gespeicherte PDF- oder Excel-Datei als Ressourcenelement hoch, falls Sie alle Kopien eines Berichts unabhängig vom Format in der Berichtsserver-Datenbank speichern möchten. Weitere Informationen zum Exportieren eines Berichts finden Sie unter [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41; ](export-reports-report-builder-and-ssrs.md) und [Hochladen einer Datei oder eines Berichts &#40;Berichts-Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).  
  

  
##  <a name="UsingFileShareDelivery"></a> Verwenden der Dateifreigabeübermittlung  
 Falls Sie viele Berichte archivieren müssen, erstellen Sie ein Abonnement, das den Bericht direkt an das Dateisystem übermittelt. Bei dieser Vorgehensweise müssen Sie für jeden Bericht ein Abonnement erstellen, einen freigegebenen Ordner zum Speichern der Berichte auswählen und einen Zeitplan definieren, der bestimmt, wann die Datei erstellt wird. Sobald Sie ein Abonnement definiert haben, kann der Berichtsserver mithilfe des bereitgestellten Zeitplanes den Bericht unbeaufsichtigt ausführen und Berichtsdateien zum Archiv hinzufügen. Darüber hinaus können Sie Zeitpläne für die einmalige Verwendung erstellen, falls Sie Berichte gelegentlich archivieren möchten. Weitere Informationen über Abonnements und die Dateifreigabeübermittlung finden Sie unter "Dateiübermittlung in Reporting Services" in der [Reporting Services-Dokumentation](http://go.microsoft.com/fwlink/?linkid=121312) in der SQL Server-Onlinedokumentation.  
  

  
##  <a name="UsingReportHistory"></a> Verwenden des Berichtsverlaufs  
 Mit der Funktion zum Berichtsverlauf können ebenfalls Verlaufskopien erstellt werden. Anschließend können Sie die Berichtsserver-Datenbank sichern und die Sicherungskopie für die spätere Verwendung an einem sicheren Ort aufbewahren. Alle Berichtsverläufe (zusammen mit Berichten, freigegebenen Datenquellenelementen, Ordnern, Abonnements und freigegebenen Zeitplänen) werden in der Berichtsserver-Datenbank gespeichert. Sie können eine Sicherungskopie erstellen, um eine permanente Kopie des Berichtsverlaufs und der Metadaten zu verwalten, wie z. B. Abonnementinformationen, die die Empfänger eines Berichts bezeichnen. Weitere Informationen finden Sie unter "Verwalten des Berichtsverlaufs" in der [Reporting Services-Dokumentation](http://go.microsoft.com/fwlink/?linkid=121312) in der SQL Server-Onlinedokumentation.  
  

  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
  
-   [Speichern von Berichten auf einem Berichtsserver &#40;Berichts-Generator&#41;](save-reports-to-a-report-server-report-builder.md)  
  
-   [Speichern eines Berichts in einer SharePoint-Bibliothek &#40;Berichts-Generator&#41;](save-a-report-to-a-sharepoint-library-report-builder.md)  
  
-   [Speichern von Berichten auf Ihrem Computer &#40;Berichts-Generator&#41;](../save-reports-to-your-computer-report-builder.md)  
  

  
## <a name="see-also"></a>Siehe auch  
 [Berichte, Berichtsteile und Berichtsdefinitionen &#40;Berichts-Generator und SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Installieren, deinstallieren und Berichts-Generator-Unterstützung](../install-uninstall-and-report-builder-support.md)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS)](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Drucken von Berichten (Berichts-Generator und SSRS)](print-reports-report-builder-and-ssrs.md)  
  
  