---
title: Erstellen eines Skriptes für eine Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a1ba568309bcea7f760d2f4c7f7a691048a4bf84
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067307"
---
# <a name="script-a-table"></a>Erstellen eines Skriptes für eine Tabelle
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Skripts für das Auswählen, Einfügen, Aktualisieren und Löschen von Tabellen und das Anlegen, Ändern, Löschen und Ausführen von gespeicherten Prozeduren erstellt werden.  
  
 Möglicherweise benötigen Sie in einigen Fällen ein Skript mit mehreren Optionen, wie z. B. zum Löschen einer Prozedur und dann zum Anlegen einer Prozedur oder zum Anlegen einer Tabelle und dann zum Ändern einer Tabelle. Zum Anlegen kombinierter Skripts speichern Sie das erste Skript in einem Abfrage-Editorfenster und das zweite in der Zwischenablage, sodass Sie es im Fenster nach dem ersten Skript einfügen können.  
  
## <a name="creating-an-update-script"></a>Anlegen eines Updateskripts  
  
#### <a name="to-create-the-insert-script-for-a-table"></a>So erstellen Sie ein Skript zum Einfügen in eine Tabelle  
  
1.  Erweitern Sie im Objekt-Explorer Ihren Server, erweitern Sie **Datenbanken**, erweitern Sie [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]und **Tabellen**, klicken Sie mit der rechten Maustaste auf **HumanResources.Employee**, und zeigen Sie anschließend auf **Skript für Tabelle als**.  
  
2.  Das Kontextmenü umfasst sieben Optionen für Skripts: **CREATE in**, **DROP in**, **DROP und CREATE in**, **SELECT in**, **INSERT in**, **UPDATE in**und **DELETE in**. Zeigen Sie auf **UPDATE in**, und klicken Sie dann auf **Neues Abfrage-Editorfenster**.  
  
3.  Ein neues Abfrage-Editorfenster wird geöffnet, eine Verbindung wird hergestellt, und die gesamte Update-Anweisung wird angezeigt.  
  
     Diese Übung zeigt Ihnen, dass die Funktion zur Skripterstellung mehr bietet als das Schreiben eines Skripts zum Anlegen einer Tabelle oder gespeicherten Prozedur. Diese neue Funktion unterstützt Sie, wenn Sie Ihrem Projekt schnell Skripts für Datenänderungen hinzufügen möchten. Es hilft Ihnen beim einfachen Erstellen von Skripts für die Ausführung gespeicherter Prozeduren. So können Sie in vielen Bereichen viel Zeit bei der Arbeit mit Tabellen und Prozeduren sparen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Zusammenfassung: Schreiben von Transact-SQL-Code](../../tutorials/summary-writing-transact-sql.md)  
  
  
