---
title: Festlegen von Quellcodeverwaltungsoptionen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Source_Control.Visual_SourceSafe
- VS.ToolsOptionsPages.Source_Control.General
- VS.ToolsOptionsPages.Source_Control.Environment
helpviewer_keywords:
- source controls [SQL Server Management Studio], options
ms.assetid: b2c6ca00-46f0-4f86-b067-07bae779c147
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 30c24ccdc17888de4b5ff8c93e76c00beb2986eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059203"
---
# <a name="set-source-control-options"></a>Festlegen von Quellcodeverwaltungsoptionen
  Bevor Sie die Funktionen der in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] integrierten Quellcodeverwaltung nutzen können, sollten Sie die Quellcodeverwaltungsoptionen für die unterschiedlichen Umgebungen konfigurieren, in denen Sie arbeiten.  
  
 Sie konfigurieren Quellcodeverwaltungsoptionen mithilfe der **Optionen** (Dialogfeld), um eine oder mehrere Quellcodeverwaltungsrollen konfigurieren. Eine Rolle besteht aus einer allgemeinen Beschreibung der Einstellung, in der Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] verwenden, und den Quellcodeverwaltungsoptionen, die mit dieser Einstellung verknüpft sind.  
  
 Wenn Sie z. B. ein unabhängiger Datenbankentwickler sind, entstehen in der Regel keine Konflikte mit anderen Benutzern, wenn Dateien ausgecheckt bleiben, nachdem Sie sie einchecken. Durch [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wird also eine Rolle für unabhängige Entwickler definiert. Für diese Rolle [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wählt automatisch die **Elemente beim Einchecken ausgecheckt lassen** Option.  
  
 Da Sie Rollen definieren und anpassen können, können Sie mit unterschiedlichen Entwicklungseinstellungen arbeiten, ohne die Quellcodeverwaltung bei jedem Einstellungswechsel vollständig neu konfigurieren zu müssen.  
  
### <a name="to-set-source-control-options"></a>So legen Sie Quellcodeverwaltungsoptionen fest  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld erweitern Sie **Quellcodeverwaltung**, und klicken Sie dann auf die **Plug-in-Auswahl** Seite.  
  
     **Aktuelles Quellcodeverwaltungs-Plug-in**  
     Wählen Sie das gewünschte Quellcodeverwaltungsprogramm aus dieser Liste aus. In dieser Liste werden nur die auf diesem Computer installierten Quellcodeverwaltungsclients angezeigt. Wenn auf diesem Computer keine Quellcodeverwaltungsclients installiert sind, enthält die Liste nur den Eintrag Keiner. Wenn Sie Microsoft Source Safe installiert haben, dann werden die folgenden Plug-Ins angezeigt:  
  
    -   Microsoft Visual SourceSafe  
  
    -   Microsoft Visual SourceSafe(Internet)  
  
3.  Legen Sie Anmeldeinformationen für jede Quellcodeverwaltungsrolle fest, die Sie verwenden möchten. Diese Seite ist nur verfügbar, wenn ein Quellcodeverwaltungs-Plug-In installiert ist.  
  
     **Rollenbeschreibung**  
     Wenn Sie eine dieser Rollen auswählen, werden die entsprechenden Quellcodeverwaltungsoptionen automatisch ausgewählt.  
  
    |-Rolle|Description|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Gibt an, dass Sie die am häufigsten verwendeten Einstellungen verwenden möchten [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe-Benutzern.|  
    |**Unabhängiger Entwickler**|Gibt an, dass Sie unabhängig arbeiten.|  
    |**Custom**|Gibt an, dass Sie die Einstellungen für eine Rolle geändert haben.|  
  
     **StatusUpdate im Hintergrund**  
     Aktualisiert automatisch die Signalsymbole der Quellcodeverwaltung im Projektmappen-Explorer, wenn sich der Status eines Elements ändert. Wenn Sie bei der Ausführung serverintensiver Vorgänge, insbesondere beim Öffnen einer Projektmappe oder eines Projekts aus der Quellcodeverwaltung, Verzögerungen bemerken, kann das Deaktivieren dieses Kontrollkästchen die Leistung verbessern.  
  
     **Login ID**  
     Gibt den Benutzernamen an, der für die Anmeldung beim Quellcode-Verwaltungsanbieter verwendet wird. Wenn vom Quellcodeverwaltungsanbieter unterstützt wird, diesen Namen wird ausgefüllt, automatisch in die **Anmeldung** (Dialogfeld), um Ihren Quellcode-Verwaltungsserver zu erreichen. Deaktivieren Sie automatische Benutzeranmeldungen, um diese Option zu aktivieren, indem Sie das Administratorprogramm Ihres Quellcode-Verwaltungsanbieters verwenden. Starten Sie anschließend [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] neu.  
  
     **Erweitert:**  
     Zeigt zusätzliche Optionen für das Hinzufügen von Elementen zur Quellcodeverwaltung an. Welche Optionen dies sind, hängt von Ihrem Quellcode-Verwaltungsanbieter ab. Hilfe zu diesen Optionen wird vom Quellcode-Verwaltungsprogramm bereitgestellt.  
  
4.  Wählen Sie die **Umgebung** Seite.  
  
5.  In der **Umgebungseinstellungen für Quellcodeverwaltung** Feld, wählen Sie die Rolle auf dem Sie die Quellcodeverwaltungsoptionen festlegen möchten.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wählt automatisch die standardmäßigen Quellcodeverwaltungsoptionen für die Rolle aus, die Sie ausgewählt haben. Wenn Sie eine der Standardoptionen, deaktivieren Sie die **Umgebungseinstellungen für Quellcodeverwaltung** Feld zeigt die **benutzerdefinierte** Option, um anzugeben, dass Sie die ursprünglich ausgewählte Rolle angepasst haben.  
  
     **Umgebungseinstellungen für Quellcodeverwaltung**  
     Gibt die Rolle an, die Sie verwenden möchten. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] definiert die folgenden Rollen.  
  
    |-Rolle|Description|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Gibt an, dass Sie die am häufigsten verwendeten Einstellungen verwenden möchten [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe-Benutzern.|  
    |**Unabhängiger Entwickler**|Gibt an, dass Sie unabhängig arbeiten.|  
    |**Custom**|Gibt an, dass Sie die Einstellungen für eine Rolle geändert haben.|  
  
     Wenn Sie eine dieser Rollen auswählen, werden die entsprechenden Quellcodeverwaltungsoptionen automatisch ausgewählt.  
  
     **Lassen Sie Elemente beim Einchecken ausgecheckt**  
     Gibt an, dass die Elemente für Sie ausgecheckt bleiben, wenn Sie Elemente zum Aktualisieren des Quellcodeverwaltungsspeichers einchecken. Wenn Sie diese Option für einen bestimmten Eincheckvorgang ändern möchten, klicken Sie auf die **Optionen** Pfeil in der **Einchecken** (Dialogfeld), und deaktivieren Sie die **beibehalten *** ausgecheckt** Kontrollkästchen.  
  
     **Eingecheckte Elemente**  
     Zeigt eine Liste der Optionen an, durch die das Verhalten von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] angegeben wird, wenn Sie ein nicht ausgechecktes Element zu bearbeiten versuchen. In den folgenden Tabellen werden die verfügbaren Optionen beschrieben.  
  
     **Speichern**  
  
    |Aktion|Description|  
    |------------|-----------------|  
    |**Aufforderung zum Auschecken**|Zeigt die **Auschecken** (Dialogfeld).|  
    |**Automatisch auschecken**|Checkt das Element ohne Anzeige der **Auschecken** (Dialogfeld). Diese Option ist die Standardeinstellung.|  
    |**Dateityp**|Speichert die Daten in einer neuen Datei.|  
  
     **Bearbeiten**  
  
    |Aktion|Description|  
    |------------|-----------------|  
    |**Aufforderung zum Auschecken**|Zeigt die **Auschecken** (Dialogfeld).|  
    |**Aufforderung zum exklusiven Auschecken**|Zeigt die **Auschecken** (Dialogfeld).|  
    |**Automatisch auschecken**|Checkt das Element ohne Anzeige der **Auschecken** (Dialogfeld). Diese Option ist die Standardeinstellung.|  
    |**Nichts Unternehmen**|Checkt die Datei nicht aus.|  
  
     **Können Sie eingecheckte Elemente bearbeitet werden**  
     Gibt an, dass eingecheckte Elemente im Speicher bearbeitet werden können. Wenn Sie dieses Kontrollkästchen aktivieren, eine **bearbeiten** Schaltfläche wird angezeigt, der **Auschecken** (Dialogfeld), wenn Sie versuchen, ein eingechecktes Element zu bearbeiten. Wenn Sie auf diese Schaltfläche klicken, können Sie das Element bearbeiten. Wenn Sie das Element zu speichern versuchen, müssen Sie es erst auschecken, oder Sie wählen einen anderen Speicherort aus.  
  
     **Zurücksetzen**  
     Setzt die Einstellungen in den Dialogfeldern zur Bestätigung der Quellcodeverwaltung auf die Standardwerte zurück. Z. B., wenn Sie ausgewählt haben die **dieses Dialogfeld nicht erneut anzeigen** Kontrollkästchen in einem Dialogfeld der quellcodeverwaltung, Auswählen der **zurücksetzen** Option umkehrt mit dieser Aktion.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen zur Quellcodeverwaltung](../../2014/database-engine/source-control-basics.md)   
 [Ändern von Quellcodeverwaltungsverbindungen](../../2014/database-engine/change-source-control-connections.md)   
 [Ausschließen von Dateien aus der Quellcodeverwaltung](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  