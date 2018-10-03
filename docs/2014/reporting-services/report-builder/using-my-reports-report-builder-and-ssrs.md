---
title: Verwenden von Meine Berichte (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9ab1c8c07ed176632f98ed19251d616633480436
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48179030"
---
# <a name="using-my-reports-report-builder-and-ssrs"></a>Verwenden von Meine Berichte (Berichts-Generator und SSRS)
  Auf einem Berichtsserver, der im einheitlichen Modus konfiguriert ist, ist der Ordner Meine Berichte ein persönlicher Arbeitsbereich, in dem Sie Ihre eigenen Berichte speichern und verwenden können. Andere Berichtsserverordner sind öffentliche Ordner, für die Benutzer in der Regel erweiterte Berechtigungen zum Hinzufügen oder Ändern von Ordnerinhalten benötigen. Demgegenüber ist der Ordner Meine Berichte ein vom Benutzer verwalteter Arbeitsbereich. Mit personalisierten Einstellungen können Sie Berichte und Ordner hinzufügen oder entfernen und verknüpfte Berichte speichern.  
  
 Vom Prinzip her ist der Ordner Meine Berichte mit dem Ordner Meine Dateien des Windows-Dateisystems zu vergleichen. Zwar gibt es für jeden Benutzer einen Ordner Meine Berichte, jeder Benutzer greift jedoch auf einen anderen Ordner zu. Mit Ausnahme der Berichtsserveradministratoren haben andere Benutzer keinen Zugriff auf Ihren Ordner Meine Berichte.  
  
 Die Funktion Meine Berichte ist optional und kann von einem Berichtsserveradministrator deaktiviert werden. Wenn die Funktion aktiviert ist, wird ein Ordner Meine Berichte im Ordner Home angezeigt, den Sie mithilfe des Berichts-Managers oder einem Webbrowser öffnen können. Weitere Informationen finden Sie unter [Suchen und Anzeigen von Berichten in Berichts-Manager (Berichts-Generator und SSRS)](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).  
  
 Auf einem Berichtsserver, der im integrierten SharePoint-Modus konfiguriert ist, gibt es kein Äquivalent für den Ordner Meine Berichte. Weitere Informationen finden Sie unter [suchen, anzeigen und Verwalten von Berichten &#40;Berichts-Generator und SSRS &#41; ](finding-viewing-and-managing-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="ways-to-use-my-reports"></a>Verwendungsmöglichkeiten von Meine Berichte  
 Meine Berichte ist bis zum Hinzufügen von Berichten, Ordnern und sonstigen Elementen leer. Es gibt folgende Möglichkeiten, um Inhalt zu Meine Berichte hinzuzufügen.  
  
-   Erstellen Sie einen persönlichen verknüpften Bericht, und speichern Sie ihn in Meine Berichte. Nicht alle Berichte können verknüpft werden. Weitere Informationen finden Sie unter [Erstellen eines verknüpften Berichts](../reports/create-a-linked-report.md).  
  
-   Laden Sie eine Berichtsdefinitionsdatei (RDL), Berichtsmodelldatei (SMDL) oder andere Dateien aus dem Dateisystem hoch. Sie können zwar jede beliebige Datei hochladen, der Berichtsserver verarbeitet jedoch nur Berichtsdateien mit der Dateierweiterung .rdl oder.smdl. Weitere Informationen finden Sie unter „Berichtsdefinitionen“ in der [Reporting Services-Dokumentation](http://go.microsoft.com/fwlink/?linkid=121312) in der SQL Server-Onlinedokumentation und unter [Hochladen einer Datei oder eines Berichts (Berichts-Manager)](../reports/upload-a-file-or-report-report-manager.md).  
  
-   Erstellen und veröffentlichen Sie Ihre eigenen Berichte in Meine Berichte. Weitere Informationen finden Sie unter [Berichtsentwurfsansicht (Berichts-Generator)](report-design-view-report-builder.md).  
  
 Gewöhnlich können Sie mit Berechtigungen für Meine Berichte den Ordner selbst verwalten. Der Berichtsserveradministrator legt letztlich fest, welche Aufgaben die Benutzer ausführen können. Wenn Sie durch unzureichende Berechtigungen Probleme beim Verwenden von Meine Berichte haben, wenden Sie sich an den Berichtsserveradministrator.  
  
## <a name="searching-my-reports"></a>Durchsuchen von Meine Berichte  
 Beim Durchsuchen einer Berichtsserver-Datenbank werden die Inhalte des Ordners Meine Berichte in die Suche einbezogen, während die Inhalte der Ordner Meine Berichte von anderen Benutzern ausgeschlossen werden. In den Suchergebnissen werden nur die Berichte aufgeführt, auf die Sie Zugriff haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS )](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
