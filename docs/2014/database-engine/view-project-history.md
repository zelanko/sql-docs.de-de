---
title: Anzeigen der Projektversionsgeschichte | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- viewing project history
- version control services [SQL Server], project history
- projects [SQL Server Management Studio], historical information
- historical information [SQL Server], projects
ms.assetid: be0ea2ac-4a35-429c-9c9e-4001ea9035a4
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d99c3a27a74d41efc895489a8690d735dadd3b4f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150953"
---
# <a name="view-project-history"></a>Anzeigen der Projektversionsgeschichte
  Der Versionsverlauf eines [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS)-Projekts enthält eine Liste aller Aktionen, die für die einzelnen Projektdateien ausgeführt wurden, einschließlich Erstellen, Hinzufügen, Löschen und Wiederherstellen.  
  
> [!NOTE]  
>  Ein Visual SourceSafe-Projekt wird häufig als Serverordner der Quellcodeverwaltung bezeichnet. Dabei handelt es sich um den Speicherort der Serverversion einer Datei unter Quellcodeverwaltung auf dem Server.  
  
 Mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die Versionsgeschichte des Visual SourceSafe-Projekts untersuchen, zu dem die zurzeit geladene Projektmappe gehört. Basierend auf den Informationen, die als Teil der Projektversionsgeschichte angezeigt werden, können Sie lokale Kopien von Dateiversionen abrufen, gelöschte Versionen wiederherstellen oder eine Dateiversion in mehreren Projekten freigeben.  
  
### <a name="to-view-the-history-of-a-vss-project"></a>So zeigen Sie die Versionsgeschichte eines VSS-Projekts an  
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2.  Auf der **Datei** Sie im Menü **Quellcodeverwaltung** , und klicken Sie auf **Verlauf anzeigen**.  
  
3.  In der **Verlauf der** \<Projekt > Dialogfeld Feld, eine der folgenden Aktionen ausführen:  
  
    -   Zeigen Sie für eine ausgewählte Datei die Kopie des Quellcodeverwaltungssystems an.  
  
    -   Zeigen Sie weitere Informationen zu einer ausgewählten Datei an.  
  
    -   Rufen Sie eine ausgewählte Datei auf den lokalen Datenträger ab.  
  
    -   Checken Sie eine ausgewählte Datei aus.  
  
    -   Geben Sie eine ausgewählte Datei in zwei Projekten unter Quellcodeverwaltung frei.  
  
    -   Exportieren Sie den Versionsgeschichtebericht an einen Drucker, in eine Datei oder in die Zwischenablage.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen und Abrufen von Versionsinformationen](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Anzeigen des Dateistatus](../../2014/database-engine/view-file-status.md)   
 [Abrufen von Dateien](../../2014/database-engine/retrieve-files.md)   
 [Vergleichen von Dateien](../../2014/database-engine/compare-files.md)  
  
  