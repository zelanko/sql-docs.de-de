---
title: Berichte, Berichtsteile und Berichtsdefinitionen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report definitions
- reports
ms.assetid: 2d746550-f8cc-4e97-8a06-d0f03cffc18d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d22c8c22170ecef301eacd553f15c16091c9a6e7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66105046"
---
# <a name="reports-report-parts-and-report-definitions-report-builder-and-ssrs"></a>Berichte, Berichtsteile und Berichtsdefinitionen (Berichts-Generator und SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet eine Vielzahl von Begriffen zum Beschreiben eines Berichts in verschiedenen Zuständen, darunter Anfangsdefinition, veröffentlichter Bericht und angezeigter Bericht, für den Benutzer angezeigt wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-definition-rdl-files"></a>RDL-Dateien (Berichtsdefinitionsdateien)  
 Bei einer Berichtsdefinition handelt es sich um eine Datei, die Sie in Berichts-Generator oder in Berichts-Designer erstellen. Sie enthält eine vollständige Beschreibung der Datenquellenverbindungen, Abfragen zum Abrufen von Daten, Ausdrücken, Parametern, Bildern, Textfeldern, Tabellen und der übrigen Entwurfszeitelemente, die in einem Bericht enthalten sein können. Obwohl eine Berichtsdefinition komplex sein kann, enthält sie mindestens eine Abfrage sowie andere Berichtsinhalte, Berichtseigenschaften und ein Berichtslayout.  
  
 Berichtsdefinitionen werden zur Laufzeit als verarbeiteter Bericht gerendert. Zur Laufzeit werden die Daten aus der Datenquelle abgerufen und entsprechend den Anweisungen in der Berichtsdefinition formatiert. Eine Berichtsdefinition kann direkt aus Ihrem Computer ausgeführt und lokal gespeichert werden. Sie kann auch auf einem Berichtsserver veröffentlicht werden, damit andere Benutzer sie ebenfalls ausführen können.  
  
 Berichtsdefinitionen werden in einem XML-Format geschrieben, das einer XML-Grammatik entspricht, der so genannten Berichtsdefinitionssprache (RDL, Report Definition Language). RDL beschreibt die XML-Elemente, die sämtliche möglichen Varianten eines Berichts umfassen.  
  
## <a name="client-report-definition-rdlc-files"></a>Clientberichtsdefinitions-Dateien (RDLC)  
 Der Visual Studio-Berichts-Designer erzeugt Clientberichtsdefinitionsdateien (Dateierweiterung .rdlc) zur Verwendung mit dem ReportViewer-Steuerelement. Die RDLC-Dateien können zur Verwendung mit Reporting Services-Berichts-Designer in RDL-Dateien konvertiert werden.  
  
## <a name="report-part-rsc-files"></a>Berichtsteildateien (.rsc)  
 Eine Berichtsteildefinition ist ein XML-Fragment einer Berichtsdefinitionsdatei. Sie erstellen Berichtsteile, indem Sie eine Berichtsdefinition erstellen und dann Berichtselemente im Bericht auswählen, die als Berichtsteile getrennt veröffentlicht werden sollen. Berichtsteile umfassen Datenbereiche, Rechtecke und enthaltene Elemente sowie Bilder. Sie können einen Berichtsteil mit seinen abhängigen Datasets und freigegebenen Datenquellenverweisen speichern, damit er in anderen Berichten wiederverwendet werden kann.  
  
 [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
## <a name="published-reports"></a>Veröffentlichte Berichte  
 Nachdem Sie eine RDL-Datei erstellt haben, können Sie sie lokal oder in einem persönlichen Ordner (wie dem Ordner Meine Berichte) auf dem Berichtsserver speichern. Wenn der Bericht zur Anzeige durch andere Benutzer bereit ist, können Sie ihn veröffentlichen, indem Sie ihn aus Berichts-Generator in einem öffentlichen Ordner auf dem Berichtsserver speichern, über den Berichts-Manager hochladen oder eine Berichtsprojektmappe aus Berichts-Designer bereitstellen. Ein veröffentlichter Bericht ist ein Element, das in einer Berichtsserver-Datenbank gespeichert und auf einem Berichtsserver oder einer SharePoint-Website verwaltet wird.  
  
 Ein veröffentlichter Bericht wird über Rollenzuweisungen gesichert, die das rollenbasierte Sicherheitsmodell von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwenden. Der Zugriff auf veröffentlichte Berichte erfolgt über URLs, SharePoint-Webparts oder den Berichts-Manager. Sie können auch zu den Berichten navigieren und sie in Berichts-Generator öffnen.  
  
### <a name="report-snapshots"></a>Berichtsmomentaufnahmen  
 Ein Bericht kann auch als Momentaufnahme veröffentlicht werden, die sowohl Layoutinformationen als auch die Daten der ersten Berichtsausführung enthält. Berichtsmomentaufnahmen werden in keinem speziellen Renderingformat gespeichert. Stattdessen werden Berichtsmomentaufnahmen erst dann in einem endgültigen Anzeigeformat (wie HTML) gerendert, wenn sie von einem Benutzer oder einer Anwendung angefordert werden. Weitere Informationen finden Sie unter [Suchen und Anzeigen von Berichten in Berichts-Manager (Berichts-Generator und SSRS)](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).  
  
## <a name="rendered-reports"></a>Gerenderte Berichte  
 Ein gerenderter Bericht ist ein vollständig verarbeiteter Bericht, der sowohl Daten als auch Layoutinformationen in einem anzeigbaren Format (beispielsweise HTML) enthält. Ein Bericht kann erst dann angezeigt werden, nachdem er in ein Ausgabeformat gerendert wurde. Führen Sie zum Rendern von Berichten einen der folgenden Schritte durch:  
  
-   Erstellen oder öffnen Sie einen Bericht in Berichts-Generator oder Berichts-Designer, und führen Sie ihn aus.  
  
-   Suchen Sie einen Bericht im Berichts-Manager, und führen Sie ihn aus.  
  
-   Suchen Sie auf einer in einen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver integrierten SharePoint-Website nach einem Bericht, und führen Sie ihn aus.  
  
-   Abonnieren Sie einen Bericht, der in einem von Ihnen angegebenen Ausgabeformat an einen E-Mail-Posteingang oder eine Dateifreigabe übermittelt wird.  
  
 Das Standardrenderingformat für Berichte ist HTML 4.0. Außer in HTML können Berichte in einer Vielzahl von Dateiformaten gerendert werden, z. B. Excel, Word, XML, PDF, TIFF und CSV. Wie veröffentlichte Berichte können auch gerenderte Berichte nicht bearbeitet oder wieder auf einem Berichtsserver gespeichert werden. Weitere Informationen finden Sie unter [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Berichterstellungskonzepte &#40;Berichts-Generator und SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Berichts-Generator in SQLServer 2014](../report-builder/report-builder-in-sql-server-2016.md)   
 [Installieren und Deinstallieren von Berichts-Generator-Unterstützung](../install-uninstall-and-report-builder-support.md)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS)](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
