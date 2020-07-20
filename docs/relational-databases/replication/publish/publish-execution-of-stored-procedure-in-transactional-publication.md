---
title: Veröffentlichen der Ausführung von gespeicherten Prozeduren (Transaktionsveröffentlichung)
description: In diesem Artikel erfahren Sie, wie Sie die Ausführung gespeicherter Prozeduren mithilfe von SQL Server Management Studio veröffentlichen.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 5f2080ec477f25289db266918b90a40ff2041f98
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86160118"
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>Veröffentlichen der Ausführung der gespeicherten Prozedur in einer Transaktionspublikation
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  Im Dialogfeld **Artikeleigenschaften - \<Article>** können Sie angeben, dass die Ausführung einer gespeicherten Prozedur (und nicht nur ihre Definition) veröffentlicht werden soll. Dieses Dialogfeld ist im Assistenten für neue Veröffentlichungen sowie über das Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** verfügbar. Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](../../../relational-databases/replication/publish/create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 Die Definition der Prozedur (die CREATE PROCEDURE-Anweisung) wird beim Initialisieren des Abonnements auf den Abonnenten repliziert. Wenn die Prozedur dann auf dem Verleger ausgeführt wird, führt die Replikation auch die entsprechende Prozedur auf dem Abonnenten aus.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>So veröffentlichen Sie die Ausführung einer gespeicherten Prozedur  
  
1.  Wählen Sie auf der Seite **Artikel** des Assistenten für neue Veröffentlichungen oder im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** eine gespeicherte Prozedur aus.  
  
2.  Klicken Sie auf **Artikeleigenschaften**und anschließend auf **Eigenschaften des hervorgehobenen Gespeicherte Prozedur-Artikels festlegen**.  
  
3.  Geben Sie im Dialogfeld **Artikeleigenschaften - \<Article>** einen der folgenden Werte für die Option **Replizieren** an:  
  
    -   **Ausführung der gespeicherten Prozedur**  
  
    -   **Ausführung in einer serialisierten Transaktion**  
  
         Es handelt sich hierbei um die bevorzugte Option, da hier die Prozedurausführung nur repliziert wird, wenn die Prozedur im Kontext einer serialisierbaren Transaktion ausgeführt wird. Falls die gespeicherte Prozedur außerhalb einer serialisierbaren Transaktion ausgeführt wird, werden Änderungen an den Daten in veröffentlichten Tabellen als eine Reihe von DML-Anweisungen (Data Manipulation Language, Datenbearbeitungssprache) repliziert.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** befinden, klicken Sie auf **OK**, um die Einstellungen zu speichern und das Dialogfeld zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen der Ausführung von gespeicherten Prozeduren in der Transaktionsreplikation](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
