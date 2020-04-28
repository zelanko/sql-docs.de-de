---
title: Master-Datenbank wiederherstellen
description: Stellen Sie die Master-Datenbank in Analytics Platform System (APS) wieder her.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6d122881f5283da86f66494ee2f049756d151551
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400451"
---
# <a name="restore-the-master-database-in-analytics-platform-system-aps"></a>Wiederherstellen der Master-Datenbank in Analytics Platform System (APS)
Auf der Seite **Wiederherstellen der Master** -Datenbank des SQL Server PDW Configuration Manager können Sie die Master-Datenbank aus einer Sicherung wiederherstellen.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
> [!IMPORTANT]  
> Um die Wiederherstellung auszuführen, müssen SQL Server PDW die aktuelle Master-Datenbank löschen, die Benutzer Sicherheitsinformationen und den Daten Bank Katalog enthält. Es wird empfohlen, vor der Wiederherstellung eine Sicherung der aktuellen Master Datenbank durchzuführen.  
  
## <a name="to-restore-the-master-database"></a>So stellen Sie die master-Datenbank wieder her  
  
1.  Starten Sie die Configuration Manager. Weitere Informationen finden Sie unter [Start the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Klicken Sie im linken Bereich des Configuration Manager auf **Master wiederherstellen**.  
  
3.  Wählen Sie die wieder herzustellende Master Sicherung aus.  
  
4.  Klicken Sie auf **Anwenden**.  
  
5.  Zum Durchführen der Wiederherstellung werden SQL Server PDW alle Geräte Dienste heruntergefahren und die Verbindung mit allen Benutzern getrennt. Nachdem die Wiederherstellung abgeschlossen ist, werden die Geräte Dienste SQL Server PDW neu gestartet.  
  
![DWConfig-Anwendung, PDW Restore Master](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
