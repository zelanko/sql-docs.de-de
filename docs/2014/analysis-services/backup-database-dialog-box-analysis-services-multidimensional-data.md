---
title: Dialog Feld ' Datenbank sichern ' (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Backup.f1
ms.assetid: 7811ce7d-6c37-4189-bfa6-ef36fb4932db
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a99ce67c4b42cc1def10127c8b1862a859d20723
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66064383"
---
# <a name="backup-database-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld Sicherungsdatenbank (Analysis Services – Mehrdimensionale Daten)
  Im Dialogfeld **Datenbank sichern** von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank in einer Sicherungsdatei im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Sicherungsdateiformat (*.abf) sichern.  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Sicherungsbefehl ausführt, über die Berechtigung zum Schreiben in den für jede Datei angegebenen Sicherungsspeicherort verfügen. Dem Benutzer muss zudem eine der folgenden Rollen zugewiesen worden sein: Mitglied einer Serverrolle für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit der Berechtigung „Vollzugriff“ (Administrator) für die wiederherzustellende Datenbank.  
  
 **So zeigen Sie das Dialogfeld Datenbank sichern an**  
  
-   Klicken Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste entweder auf den Ordner **Datenbanken** einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder auf eine Datenbank im **Objekt-Explorer**, und klicken Sie dann auf **Sichern**.  
  
## <a name="options"></a>Optionen  
 **Skript**  
 Erstellt ein Sicherungsskript, das auf den im Dialogfeld aktivierten Optionen basiert. Das Wiederherstellungsskript wird in der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Skriptsprache (ASSL) geschrieben.  
  
 Wenn Sie auf das Symbol **Skript** klicken, wird das Sicherungsskript standardmäßig an ein neues Abfragefenster gesendet.  
  
 Durch Klicken auf den Pfeil neben **Skript** wird ein Menü angezeigt, in dem Sie auswählen können, wohin das Sicherungsskript geschickt werden soll:  
  
-   An ein neues Abfragefenster (Standard)  
  
-   An eine Datei  
  
-   An die Zwischenablage  
  
-   An einen Auftrag  
  
 **Datenbank**  
 Zeigt den Namen der aktuell ausgewählten Datenbank von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] an.  
  
 **Sicherungsdatei**  
 Geben Sie den vollständigen Pfad und Dateinamen der Sicherungsdatei ein, die verwendet werden soll.  
  
 **Durchsuchen**  
 Klicken Sie hier, um das Dialogfeld **Datei speichern unter** anzuzeigen, und wählen Sie Pfad und Dateinamen der Sicherungsdatei aus, die verwendet werden soll. Weitere Informationen zum Dialogfeld **Speichern unter** finden Sie unter [Dialogfeld „Datei speichern unter“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Überschreiben von Dateien zulassen**  
 Wählen Sie diese Option aus, um eine gegebenenfalls vorhandene Sicherungsdatei oder eine Remotesicherungsdatei zu überschreiben.  
  
> [!NOTE]  
>   Wenn diese Option nicht ausgewählt ist und die in einem der Felder **Sicherungsdatei** oder **Remotesicherungsdatei** angegebene Sicherungsdatei vorhanden ist, wird ein Fehler gemeldet.  
  
 **Komprimierung anwenden**  
 Wählen Sie diese Option aus, um den Inhalt der Sicherungsdatei und gegebenenfalls vorhandener Remotesicherungsdateien zu komprimieren.  
  
 **Sicherungsdatei verschlüsseln**  
 Wählen Sie diese Option aus, um die Sicherungsdatei mithilfe des im Feld **Kennwort**bereitgestellten Kennworts zu verschlüsseln.  
  
 **Kennwort**  
 Geben Sie das Kennwort ein, das beim Verschlüsseln der Sicherungsdatei und gegebenenfalls vorhandener Remotesicherungsdateien verwendet werden soll.  
  
> [!NOTE]  
>   Diese Option ist nur bei Auswahl von **Sicherungsdatei verschlüsseln** aktiviert.  
  
 **Kennwort bestätigen**  
 Geben Sie das im Feld **Kennwort** eingegebene Kennwort ein, um das Kennwort für die Sicherungsdatei und für gegebenenfalls vorhandene Remotesicherungsdateien zu bestätigen.  
  
> [!NOTE]  
>   Diese Option ist nur bei Auswahl von **Sicherungsdatei verschlüsseln** aktiviert.  
  
 **Remotepartition(en) sichern**  
 Wählen Sie diese Option aus, um Informationen zum Speicherort sowie die Daten der Remotepartitionen in der Sicherungsdatei zu sichern.  
  
> [!NOTE]  
>  Diese Option ist nur dann aktiviert, wenn für die aktuell ausgewählte [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank Remotepartitionen verwendet werden.  
  
 **Speicherort für Remotepartitionssicherungen**  
 Zeigt den Speicherort der Remotepartitionen an, die der ausgewählten Datenbank zugeordnet sind, sowie die Remotesicherungsdatei, in der die Daten und Metadaten der Remotepartitionen gesichert werden. Folgende Spalten sind verfügbar:  
  
|Column|BESCHREIBUNG|  
|------------|-----------------|  
|**Server**|Zeigt die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] an, die die Remotepartitionen verwaltet.|  
|**Datenbank**|Zeigt die Datenbank von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] an, zu der die Remotepartitionen gehören.|  
|**Partitionsliste**|Zeigt die Liste der Remotepartitionen an, die zu der im Feld **Datenbank**angegebenen Datenbank gehören.|  
|**Remotesicherungsdatei**|Geben Sie den vollständigen Pfad und Dateinamen der Remotesicherungsdatei ein, die verwendet werden soll. Wahlweise können Sie auch auf die Schaltfläche mit den Auslassungspunkten (**...**) klicken, um das Dialogfeld **Datei speichern unter** anzuzeigen und dort den Pfad und Dateinamen der betreffenden Remotesicherungsdatei auszuwählen. Weitere Informationen zum Dialogfeld **Speichern unter** finden Sie unter [Dialogfeld „Datei speichern unter“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
