---
title: Ausschließen von Dateien aus der Quell Code Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9fb3c5ccb4fcaad062236eec6d04f995557dc2b8
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933089"
---
# <a name="exclude-files-from-source-control"></a>Ausschließen von Dateien aus der Quellcodeverwaltung
  Wenn die Projekt Mappe, an der Sie arbeiten, Dateien enthält, für die keine Quell Code Verwaltungsdienste erforderlich sind, können Sie den Befehl **aus Quell** Code Verwaltung ausschließen verwenden, um die Datei aus der Quell Code Verwaltung auszuschließen. Dabei bleibt die Datei zwar in der [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe-Datenbank, wird aber nicht mehr mit dem Projekt ein- oder ausgecheckt.  
  
 Sie sollten den Befehl **aus Quell** Code Verwaltung ausschließen nur für generierte Dateien verwenden. Eine generierte Datei kann auf [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Grundlage des Inhalts einer anderen Datei in der Projekt Mappe vollständig neu erstellt werden.  
  
### <a name="to-exclude-a-file-from-source-control"></a>So schließen Sie eine Datei aus der Quellcodeverwaltung aus  
  
1.  Wählen Sie die auszuschließende Datei im Projektmappen-Explorer aus.  
  
2.  Zeigen Sie im Menü **Datei** auf **Quell**Code Verwaltung, und klicken Sie **Exclude** dann auf *\<file name>* **aus Quell**Code Verwaltung ausschließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlagen der Quellen Verwaltung](../../2014/database-engine/source-control-basics.md)   
 [Optionen für die Quell Code Verwaltung festlegen](../../2014/database-engine/set-source-control-options.md)   
 [Ändern von Quellcodeverwaltungsverbindungen](../../2014/database-engine/change-source-control-connections.md)  
  
  
