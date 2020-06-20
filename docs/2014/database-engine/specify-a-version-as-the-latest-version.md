---
title: Geben Sie eine Version als neueste Version an | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d598ec6f828fc7d8d59b3f998b775a752b94c4a6
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928869"
---
# <a name="specify-a-version-as-the-latest-version"></a>Angeben einer Version als letzte Version
  Wenn Sie eine Datei in die Quellcodeverwaltung einchecken, wird die eingecheckte Version zur letzten Version. Benutzer, die die letzte Version auschecken oder abrufen, erhalten lokale Kopien des zuletzt eingecheckten Elements.  
  
 In einigen Situationen können Sie aber auch eine frühere Version eines Elements als letzte Version bestimmen. Sie können z. B. eine Datei auschecken, die Datei ändern und sie anschließend einchecken. Später beschließen Sie, die Änderungen zu verwerfen. Da Sie das Element eingecheckt haben, können Sie das ursprüngliche Auschecken nicht rückgängig machen. In diesem Fall können Sie die usprünglich ausgecheckte Version als letzte Version des Elements bestimmen.  
  
 Sie können die letzte Version folgendermaßen bestimmen:  
  
-   **Anhenung einer Version**. Wenn Sie eine Dateiversion festhalten, werden Versionen, die jünger als die festgehaltene Version sind, nicht gelöscht. Außerdem können Sie das Festhalten einer Datei aufheben, die Sie zuvor festgehalten haben. Dabei wird die zuletzt eingecheckte Version der Datei zur letzten Version. Sie können aber keine festgehaltene Datei auschecken.  
  
-   **Rollback zu einer bestimmten Version**. Wenn Sie ein Rollback zu einer Version ausführen, werden alle aktuelleren Versionen aus der Quellcodeverwaltung gelöscht. Sie können dann die letzte verbleibende Version auschecken.  
  
### <a name="to-pin-a-version"></a>So halten Sie eine Version fest  
  
1.  Öffnen Sie in die Projekt Mappe [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
2.  Wählen Sie im Projektmappen-Explorer die Datei aus, die Sie als letzte Version angeben möchten.  
  
3.  Zeigen Sie im Menü **Datei** auf **Quell** Code Verwaltung, und klicken Sie auf **ViewHistory**.  
  
4.  Wählen Sie **History of** im \<file> Dialogfeld Verlauf die Version aus, die Sie als letztes angeben möchten, und klicken Sie auf **Pin**anheften.  
  
     Die von Ihnen ausgewählte Version wird mit einem entsprechenden Symbol als aktuelle Dateiversion gekennzeichnet. Wenn eine andere Version in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] geladen wurde, werden Sie aufgefordert, die Datei neu zu laden.  
  
### <a name="to-roll-back-to-a-version"></a>So führen Sie ein Rollback zu einer Version aus  
  
1.  Öffnen Sie in die Projekt Mappe [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
2.  Wählen Sie im Projektmappen-Explorer das Element aus, das Sie als letzte Version angeben möchten.  
  
3.  Zeigen Sie im Menü **Datei** auf **Quell** Code Verwaltung, und klicken Sie auf **Verlauf**.  
  
4.  Klicken Sie im Dialogfeld Versions Verlaufs **Optionen** auf **OK** , um das Dialogfeld **Verlauf der Datei** anzuzeigen.  
  
5.  Wählen Sie im Feld **Verlauf der Datei** die Version aus, die Sie als neueste Version angeben möchten, und klicken Sie auf **Rollback**.  
  
     Eine Meldung wird angezeigt, in der Sie darüber benachrichtigt werden, dass alle Versionen nach der von Ihnen ausgewählten Version gelöscht werden.  
  
6.  Klicken Sie auf **Ja** , um ein Rollback zur ausgewählten Version auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Check-Ins verwalten](../../2014/database-engine/manage-checkins.md)   
 [Einchecken von Dateien](../../2014/database-engine/check-in-files.md)  
  
  
