---
title: Zieldatenbankdateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2cfee31b4167625b4f868d7312abd752a215652c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66059545"
---
# <a name="destination-database-files"></a>Zieldatenbankdateien
  Verwenden Sie das Dialogfeld **Zieldatenbankdateien** , um die Namen und Speicherorte der Datenbankdateien auf dem Zielserver anzuzeigen oder um für den Task "Datenbanken übertragen" eine Dateifreigabe auf dem Netzwerk anzugeben. Weitere Informationen zu diesem Task finden Sie unter [Datenbanken übertragen (Task)](control-flow/transfer-database-task.md).  
  
 Um dieses Dialogfeld automatisch mit den Datenbankdateinamen und -speicherorten des Quellservers aufzufüllen, geben Sie zuerst auf der Seite **Datenbanken**des Dialogfelds **Editor für den Task 'Datenbanken übertragen'** die Parameter **SourceConnection** , **SourceDatabaseName** und **SourceDatabaseFiles** an.  
  
## <a name="options"></a>Optionen  
 **Zieldatei**  
 Namen der übertragenen Datenbankdateien auf dem Zielserver.  
  
 Geben Sie den Dateinamen ein, oder klicken Sie darauf, um ihn zu bearbeiten.  
  
 **Zielordner**  
 Der Ordner auf dem Zielserver, in den die Datenbankdateien übertragen werden sollen.  
  
 Geben Sie den Ordnerpfad auf dem Zielserver ein, klicken Sie darauf, um ihn zu bearbeiten, oder klicken Sie auf die Schaltfläche zum Durchsuchen, um zu dem Ordner zu navigieren, in den Sie die Datenbankdateien übertragen wollen.  
  
 **Netzwerkdateifreigabe**  
 Die Netzwerkdateifreigabe auf dem Zielserver, in die die Datenbankdateien übertragen werden sollen. Verwenden Sie **Netzwerkdateifreigabe** , wenn Sie eine Datenbank im Offlinemodus übertragen, indem Sie auf der Seite **Datenbanken** des Dialogfelds **Editor für den Task 'Datenbanken übertragen'** als **Methode** **DatabaseOffline** angeben.  
  
 Geben Sie den Speicherort der Netzwerkdateifreigabe ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen, um zu dieser Netzwerkdateifreigabe zu navigieren.  
  
 Beim Übertragen einer Datenbank im Offlinemodus werden die Datenbankdateien zunächst in den als **Netzwerkdateifreigabe** angegebenen Speicherort kopiert, bevor sie in den als **Zielordner** gekennzeichneten Speicherort übertragen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task „Datenbanken übertragen“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task „Datenbanken übertragen“ &#40;Seite „Datenbanken“&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
