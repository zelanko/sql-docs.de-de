---
title: Optionen für die Quell Code Verwaltung festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Source_Control.Visual_SourceSafe
- VS.ToolsOptionsPages.Source_Control.General
- VS.ToolsOptionsPages.Source_Control.Environment
helpviewer_keywords:
- source controls [SQL Server Management Studio], options
ms.assetid: b2c6ca00-46f0-4f86-b067-07bae779c147
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5ab6d134177c7861c3a8f92cf767c71c0b56e233
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84929141"
---
# <a name="set-source-control-options"></a>Festlegen von Quellcodeverwaltungsoptionen
  Bevor Sie die Funktionen der in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] integrierten Quellcodeverwaltung nutzen können, sollten Sie die Quellcodeverwaltungsoptionen für die unterschiedlichen Umgebungen konfigurieren, in denen Sie arbeiten.  
  
 Sie konfigurieren die Quell Code Verwaltungs Optionen mithilfe des Dialog Felds **Optionen** , um eine oder mehrere Quell Code Verwaltungs Rollen zu konfigurieren. Eine Rolle besteht aus einer allgemeinen Beschreibung der Einstellung, in der Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] verwenden, und den Quellcodeverwaltungsoptionen, die mit dieser Einstellung verknüpft sind.  
  
 Wenn Sie z. B. ein unabhängiger Datenbankentwickler sind, entstehen in der Regel keine Konflikte mit anderen Benutzern, wenn Dateien ausgecheckt bleiben, nachdem Sie sie einchecken. Durch [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wird also eine Rolle für unabhängige Entwickler definiert. Bei dieser Rolle [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wählt automatisch die Option **Elemente beim Einchecken ausgecheckt bleiben aus** .  
  
 Da Sie Rollen definieren und anpassen können, können Sie mit unterschiedlichen Entwicklungseinstellungen arbeiten, ohne die Quellcodeverwaltung bei jedem Einstellungswechsel vollständig neu konfigurieren zu müssen.  
  
### <a name="to-set-source-control-options"></a>So legen Sie Quellcodeverwaltungsoptionen fest  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** den Eintrag **Quell**Code Verwaltung, und klicken Sie dann auf die Seite **Plug-in-Auswahl** .  
  
     **Aktuelles Quellcodeverwaltungs-Plug-In**  
     Wählen Sie das gewünschte Quellcodeverwaltungsprogramm aus dieser Liste aus. In dieser Liste werden nur die auf diesem Computer installierten Quellcodeverwaltungsclients angezeigt. Wenn auf diesem Computer keine Quellcodeverwaltungsclients installiert sind, enthält die Liste nur den Eintrag Keiner. Wenn Sie Microsoft Source Safe installiert haben, dann werden die folgenden Plug-Ins angezeigt:  
  
    -   Microsoft Visual SourceSafe  
  
    -   Microsoft Visual SourceSafe(Internet)  
  
3.  Legen Sie Anmeldeinformationen für jede Quellcodeverwaltungsrolle fest, die Sie verwenden möchten. Diese Seite ist nur verfügbar, wenn ein Quellcodeverwaltungs-Plug-In installiert ist.  
  
     **Rollenbeschreibung**  
     Wenn Sie eine dieser Rollen auswählen, werden die entsprechenden Quellcodeverwaltungsoptionen automatisch ausgewählt.  
  
    |Role|Beschreibung|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Gibt an, dass die von Visual SourceSafe-Benutzern am häufigsten verwendeten Einstellungen verwendet werden sollen [!INCLUDE[msCoName](../includes/msconame-md.md)] .|  
    |**Unabhängiger Entwickler**|Gibt an, dass Sie unabhängig arbeiten.|  
    |**Benutzerdefiniert**|Gibt an, dass Sie die Einstellungen für eine Rolle geändert haben.|  
  
     **Statusupdate im Hintergrund**  
     Aktualisiert automatisch die Signalsymbole der Quellcodeverwaltung im Projektmappen-Explorer, wenn sich der Status eines Elements ändert. Wenn Sie bei der Ausführung serverintensiver Vorgänge, insbesondere beim Öffnen einer Projektmappe oder eines Projekts aus der Quellcodeverwaltung, Verzögerungen bemerken, kann das Deaktivieren dieses Kontrollkästchen die Leistung verbessern.  
  
     **Login ID**  
     Gibt den Benutzernamen an, der für die Anmeldung beim Quellcode-Verwaltungsanbieter verwendet wird. Wenn Sie von Ihrem Quell Code Verwaltungs Anbieter unterstützt wird, wird dieser Name automatisch im **Anmelde** Dialogfeld ausgefüllt, um den Quell Code Verwaltungs Server zu erreichen. Deaktivieren Sie automatische Benutzeranmeldungen, um diese Option zu aktivieren, indem Sie das Administratorprogramm Ihres Quellcode-Verwaltungsanbieters verwenden. Starten Sie anschließend [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] neu.  
  
     **Erweitert**  
     Zeigt zusätzliche Optionen für das Hinzufügen von Elementen zur Quellcodeverwaltung an. Welche Optionen dies sind, hängt von Ihrem Quellcode-Verwaltungsanbieter ab. Hilfe zu diesen Optionen wird vom Quellcode-Verwaltungsprogramm bereitgestellt.  
  
4.  Wählen Sie die Seite **Umgebung** aus.  
  
5.  Wählen Sie im Feld **Umgebungseinstellungen** für die Quell Code Verwaltung die Rolle aus, für die Sie Quell Code Verwaltungs Optionen festlegen möchten.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wählt automatisch die standardmäßigen Quellcodeverwaltungsoptionen für die Rolle aus, die Sie ausgewählt haben. Wenn Sie eine der Standardoptionen deaktivieren, wird im Feld Quell Code Verwaltungs **Umgebung** die Option **Benutzer** definiert angezeigt, um anzugeben, dass Sie die ursprünglich ausgewählte Rolle angepasst haben.  
  
     **Umgebungseinstellungen für Quellcodeverwaltung**  
     Gibt die Rolle an, die Sie verwenden möchten. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] definiert die folgenden Rollen.  
  
    |Role|Beschreibung|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Gibt an, dass die von Visual SourceSafe-Benutzern am häufigsten verwendeten Einstellungen verwendet werden sollen [!INCLUDE[msCoName](../includes/msconame-md.md)] .|  
    |**Unabhängiger Entwickler**|Gibt an, dass Sie unabhängig arbeiten.|  
    |**Benutzerdefiniert**|Gibt an, dass Sie die Einstellungen für eine Rolle geändert haben.|  
  
     Wenn Sie eine dieser Rollen auswählen, werden die entsprechenden Quellcodeverwaltungsoptionen automatisch ausgewählt.  
  
     **Elemente beim Einchecken ausgecheckt lassen**  
     Gibt an, dass die Elemente für Sie ausgecheckt bleiben, wenn Sie Elemente zum Aktualisieren des Quellcodeverwaltungsspeichers einchecken. Wenn Sie diese Option für einen bestimmten Eincheck Vorgang ändern möchten, klicken Sie im Dialogfeld **Einchecken** auf den Pfeil **Optionen** , und deaktivieren Sie das Kontrollkästchen **ausgecheckt lassen** .  
  
     **Eingecheckte Elemente**  
     Zeigt eine Liste von Optionen an, die angeben, wie sich [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Verhalten soll, wenn Sie versuchen, ein nicht ausgechecktes Element zu bearbeiten. In den folgenden Tabellen werden die verfügbaren Optionen beschrieben.  
  
     **Speichern**  
  
    |Aktion|Beschreibung|  
    |------------|-----------------|  
    |**Aufforderung zum Auschecken**|Zeigt das Dialogfeld **Auschecken** an.|  
    |**Automatisch auschecken**|Checkt das Element aus, ohne das Dialogfeld **Auschecken** anzuzeigen. Dies ist die Standardoption.|  
    |**Speichern unter**|Speichert die Daten in einer neuen Datei.|  
  
     **Bearbeitung läuft**  
  
    |Aktion|Beschreibung|  
    |------------|-----------------|  
    |**Aufforderung zum Auschecken**|Zeigt das Dialogfeld **Auschecken** an.|  
    |**Aufforderung zum exklusiven Auschecken**|Zeigt das Dialogfeld **Auschecken** an.|  
    |**Automatisch auschecken**|Checkt das Element aus, ohne das Dialogfeld **Auschecken** anzuzeigen. Dies ist die Standardoption.|  
    |**Keine Maßnahmen**|Checkt die Datei nicht aus.|  
  
     **Das Bearbeiten von eingecheckten Elementen zulassen**  
     Gibt an, dass eingecheckte Elemente im Speicher bearbeitet werden können. Wenn Sie dieses Kontrollkästchen aktivieren, wird im Dialogfeld " **Auschecken** " eine Schaltfläche " **Bearbeiten** " angezeigt, wenn Sie versuchen, ein eingechecktes Element zu bearbeiten. Wenn Sie auf diese Schaltfläche klicken, können Sie das Element bearbeiten. Wenn Sie das Element zu speichern versuchen, müssen Sie es erst auschecken, oder Sie wählen einen anderen Speicherort aus.  
  
     **Neu starten**  
     Setzt die Einstellungen in den Dialogfeldern zur Bestätigung der Quellcodeverwaltung auf die Standardwerte zurück. Wenn Sie z. b. das Kontrollkästchen **dieses Dialogfeld nicht mehr anzeigen** im Dialogfeld Quell Code Verwaltung aktiviert haben, wird diese Aktion durch Auswählen der Option **Zurücksetzen** rückgängig gemacht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlagen der Quellen Verwaltung](../../2014/database-engine/source-control-basics.md)   
 [Ändern von Quell Code Verwaltungs Verbindungen](../../2014/database-engine/change-source-control-connections.md)   
 [Ausschließen von Dateien aus der Quellcodeverwaltung](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
