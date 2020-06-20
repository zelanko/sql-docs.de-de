---
title: Veröffentlichen der Ausführung einer gespeicherten Prozedur in einer Transaktions Veröffentlichung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a226d7c58b3b72caf415d8e873b58ca38d3c749f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060433"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a>Veröffentlichen der Ausführung einer gespeicherten Prozedur in einer Transaktionsveröffentlichung (SQL Server Management Studio)
  Gibt an, dass die Ausführung einer gespeicherten Prozedur (und nicht nur ihrer Definition) im Dialogfeld **Artikeleigenschaften- \<Article> ** veröffentlicht werden soll. Dieses Dialogfeld ist im Assistenten für neue Veröffentlichung und im Dialogfeld **Veröffentlichungs Eigenschaften \<Publication> -** verfügbar. Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
 Die Definition der Prozedur (die CREATE PROCEDURE-Anweisung) wird beim Initialisieren des Abonnements auf den Abonnenten repliziert. Wenn die Prozedur dann auf dem Verleger ausgeführt wird, führt die Replikation auch die entsprechende Prozedur auf dem Abonnenten aus.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>So veröffentlichen Sie die Ausführung einer gespeicherten Prozedur  
  
1.  Wählen Sie auf der Seite **Artikel** des Assistenten für neue Veröffentlichung oder im Dialogfeld **Veröffentlichungs Eigenschaften- \<Publication> ** eine gespeicherte Prozedur aus.  
  
2.  Klicken Sie auf **Artikeleigenschaften**und anschließend auf **Eigenschaften des hervorgehobenen Gespeicherte Prozedur-Artikels festlegen**.  
  
3.  Geben Sie im Dialogfeld **Artikeleigenschaften- \<Article> ** einen der folgenden Werte für die Option **Replizieren** an:  
  
    -   **Ausführung der gespeicherten Prozedur**  
  
    -   **Ausführung in einer serialisierten Transaktion der gespeicherten Prozedur**  
  
         Es handelt sich hierbei um die bevorzugte Option, da hier die Prozedurausführung nur repliziert wird, wenn die Prozedur im Kontext einer serialisierbaren Transaktion ausgeführt wird. Falls die gespeicherte Prozedur außerhalb einer serialisierbaren Transaktion ausgeführt wird, werden Änderungen an den Daten in veröffentlichten Tabellen als eine Reihe von DML-Anweisungen (Data Manipulation Language, Datenbearbeitungssprache) repliziert.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Wenn Sie sich im Dialogfeld **Veröffentlichungs Eigenschaften \<Publication> -** befinden, klicken Sie auf **OK** , um das Dialogfeld zu speichern und zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen der Ausführung gespeicherter Prozeduren in der Transaktions Replikation](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
