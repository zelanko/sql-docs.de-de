---
title: Zuordnen von Dateierweiterungen zu einem Code-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- file extensions [SQL Server]
- associating file extensions [SQL Server]
- Query Editor [SQL Server Management Studio], associating file extensions
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 546835fb2aaadb9ea5d65e3cf77e87df8f24b487
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164289"
---
# <a name="associate-file-extensions-to-a-code-editor"></a>Zuordnen von Dateierweiterungen zu einem Code-Editor
  Wenn Sie Dateierweiterungen einem bestimmten Code-Editor zuordnen, werden entsprechende Dateien von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mit dem jeweiligen Code-Editor geöffnet, wenn Sie in Windows-Explorer auf eine Datei doppelklicken. Für in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]häufig verwendete Erweiterungen, z. B. SQL und MDX, werden die Zuordnungen bei der Installation erstellt. Neue Dateierweiterungen müssen im Dateisystem auch [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] zugeordnet werden. Sie können mit dieser Funktion auch Dateien öffnen, die mit anderen Editoren erstellt wurden. Das Gleiche gilt für Dateien, die Sie umbenannt haben, z. B. in BAK-Dateien umbenannte Sicherungen von SQL-Dateien.  
  
 Für diesen Vorgang sind zwei Schritte erforderlich. Ordnen Sie die Erweiterung zunächst [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]und anschließend einem bestimmten Code-Editor zu.  
  
### <a name="to-associate-a-new-file-extension-with-sql-server-management-studio"></a>So ordnen Sie SQL Server Management Studio eine neue Dateierweiterung zu  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf **Zubehör**, und klicken Sie dann auf **Windows-Explorer**.  
  
2.  Klicken Sie im Menü **Extras** von Windows-Explorer auf **Ordneroptionen**.  
  
3.  Klicken Sie auf der Registerkarte **Dateitypen** des Dialogfelds **Ordneroptionen** auf **Neu**.  
  
4.  Geben Sie im Feld **Dateierweiterung** des Dialogfelds **Eine neue Erweiterung erstellen** die neue Dateierweiterung ein, für die Sie eine Verknüpfung erstellen möchten, und klicken Sie dann auf **OK**. Lassen Sie den Punkt am Anfang der Erweiterung weg.  
  
5.  Klicken Sie im Feld **Registrierte Dateitypen** auf die neue Erweiterung, und klicken Sie dann auf **Ändern**.  
  
6.  Klicken Sie im Dialogfeld **Öffnen mit** auf **SSMS - SQL Server Management Studio**, und klicken Sie dann auf **OK**.  
  
7.  Klicken Sie auf **Schließen** , um das Dialogfeld **Ordneroptionen** zu schließen, und schließen Sie dann Windows-Explorer.  
  
### <a name="to-associate-a-new-file-extension-with-a-code-editor-in-sql-server-management-studio"></a>So ordnen Sie einem Code-Editor in SQL Server Management Studio eine neue Dateierweiterung zu  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Menü **Extras** auf **Optionen**.  
  
2.  Klicken Sie im Dialogfeld **Optionen** auf **Text-Editor**, und klicken Sie dann auf **Dateierweiterung**.  
  
3.  Geben Sie im Feld **Erweiterung** die neue Dateierweiterung ein.  
  
4.  Klicken Sie im Feld **Editor** auf den Code-Editor, mit dem dieser Dateityp geöffnet werden soll, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Ssms-Hilfsprogramm](../../ssms/ssms-utility.md)  
  
  
