---
title: Zieldatenbankdateien | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 97d8a955b199aeb617171ed29f27271252a9fc4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047225"
---
# <a name="destination-database-files"></a>Zieldatenbankdateien
  Verwenden Sie das Dialogfeld **Zieldatenbankdateien** , um die Namen und Speicherorte der Datenbankdateien auf dem Zielserver anzuzeigen oder um für den Task "Datenbanken übertragen" eine Dateifreigabe auf dem Netzwerk anzugeben. Weitere Informationen zu diesem Task finden Sie unter [Datenbanken übertragen (Task)](control-flow/transfer-database-task.md).  
  
 Um dieses Dialogfeld automatisch mit den Datenbankdateinamen und -speicherorten des Quellservers aufzufüllen, geben Sie zuerst auf der Seite **Datenbanken**des Dialogfelds **Editor für den Task 'Datenbanken übertragen'** die Parameter **SourceConnection** , **SourceDatabaseName** und **SourceDatabaseFiles** an.  
  
## <a name="options"></a>Tastatur  
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
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task Datenbanken übertragen &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task Datenbanken übertragen &#40;Seite Datenbanken&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  