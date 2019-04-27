---
title: Wiederherstellen der master-Datenbank - Analytics Platform System | Microsoft-Dokumentation
description: Wiederherstellen Sie den master-Datenbank in Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 184184f332225e76e152c2d909cfff788b4fea91
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62678425"
---
# <a name="restore-the-master-database-in-analytics-platform-system"></a>Wiederherstellen der master-Datenbank in Analytics Platform System
Die **Restore Master** Seite von SQL Server PDW-Konfigurations-Manager können Sie die master-Datenbank aus einer Sicherung wiederherstellen.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
> [!IMPORTANT]  
> Um die Wiederherstellung ausführen zu können, müssen SQL Server PDW die aktuelle Masterdatenbank löschen die Sicherheitsinformationen des Benutzers und die Datenbank-Katalog enthält. Es wird empfohlen, Erstellung von einer Sicherungskopie der aktuellen master-Datenbank vor dem Ausführen der Wiederherstellung.  
  
## <a name="to-restore-the-master-database"></a>So stellen Sie die master-Datenbank wieder her  
  
1.  Starten Sie den Konfigurations-Manager. Weitere Informationen finden Sie unter [Starten des Konfigurations-Managers &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Klicken Sie im linken Bereich des Konfigurations-Managers auf **Restore Master**.  
  
3.  Wählen Sie die master Sicherung wiederherstellen.  
  
4.  Klicken Sie auf **Anwenden**.  
  
5.  Um die Wiederherstellung ausführen, wird SQL Server PDW beendet alle Dienste der Anwendung und alle Benutzer trennen. Nach Abschluss die Wiederherstellung wird in SQL Server PDW Appliance Dienste neu gestartet.  
  
![DWConfig Anwendung, PDW Restore Master](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
