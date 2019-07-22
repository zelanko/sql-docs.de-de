---
title: Hinzufügen und Löschen von Artikeln aus einer Veröffentlichung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b536a359ad566e022ef0c69f00f12dd2a178fb4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67907995"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication"></a>Hinzufügen und Löschen von Artikeln aus einer Veröffentlichung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Sie können einer Veröffentlichung bereits bei Ihrer Erstellung im Assistenten für neue Veröffentlichung Artikel hinzufügen. Weitere Informationen über das Verwenden dieses Assistenten finden Sie unter [Erstellen einer Veröffentlichung](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 Zum Hinzufügen und Löschen von Artikeln zu bzw. aus einer bereits erstellten Veröffentlichung steht Ihnen die Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** zur Verfügung. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Informationen zu Überlegungen für das Hinzufügen und Löschen von Artikeln finden Sie unter [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a>So fügen Sie einer bereits erstellten Veröffentlichung einen Artikel hinzu  
  
1.  Deaktivieren Sie auf der Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Option **Nur aktivierte Objekte in der Liste anzeigen**. Auf diese Weise werden nur die nicht veröffentlichten Objekte in der Veröffentlichungsdatenbank angezeigt.  
  
2.  Markieren Sie die Kontrollkästchen für alle Artikel, die Sie der Veröffentlichung hinzufügen möchten.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a>So löschen Sie einen Artikel  
  
1.  Deaktivieren Sie auf der Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Kontrollkästchen für alle Artikel, die aus der Veröffentlichung gelöscht werden sollen.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren eines Artikels](../../../relational-databases/replication/publish/define-an-article.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
