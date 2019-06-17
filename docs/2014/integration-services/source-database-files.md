---
title: Datenbank-Quelldateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ac7d4b590fa5c3efccd16deebf3bafab83b74f6b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66055538"
---
# <a name="source-database-files"></a>Quelldatenbankdateien
  Verwenden Sie das Dialogfeld **Quelldatenbankdateien** , um die Namen und Speicherorte der Datenbankdateien auf dem Quellserver anzuzeigen, oder um für den Task "Datenbanken übertragen" eine Dateifreigabe auf dem Netzwerk anzugeben. Weitere Informationen zu diesem Task finden Sie unter [Datenbanken übertragen (Task)](control-flow/transfer-database-task.md).  
  
 Um dieses Dialogfeld mit den Datenbankdateinamen und -speicherorten des Quellservers aufzufüllen, geben Sie zuerst auf der Seite **Datenbanken** des Dialogfelds **Editor für den Task 'Datenbanken übertragen'** die Parameter **SourceConnection** und **SourceDatabaseName** an.  
  
## <a name="options"></a>Optionen  
 **Quelldatei**  
 Die Namen der zu übertragenden Datenbankdateien auf dem Quellserver. **Quelldatei** ist schreibgeschützt.  
  
 **Quellordner**  
 Der Ordner auf dem Quellserver, in dem sich die zu übertragenden Datenbankdateien befinden. **Quellordner** ist schreibgeschützt.  
  
 **Netzwerkdateifreigabe**  
 Der auf dem Netzwerk freigegebene Ordner auf dem Quellserver, aus dem die Datenbankdateien übertragen werden sollen. Verwenden Sie **Netzwerkdateifreigabe** , wenn Sie eine Datenbank im Offlinemodus übertragen, indem Sie auf der Seite **Datenbanken** des Dialogfelds **Editor für den Task 'Datenbanken übertragen'** als **Methode** **DatabaseOffline** angeben.  
  
 Geben Sie den Speicherort der Netzwerkdateifreigabe ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen **(…)** , um zu dieser Netzwerkdateifreigabe zu navigieren.  
  
 Beim Übertragen einer Datenbank im Offlinemodus werden die Datenbankdateien zunächst in den als **Netzwerkdateifreigabe** angegebenen Speicherort auf dem Quellserver kopiert, bevor sie auf den Zielserver übertragen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task „Datenbanken übertragen“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task „Datenbanken übertragen“ &#40;Seite „Datenbanken“&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
