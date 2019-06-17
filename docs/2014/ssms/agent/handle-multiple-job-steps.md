---
title: Handhaben mehrerer Auftragsschritte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- ordering job steps [SQL Server]
- multiple job steps
- SQL Server Agent jobs, job steps
- control of flow for jobs [SQL Server]
ms.assetid: 7aba19ff-72b3-45f6-8e54-23f4988d63a8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 379877d3a08c60a293b96c5c57d55a2894ba0a79
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63074051"
---
# <a name="handle-multiple-job-steps"></a>Handhaben mehrerer Auftragsschritte
  Wenn Ihr Auftrag aus mehr als einem Auftragsschritt besteht, müssen Sie die Reihenfolge angeben, in der die Auftragsschritte ausgeführt werden. Dies wird *Ablaufsteuerung*** genannt. Sie können jederzeit neue Auftragsschritte hinzufügen und den Ablauf der Auftragsschritte neu ordnen. Die Änderungen werden bei der nächsten Ausführung des Auftrags wirksam. In dieser Abbildung ist die Ablaufsteuerung eines Auftrags für die Datenbanksicherung dargestellt.  
  
 ![Ablaufsteuerung für SQL Server-Agent-Auftragsschritte](../../database-engine/media/dbflow01.gif "Ablaufsteuerung für SQL Server-Agent-Auftragsschritte")  
  
 Der erste Schritt besteht in der Datenbanksicherung. Wenn dieser Schritt einen Fehler erzeugt, wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ein Fehler an den Ausführenden berichtet, der als Empfänger der Benachrichtigung definiert ist. Wenn der Schritt zur Datenbanksicherung erfolgreich ist, wird vom Auftrag der nächste Schritt ausgeführt, das "Bereinigen" der Kundendaten. Wenn dieser Schritt einen Fehler erzeugt, wird vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent der Ablauf mit der Datenbankwiederherstellung fortgesetzt. Wenn die Bereinigung der Benutzerdaten erfolgreich ist, wird der Auftrag mit dem nächsten Schritt fortgesetzt, beispielsweise Aktualisieren der Statistik und so weiter, bis der letzte Schritt entweder einen Erfolg oder einen Fehler des Berichts zum Ergebnis hat.  
  
 Sie definieren eine Ablaufsteuerungsaktion für die erfolgreiche oder fehlgeschlagene Ausführung einzelner Auftragsschritte. Sie müssen eine Aktion angeben, die durchgeführt werden soll, wenn ein Auftragsschritt erfolgreich ausgeführt wird, und eine Aktion für den Fall, dass ein Auftragsschritt einen Fehler erzeugt. Sie können zudem die Anzahl der Wiederholungsversuche und der Intervalle zwischen diesen Versuchen bei fehlgeschlagenen Auftragsschritten definieren.  
  
> [!NOTE]  
>  Wenn Sie einen oder mehrere Schritte über die grafische Benutzeroberfläche (Graphical User Interface, GUI) des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents aus einem Auftrag mit mehreren Schritten löschen, entfernt die GUI alle Auftragsschritte und fügt die verbleibenden Schritte mit den richtigen Verweisen bei Erfolg oder bei Fehler wieder hinzu. Angenommen, ein Auftrag besteht aus fünf Schritten, und der erste Schritt ist so konfiguriert, dass er bei erfolgreichem Abschluss zu Schritt 4 springt. Wenn Sie Schritt 3 löschen, entfernt die GUI alle Schritte für diesen Auftrag und fügt die verbleibenden Schritte (1, 2, 4 und 5) mit den korrigierten Verweisen wieder hinzu. In diesem Fall wird der Verweis in Schritt 1 neu konfiguriert, damit der Vorgang bei erfolgreichem Abschluss von Schritt 1 mit Schritt 3 fortgesetzt wird.  
  
 Auftragsschritte müssen eigenständig sein. Ein Auftrag kann keine booleschen Werte, Daten oder numerischen Werte zwischen den Auftragsschritten übergeben. Sie können allerdings Werte von einem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Auftragsschritt zu einem anderen mithilfe von dauerhaften Tabellen oder globalen temporären Tabellen übergeben. Sie können Werte von Auftragsschritten, die Programme von einem Auftragsschritt zum nächsten ausführen, mithilfe von Dateien übergeben. Von einer Datei, die von einem Auftragsschritt ausgeführt wird, kann beispielsweise in eine Datei geschrieben werden, und von einer Datei, die von einem nachfolgenden Auftragsschritt ausgeführt wird, kann die Datei gelesen werden.  
  
> [!NOTE]  
>  Sollten Sie Auftragsschritte erstellen, die sich in einer Schleife gegenseitig aufrufen (auf Auftragsschritt 1 folgt Auftragsschritt 2, dann kehrt Auftragsschritt 2 zu Auftragsschritt 1 zurück), wird eine Warnmeldung angezeigt, wenn der Auftrag mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellt wird.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent zeichnet die Informationen von Aufträgen und Auftragsschritten im Auftragsverlauf auf.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)   
 [dbo.sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)   
 [dbo.sysjobs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql)   
 [dbo.sysjobsteps &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql)   
 [Implementieren von Aufträgen](implement-jobs.md)   
 [Verwalten von Auftragsschritten](manage-job-steps.md)  
  
  
