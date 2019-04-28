---
title: Wiederherstellungsoptionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a66aabc9388c85e8d7d1e3df26bc02388347b6a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62736651"
---
# <a name="restore-options"></a>Wiederherstellungsoptionen
  Es gibt viele Möglichkeiten zum Wiederherstellen einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank. Jede dieser Möglichkeiten setzt jedoch voraus, dass Sie sowohl für den Servercomputer als auch für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank über Administratorberechtigungen verfügen. Zum Wiederherstellen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank können Sie das Dialogfeld **Datenbank wiederherstellen** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]öffnen, die entsprechenden Konfigurationsoptionen auswählen und dann die Wiederherstellung vom Dialogfeld aus ausführen. Sie können aber auch mithilfe der in der Datei bereits angegebenen Einstellungen ein Skript erstellen. Das Skript kann gespeichert und immer bei Bedarf ausgeführt werden. Bei dieser Methode wird die Wiederherstellung wie im nächsten Abschnitt beschrieben mithilfe von XMLA abgeschlossen.  
  
## <a name="restoring-databases-using-xmla"></a>Wiederherstellen von Datenbanken mithilfe von XMLA  
 Mit dem XMLA-Befehl Restore kann durch Ausführen einer auf einer ABF-Datei basierenden Wiederherstellung der Wiederherstellungsprozess automatisiert werden. Für den Befehl Restore kann eine Reihe von Eigenschaften festgelegt werden, um Sicherheitsdefinitionen, den Speicherort von Remotepartitionen und das Verschieben von relationalen OLAP-Objekten (ROLAP) anzugeben. Weitere Informationen finden Sie unter [Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla).  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Wiederherstellungsbefehl ausführt, über die Berechtigung zum Lesen von dem für jede Datei angegebenen Sicherungsspeicherort verfügen. Zum Wiederherstellen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank, die nicht auf dem Server installiert ist, muss der Benutzer zusätzlich Mitglied der Serverrolle für die betreffende [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz sein. Zum Überschreiben einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank muss der Benutzer entweder Mitglied der Serverrolle für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit der Berechtigung „Vollzugriff“ (Administrator) für die wiederherzustellende Datenbank sein.  
  
> [!NOTE]  
>  Nach dem Wiederherstellen einer vorhandenen Datenbank verliert der Benutzer, der die Datenbank wiederhergestellt hat, möglicherweise den Zugriff auf diese Datenbank. Dies ist u. U. der Fall, wenn der Benutzer zum Zeitpunkt der Sicherung kein Mitglied der Serverrolle oder der Datenbankrolle mit der Berechtigung "Vollzugriff (Administrator)" war.  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld Datenbank wiederherstellen &#40;Analysis Services – Mehrdimensionale Daten&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](backup-and-restore-of-analysis-services-databases.md)   
 [Restore-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [Sichern, Wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
