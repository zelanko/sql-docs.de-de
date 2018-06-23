---
title: Allgemein (im Dialogfeld Datenbank wiederherstellen) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.restoredbdialog.f1
ms.assetid: 319e7ef5-c9c7-4e50-8690-02a90aed006f
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4969ceb840f6c3d80b4d0854d582e695c109806b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150694"
---
# <a name="general-restore-database-dialog-box-analysis-services---multidimensional-data"></a>Allgemein (Dialogfeld Datenbank wiederherstellen) (Analysis Services – Mehrdimensionale Daten)
  Auf der Seite **Allgemein** des Dialogfelds **Datenbank wiederherstellen** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die Sicherungsdatei und die allgemeinen Einstellungen angeben, die beim Wiederherstellen einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank verwendet werden sollen.  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Wiederherstellungsbefehl ausführt, über die Berechtigung zum Lesen von dem für jede Datei angegebenen Sicherungsspeicherort verfügen. Zum Wiederherstellen einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank, die nicht auf dem Server installiert ist, muss der Benutzer zusätzlich Mitglied der Serverrolle für die betreffende [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz sein. Zum Überschreiben einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank muss der Benutzer entweder Mitglied der Serverrolle für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit den Berechtigungen "Vollzugriff" (Administrator) für die wiederherzustellende Datenbank sein.  
  
> [!NOTE]  
>  Nach dem Wiederherstellen einer vorhandenen Datenbank verliert der Benutzer, der die Datenbank wiederhergestellt hat, möglicherweise den Zugriff auf diese Datenbank. Dies ist u. U. der Fall, wenn der Benutzer zum Zeitpunkt der Sicherung kein Mitglied der Serverrolle oder der Datenbankrolle mit der Berechtigung "Vollzugriff (Administrator)" war.  
  
 **Zum Anzeigen der Seite "Allgemein" im Dialogfeld Datenbank wiederherstellen**  
  
-   Klicken Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste entweder auf den Ordner **Datenbanken** einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder auf eine Datenbank im **Objekt-Explorer**, klicken Sie auf **Wiederherstellen**, und unter **Seite auswählen**klicken Sie anschließend auf **Allgemein**.  
  
## <a name="options"></a>Tastatur  
 **Skript**  
 Erstellt ein Wiederherstellungsskript, das auf den im Dialogfeld aktivierten Optionen basiert. Das Wiederherstellungsskript wird in der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Skriptsprache (ASSL) geschrieben.  
  
 Wenn Sie auf das Symbol **Skript** klicken, wird das Wiederherstellungsskript standardmäßig an ein neues Abfragefenster gesendet.  
  
 Durch Klicken auf den Pfeil neben **Skript** wird ein Menü angezeigt, in dem Sie auswählen können, wohin das Wiederherstellungsskript geschickt werden soll:  
  
-   An ein neues Abfragefenster (Standard)  
  
-   An eine Datei  
  
-   An die Zwischenablage  
  
-   An einen Auftrag  
  
 **Stellen Sie die Datenbank wieder her.**  
 Wählen Sie die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank aus, die wiederhergestellt werden soll.  
  
 **Aus Sicherungsdatei**  
 Wählen Sie die Sicherungsdatei aus, aus der die ausgewählte [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank wiederhergestellt werden soll.  
  
 **Durchsuchen**  
 Klicken Sie hier, um das Dialogfeld **Datenbankdateien suchen** anzuzeigen, und wählen Sie Pfad und Dateinamen der Sicherungsdatei aus, die verwendet werden soll. Weitere Informationen zum Dialogfeld **Datenbankdateien suchen** finden Sie unter [Dialogfeld „Datenbankdateien suchen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Überschreiben der Datenbank zulassen**  
 Wählen Sie diese Option aus, damit beim Wiederherstellen durch [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die vorhandenen Objekte in der ausgewählten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank mit dem Inhalt der ausgewählten Sicherungsdatei überschrieben werden können.  
  
 **Sicherheitsinformationen einschließen**  
 Wählen Sie diese Option aus, um alle Sicherheitsinformationen in die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank zu kopieren, die in der Sicherungsdatei gespeichert sind.  
  
 Wenn diese Option ausgewählt ist, können Sie den Umfang der Sicherheitsinformationen aus der dann verfügbaren Dropdownliste auswählen. Die folgenden Optionen stehen zur Verfügung:  
  
|Option|Description|  
|------------|-----------------|  
|**Kopieren Sie alle**|Stellt die Datenbankrollen und die den Rollen zugeordneten Benutzerkonten wieder her, die in der Sicherungsdatei enthalten sind.|  
|**Mitgliedschaft auslassen**|Stellt die Datenbankrollen wieder her, die in der Sicherungsdatei enthalten sind, nicht aber die den Rollen zugeordneten Benutzerkonten.|  
  
 **Kennwort**  
 Wenn die Sicherungsdatei verschlüsselt ist, geben Sie das Kennwort ein, dass zur Verschlüsselung der Sicherungsdatei verwendet wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld Datenbank wiederherstellen &#40;Analysis Services – mehrdimensionale Daten&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Partitionen &#40;Dialogfeld Datenbank wiederherstellen&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  