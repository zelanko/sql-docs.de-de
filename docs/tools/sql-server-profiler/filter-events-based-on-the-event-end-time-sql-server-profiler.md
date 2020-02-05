---
title: Filtern von Ereignissen basierend auf der Beendigungszeit des Ereignisses
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 8372ce58317eead122675f3585be01f5da7eb829
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307268"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a>Filtern von Ereignissen anhand der Ereignisendzeit (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]Ablaufverfolgungsereignisse basierend auf der Beendigungszeit des Ereignisses filtern.  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a>So filtern Sie Ereignisse, die auf der Beendigungszeit des Ereignisses basieren  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Stellen Sie im Dialogfeld **Ablaufverfolgungseigenschaften** sicher, dass die Registerkarte **Allgemein** ausgewählt ist, und geben Sie in das Textfeld **Ablaufverfolgungsname** einen Namen ein.  
  
3.  Wählen Sie in der Liste **Vorlage verwenden**eine Nachverfolgungsvorlage aus.  
  
4.  Sie können optional eine Zieldatei oder Zieltabelle angeben, in der die Ablaufverfolgungsergebnisse gespeichert werden.  
  
5.  Klicken Sie auf der Registerkarte **Ereignisauswahl**auf die **EndTime** Datenspalte, um das Dialogfeld **Filter bearbeiten** zu öffnen. Sie können auch mit der rechten Maustaste auf die Spaltenüberschrift klicken und **Spaltenfilter bearbeiten**auswählen.  
  
6.  Erweitern Sie **Größer als** oder **Kleiner als**, und geben Sie einen **datetime**-Wert in das Feld ein, welches unterhalb des Vergleichsoperators angezeigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
