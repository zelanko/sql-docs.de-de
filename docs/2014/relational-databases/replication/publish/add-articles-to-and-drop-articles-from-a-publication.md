---
title: Hinzufügen von Artikeln zu, und Löschen von Artikeln aus einer Veröffentlichung (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ea3c32da50b3ec5e2a2eb3d3bf58fad1e0323f10
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049887"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication-sql-server-management-studio"></a>Hinzufügen von Artikeln zu einer Veröffentlichung und Löschen von Artikeln aus einer Veröffentlichung (SQL Server Management Studio)
  Sie können einer Veröffentlichung bereits bei Ihrer Erstellung im Assistenten für neue Veröffentlichung Artikel hinzufügen. Weitere Informationen über das Verwenden dieses Assistenten finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md).  
  
 Zum Hinzufügen und Löschen von Artikeln zu bzw. aus einer bereits erstellten Veröffentlichung steht Ihnen die Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** zur Verfügung. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md). Informationen zu Überlegungen für das Hinzufügen und Löschen von Artikeln finden Sie unter [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a>So fügen Sie einer bereits erstellten Veröffentlichung einen Artikel hinzu  
  
1.  Deaktivieren Sie auf der Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Option **Nur aktivierte Objekte in der Liste anzeigen**. Auf diese Weise werden nur die nicht veröffentlichten Objekte in der Veröffentlichungsdatenbank angezeigt.  
  
2.  Markieren Sie die Kontrollkästchen für alle Artikel, die Sie der Veröffentlichung hinzufügen möchten.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a>So löschen Sie einen Artikel  
  
1.  Deaktivieren Sie auf der Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Kontrollkästchen für alle Artikel, die aus der Veröffentlichung gelöscht werden sollen.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren eines Artikels](define-an-article.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md)  
  
  