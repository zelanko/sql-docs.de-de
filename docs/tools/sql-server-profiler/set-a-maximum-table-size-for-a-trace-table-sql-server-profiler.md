---
title: Festlegen der maximalen Größe für eine Ablaufverfolgungstabelle
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 21d68638d85acd48f8f1c552319b0ea4784dec68
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307618"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>Festlegen der maximalen Tabellengröße für eine Ablaufverfolgungstabelle (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]die maximale Tabellengröße für Ablaufverfolgungstabellen festlegen.  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>So legen Sie die maximale Tabellengröße für eine Ablaufverfolgungstabelle fest  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung zu einer Instanz von SQL Server her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Geben Sie im Feld **Ablaufverfolgungsname** einen Namen für die Ablaufverfolgung ein.  
  
3.  Geben Sie im Feld **Vorlagenname**eine Ablaufverfolgungsvorlage aus.  
  
4.  Aktivieren Sie das Kontrollkästchen **In Tabelle speichern**.  
  
5.  Stellen Sie eine Verbindung mit dem Server her, auf dem Sie die Ablaufverfolgung speichern möchten.  
  
     Das Dialogfeld **Zieltabelle** wird geöffnet.  
  
6.  Wählen Sie aus der Liste **Datenbank** eine Datenbank für die Ablaufverfolgung aus.  
  
7.  Geben Sie im Feld **Tabelle** einen Tabellennamen ein, oder wählen Sie ihn aus.  
  
8.  Aktivieren Sie das Kontrollkästchen **Maximale Zeilenanzahl festlegen** , und geben Sie die maximale Zeilenanzahl für die Ablaufverfolgungstabelle an.  
  
    > [!NOTE]  
    >  Überschreiten die Zeilen in der Tabelle die maximale Anzahl, die Sie angegeben haben, werden keine Ablaufverfolgungsereignisse mehr aufgezeichnet. Die Ablaufverfolgung wird jedoch fortgesetzt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
