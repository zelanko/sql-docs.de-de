---
title: Generieren von Spiegeltabellen und CDC-Aufzeichnungsinstanzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5b462a03b15042c6fbb801b121bb04a07b7966b
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921593"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a>Generieren von Spiegeltabellen und CDC-Aufzeichnungsinstanzen

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Verwenden der Seite Generate Mirror Tables zum Generieren der Spiegeltabellen für Tabellen, die Sie in die CDC-Instanz eingeschlossen haben  
  
 Klicken Sie auf **Ausführen** , um die Spiegeltabellen zu erstellen. Der Status der Erstellung jeder Tabelle wird angezeigt, und Sie werden anhand einer Meldung darüber informiert, ob die einzelnen Spiegeltabellen mit oder ohne Fehler erstellt wurden. Klicken Sie beim Auftreten von Fehlern auf **Details** , um ein Dialogfeld mit einer Erklärung des Fehlers anzuzeigen.  
  
 Falls Tabellen nicht erstellt werden, können Sie fortfahren oder vorher alle fehlerhaften Tabellen löschen. Nachdem Sie die Ausführung des Assistenten beendet haben, können Sie entscheiden, ob Sie die Tabelle in der Oracle-Quelldatenbank korrigieren oder ob Sie sie nicht in der CDC-Instanz verwenden möchten. Wenn Sie die Tabelle korrigieren, können Sie diese während des Schritts [Edit Tables](../../integration-services/change-data-capture/edit-tables.md)hinzufügen.  
  
 Klicken Sie auf **Weiter** , um die Seite [Finish](../../integration-services/change-data-capture/finish.md) zu öffnen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen der Instanz für die SQL Server-Änderungsdatenbank](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)  
  
  
