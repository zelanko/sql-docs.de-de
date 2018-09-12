---
title: Angeben einer Version als die neueste Version | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b55617f70a36861cb9b97aea45eaef5a08bac736
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808726"
---
# <a name="specify-a-version-as-the-latest-version"></a>Angeben einer Version als letzte Version
  Wenn Sie eine Datei in die Quellcodeverwaltung einchecken, wird die eingecheckte Version zur letzten Version. Benutzer, die die letzte Version auschecken oder abrufen, erhalten lokale Kopien des zuletzt eingecheckten Elements.  
  
 In einigen Situationen können Sie aber auch eine frühere Version eines Elements als letzte Version bestimmen. Sie können z. B. eine Datei auschecken, die Datei ändern und sie anschließend einchecken. Später beschließen Sie, die Änderungen zu verwerfen. Da Sie das Element eingecheckt haben, können Sie das ursprüngliche Auschecken nicht rückgängig machen. In diesem Fall können Sie die usprünglich ausgecheckte Version als letzte Version des Elements bestimmen.  
  
 Sie können die letzte Version folgendermaßen bestimmen:  
  
-   **Festhalten einer Version**. Wenn Sie eine Dateiversion festhalten, werden Versionen, die jünger als die festgehaltene Version sind, nicht gelöscht. Außerdem können Sie das Festhalten einer Datei aufheben, die Sie zuvor festgehalten haben. Dabei wird die zuletzt eingecheckte Version der Datei zur letzten Version. Sie können aber keine festgehaltene Datei auschecken.  
  
-   **Rollback zu einer angegebenen Version**. Wenn Sie ein Rollback zu einer Version ausführen, werden alle aktuelleren Versionen aus der Quellcodeverwaltung gelöscht. Sie können dann die letzte verbleibende Version auschecken.  
  
### <a name="to-pin-a-version"></a>So halten Sie eine Version fest  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], öffnen Sie die Projektmappe.  
  
2.  Wählen Sie im Projektmappen-Explorer die Datei aus, die Sie als letzte Version angeben möchten.  
  
3.  Auf der **Datei** Startmenü **Quellcodeverwaltung** , und klicken Sie auf **ViewHistory**.  
  
4.  In der **Verlauf** \<Datei > Dialogfeld Feld, wählen Sie die Version, die Sie verwenden möchten, geben Sie als die neueste Version aus, und klicken Sie auf **Pin**.  
  
     Die von Ihnen ausgewählte Version wird mit einem entsprechenden Symbol als aktuelle Dateiversion gekennzeichnet. Wenn eine andere Version in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] geladen wurde, werden Sie aufgefordert, die Datei neu zu laden.  
  
### <a name="to-roll-back-to-a-version"></a>So führen Sie ein Rollback zu einer Version aus  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], öffnen Sie die Projektmappe.  
  
2.  Wählen Sie im Projektmappen-Explorer das Element aus, das Sie als letzte Version angeben möchten.  
  
3.  Auf der **Datei** Startmenü **Quellcodeverwaltung** , und klicken Sie auf **Verlauf**.  
  
4.  In der **Verlaufsoptionen** Dialogfeld klicken Sie auf **OK** zum Anzeigen der **Versionsgeschichte von Datei** im Dialogfeld.  
  
5.  In der **Versionsgeschichte von Datei** Feld, wählen Sie die Version, die Sie verwenden möchten, geben Sie als letzte Version, und klicken Sie auf **Rollback**.  
  
     Eine Meldung wird angezeigt, in der Sie darüber benachrichtigt werden, dass alle Versionen nach der von Ihnen ausgewählten Version gelöscht werden.  
  
6.  Klicken Sie auf **Ja** Rollback zur ausgewählten Version.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Eincheckvorgängen](../../2014/database-engine/manage-checkins.md)   
 [Einchecken von Dateien](../../2014/database-engine/check-in-files.md)  
  
  
