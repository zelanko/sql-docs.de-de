---
title: Projekte zur Quellcodeverwaltung hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c0936af9b97d08c6bcd5033e61d9fa1c9153272e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62791777"
---
# <a name="add-projects-to-source-control"></a>Hinzufügen von Projekten zur Quellcodeverwaltung
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Projektmappen können mehrere Skriptprojekte hosten. Wie Sie ein Projekt zur Quellcodeverwaltung hinzufügen, hängt davon ab, ob die entsprechende Projektmappe der Quellcodeverwaltung unterliegt. Wenn die Projektmappe der Quellcodeverwaltung unterliegt, wird beim Einchecken der Projektmappe das Projekt automatisch der Quellcodeverwaltung hinzugefügt. Weitere Informationen zum Einchecken von Projektmappen finden Sie unter [Dateien einchecken](../../2014/database-engine/check-in-files.md).  
  
 Wenn die Projektmappe für dieses Projekt nicht der Quellcodeverwaltung unterliegt, können Sie der Quellcodeverwaltung die Projektmappe hinzufügen. Die Quellcodeverwaltung fügt dann automatisch die Projekte der Projektmappe hinzu. Weitere Informationen zum Hinzufügen von Projektmappen zur quellcodeverwaltung finden Sie unter [Projektmappen zur Quellcodeverwaltung hinzufügen](../../2014/database-engine/add-solutions-to-source-control.md).  
  
 Wenn Sie nicht die Projektmappe zur quellcodeverwaltung hinzufügen möchten, können Sie mithilfe der **Auswahl zur Quellcodeverwaltung hinzufügen** Befehl aus, um das Projekt manuell hinzufügen.  
  
 Datenbankobjekte werden nicht direkt vom Quellcodeverwaltungsanbieter geschützt. Sie können jedoch Skripts von Datenbankobjekten erstellen und die Skripts unter der Quellcodeverwaltung speichern.  
  
### <a name="to-add-a-project-to-source-control"></a>So fügen Sie der Quellcodeverwaltung ein Projekt hinzu  
  
1.  Wählen Sie im Projektmappen-Explorer ein Projekt aus.  
  
2.  Auf der **Datei** Startmenü **Quellcodeverwaltung**, und klicken Sie dann auf **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.  
  
    > [!NOTE]  
    >  Bei Verwendung der **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen** -Befehl, um ein Projekt hinzufügen, die zu einer Projektmappe unter quellcodeverwaltung gehört, werden Sie aufgefordert, ob Sie das Projekt als Unterordner der Projektmappe der quellcodeverwaltung unterliegende hinzuzufügen oder hinzufügen möchten. das Projekt als einen separaten Ordner.  
  
3.  Melden Sie sich beim Quellcodeverwaltungsanbieter an, wenn Sie dazu aufgefordert werden.  
  
4.  Die **zu SourceSafe hinzufügen** Dialogfeld wird angezeigt. Der Name des Projekts wird in der **Projekt** Feld.  
  
5.  In der **Ordner** auflisten, öffnen Sie den Ordner, in dem Sie das Projekt platzieren möchten. Alternativ können Sie klicken **erstellen** zum Erstellen eines Ordners mit dem Namen angezeigt, der **Projekt** Feld.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Projektmappen und Projekten zur Quellcodeverwaltung](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
