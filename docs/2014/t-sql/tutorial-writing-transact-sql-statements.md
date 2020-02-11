---
title: 'Tutorial: Schreiben von Transact-SQL-Anweisungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL statements, tutorials
- Transact-SQL tutorials
- tutorials [Transact-SQL]
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 67e09713fdec72313bde6ba81e1cc169467fda0c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211196"
---
# <a name="tutorial-writing-transact-sql-statements"></a>Lernprogramm: Schreiben von Transact-SQL-Anweisungen
  Willkommen beim Lernprogramm zum Schreiben von [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen. Dieses Lernprogramm richtet sich an Benutzer, die noch keine Erfahrung mit dem Schreiben von SQL-Anweisungen haben. Neuen Benutzern wird der Einstieg erleichtert, indem einige einfache Anweisungen zum Erstellen von Tabellen und Einfügen von Daten behandelt werden. In diesem Lernprogramm wird [!INCLUDE[tsql](../includes/tsql-md.md)]- die Implementierung des SQL-Standards durch [!INCLUDE[msCoName](../includes/msconame-md.md)] - verwendet. Dieses Lernprogramm ist als kurze Einführung in die [!INCLUDE[tsql](../includes/tsql-md.md)] -Sprache und nicht als Ersatz für eine [!INCLUDE[tsql](../includes/tsql-md.md)] -Schulung gedacht. Die Anweisungen in diesem Lernprogramm wurden absichtlich einfach gestaltet und geben nicht die Komplexität einer typischen Produktionsdatenbank wieder.  
  
> [!NOTE]  
>  Benutzer, die erstmals mit Datenbanken arbeiten, empfinden die Verwendung von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] anstelle des Schreibens von [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen gewöhnlich als einfacher.  
  
## <a name="finding-more-information"></a>Weitere Informationsquellen  
 Weitere Informationen zu bestimmten Anweisungen erhalten Sie, indem Sie in der SQL Server-Onlinedokumentation nach dem Namen der jeweiligen Anweisung suchen oder die 1.800 alphabetisch geordneten Sprachelemente unter [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference) über das Inhaltsverzeichnis durchsuchen. Eine weitere gute Strategie zum Suchen von Informationen besteht darin, Stichwörtern zu verwenden, die mit dem betreffenden Fachgebiet zu tun haben. Wenn Sie z.B. wissen möchten, wie Teile eines Datums zurückgegeben werden (z.B. der Monat), suchen Sie im Index nach **Datumsangaben [SQL Server]** , und wählen Sie die **Datumsbestandteile**aus. Dadurch gelangen Sie zum Thema [DATEPART &#40;Transact-SQL&#41;](/sql/t-sql/functions/datepart-transact-sql). Wenn Sie beispielsweise Informationen zur Verwendung von Zeichenfolgen benötigen, suchen Sie nach **Zeichenfolgenfunktionen**. Dadurch gelangen Sie zum Thema [Zeichenfolgenfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql).  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm wird Ihnen gezeigt, wie eine Datenbank erstellt wird, eine Tabelle in der Datenbank erstellt wird, Daten in die Tabelle eingefügt werden, die Daten aktualisiert, gelesen und gelöscht werden und die Tabelle anschließend gelöscht wird. Sie erstellen Sichten und gespeicherte Prozeduren und konfigurieren einen Benutzer für die Datenbank und die Daten.  
  
 Dieses Lernprogramm ist in drei Lektionen aufgeteilt:  
  
 [Lesson 1: Creating Database Objects (Lektion 1: Erstellen von Datenbankobjekten)](lesson-1-creating-database-objects.md)  
 In dieser Lektion erstellen Sie eine Datenbank und eine Tabelle in der Datenbank, fügen Daten in die Tabelle ein und aktualisieren und lesen die Daten.  
  
 [Lesson 2: Configuring Permissions on Database Objects (Lektion 2: Konfigurieren von Berechtigungen für Datenbankobjekte)](lesson-2-configuring-permissions-on-database-objects.md)  
 In dieser Lektion erstellen Sie einen Anmeldenamen und einen Benutzer. Sie erstellen auch eine Sicht und eine gespeicherte Prozedur und erteilen dann dem Benutzer eine Berechtigung für die gespeicherte Prozedur.  
  
 [Lesson 3: Deleting Database Objects (Lektion 3: Löschen von Datenbankobjekten)](lesson-3-1-deleting-database-objects.md)  
 In dieser Lektion entfernen Sie den Zugriff auf Daten, löschen Daten aus einer Tabelle und löschen die Tabelle und anschließend die Datenbank.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Damit Sie dieses Lernprogramm ausführen können, müssen Sie die SQL-Sprache nicht beherrschen, sollten jedoch grundlegende Konzepte einer Datenbank, wie z. B. Tabellen, kennen. Im Verlauf dieses Lernprogramms erstellen Sie eine Datenbank und einen Windows-Benutzer. Für diese Aufgaben sind Berechtigungen auf höherer Ebene erforderlich. Sie sollten sich deshalb als Administrator am Computer anmelden.  
  
 Auf dem System muss Folgendes installiert sein:  
  
-   Eine beliebige Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Entweder [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder Management Studio Express.  
  
-   Internet Explorer 6 oder höher.  
  
> [!NOTE]  
>  Wenn Sie die Tutorials überprüfen, empfiehlt es sich, der Symbolleiste in der Dokument Anzeige **die Schaltflächen** **weiter** und zurück hinzuzufügen.  
  
  
