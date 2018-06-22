---
title: Sicherungsmedium auswählen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6135239b182c66ae4622dcf9af704fb30f167f6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057852"
---
# <a name="select-backup-device"></a>Sicherungsmedium auswählen
  Mithilfe des Dialogfelds **Sicherungsmedium auswählen** können Sie ein logisches Sicherungsmedium für die Wiederherstellung auswählen.  
  
 Ein logisches Sicherungsmedium ist ein benutzerdefiniertes logisches Medium, das einem vom Betriebssystem bereitgestellten physischen Medium, entweder Bandlaufwerk oder Disketten- bzw. Festplattenlaufwerk, entspricht.  
  
> [!NOTE]  
>  Wenn eine Sicherung mehrere Sicherungsmedien verwendet, müssen diese alle einem einzigen Medientyp entsprechen.  
  
 **So verwenden Sie SQL Server Management Studio zum Anzeigen des Inhalts eines Sicherungsmediums**  
  
-   [Anzeigen der Inhalte eines Sicherungsbands oder einer -datei &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Tastatur  
 **Sicherungsmedium**  
 Wählen Sie im Listenfeld den Namen eines logischen Sicherungsmediums aus, von dem die Wiederherstellung erfolgen soll.  
  
 Weitere Informationen zum Anzeigen des Inhalts eines Sicherungsmediums finden Sie unter [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).  
  
## <a name="remarks"></a>Hinweise  
 Wenn kein logisches Sicherungsmedium in der Liste angezeigt wird, das die gesuchte Sicherung enthält, wurde die Sicherung möglicherweise direkt in eine oder mehrere Dateien oder Bandlaufwerke geschrieben. Schließen Sie in diesem Fall das Dialogfeld **Sicherungsmedium auswählen** , und wählen Sie im Dialogfeld **Sicherung angeben** im Listenfeld **Sicherungsmedium** die Option **Datei** oder **Band** aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)  
  
  