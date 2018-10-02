---
title: Abgleichen eines Datenbankdiagramms mit einer geänderten Datenbank (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- updating diagram to match database
- reconciling database diagrams
- diagrams [SQL Server], reconciling changes
- updating database to match diagram
- database diagrams [SQL Server], reconciling changes
ms.assetid: eda8dea2-eedd-43a7-85aa-92bd97783b5f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e01ac9ee73eaa64b68153e30bcdbbb9acb98c36a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650878"
---
# <a name="reconcile-a-database-diagram-with-a-modified-database-visual-database-tools"></a>Abgleichen eines Datenbankdiagramms mit einer geänderten Datenbank (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Ein Datenbankdiagramm wird gespeichert, wenn die Datenbank mit dem Diagramm aktualisiert werden soll. Wenn die Datenbank jedoch von anderen Benutzern aktualisiert wurde, während Ihr Diagramm geöffnet war, können sich die Änderungen der anderen Benutzer auf Ihr Diagramm auswirken und umgekehrt.  
  
Beim Speichern des Diagramms wird die Datenbank mit dem Diagramm abgeglichen. Die Änderungen anderer Benutzer werden dabei überschrieben, sodass die Daten in der Datenbank mit Ihrem Diagramm übereinstimmen.  
  
### <a name="to-update-a-database-to-match-your-diagram"></a>So aktualisieren Sie eine Datenbank anhand der Daten des Diagramms  
  
1.  Speichern Sie das Datenbankdiagramm.  
  
    Wenn Sie das Diagramm zum ersten Mal speichern, geben Sie im Dialogfeld **Neue(s) Datenbankdiagramm speichern** einen Namen für das Diagramm ein, und klicken Sie auf **OK**.  
  
2.  Im Dialogfeld **Speichern** werden die Tabellen aufgeführt, auf die sich das Speichern des Diagramms auswirkt. Wählen Sie **Ja** , um den Vorgang fortzusetzen.  
  
3.  Im Dialogfeld **Es wurden Änderungen in der Datenbank festgestellt** werden die Objekte aufgeführt, die bearbeitet wurden und geändert werden müssen, um eine Übereinstimmung mit dem Diagramm zu erzielen. Wählen Sie **Ja** , um das Diagramm zu speichern und die Liste der Änderungen zu übernehmen.  
  
    > [!NOTE]  
    > Wenn das Diagramm Tabellen und Spalten enthält, die in der Datenbank gelöscht wurden, werden beim Speichern des Diagramms nur die zugehörigen Definitionen in der Datenbank neu erstellt. Die Daten, die diese Objekte vor dem Löschen enthielten, können mit diesem Prozess nicht wiederhergestellt werden.  
  
### <a name="to-update-your-diagram-to-match-a-modified-database"></a>So aktualisieren Sie das Diagramm anhand der Daten einer geänderten Datenbank  
  
1.  Schließen Sie das Diagramm, ohne die Änderungen zu speichern.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf das Diagramm.  
  
3.  Klicken Sie im Kontextmenü auf **Aktualisieren**.  
  
4.  Öffnen Sie das Diagramm erneut.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Verwenden von Datenbankdiagrammen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
  
