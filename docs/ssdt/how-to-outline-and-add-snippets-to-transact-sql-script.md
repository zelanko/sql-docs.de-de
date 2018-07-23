---
title: 'Gewusst wie: Gliedern und Hinzufügen von Ausschnitten zu Transact-SQL-Skripts | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 543e7ce7-8639-4281-8a91-85314755e5de
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 741168fafc480c74d34a74c346d307321fa74e43
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085482"
---
# <a name="how-to-outline-and-add-snippets-to-transact-sql-script"></a>Vorgehensweise: Gliedern und Hinzufügen von Ausschnitten zu Transact-SQL-Skripts
SQL Server Data Tools enthält eine Codebibliothek mit Codeausschnitten, die in die Anwendung eingefügt werden können. Jeder Ausschnitt führt einen kompletten Skripttask aus, z. B. das Erstellen einer Funktion, einer Tabelle, eines Triggers, eines Index, einer Sicht, eines benutzerdefinierten Datentyps usw. Sie können mit wenigen Mausklicks einen Codeausschnitt in Ihren Quellcode einfügen. Diese Ausschnitte erhöhen die Produktivität, da Sie weniger Zeit für die Eingabe benötigen.  
  
Wenn Sie nach dem geeigneten Ausschnitt suchen müssen, können Sie die Ausschnittauswahl verwenden, in der kategorisierte Listen von Ausschnitten zur Auswahl stehen. Sobald Sie dem Code den Ausschnitt hinzugefügt haben, müssen möglicherweise Teile des Codes angepasst werden, indem z. B. Variablennamen durch besser geeignete Namen ersetzt werden oder die tatsächliche Logik einer gespeicherten Prozedur eingefügt wird. Sie werden feststellen, dass zu diesem Zweck im eingefügten Codeausschnitt ein oder mehrere Ersetzungspunkte hervorgehoben werden. Wenn Sie den Mauszeiger auf den Ersetzungspunkt setzen, wird in einer QuickInfo erläutert, wie Sie den Code ändern können.  
  
Standardmäßig wird im Transact\-SQL-Editor der gesamte Text angezeigt, Sie können jedoch Teile des Codes ausblenden. Im Transact\-SQL-Editor können Sie einen Codebereich markieren und als reduzierbar festlegen, sodass dieser Bereich unter einem Pluszeichen (+) angezeigt wird. Anschließend können Sie den Bereich erweitern oder ausblenden, indem Sie auf das Pluszeichen (+) neben dem Symbol klicken. Code in einer Gliederung wird nicht gelöscht, sondern nur ausgeblendet.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-insert-snippets"></a>So fügen Sie Ausschnitte ein  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TradeDev**, und klicken Sie auf **Hinzufügen** und dann auf **Skript**. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Hinzufügen**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Transact\-SQL-Editor, und wählen Sie **Ausschnitt einfügen** aus. Die Codeausschnittauswahl wird angezeigt.  
  
3.  Doppelklicken Sie in der Codeausschnittauswahl auf **Tabelle** und dann auf **Tabelle erstellen**.  
  
4.  Beachten Sie, dass Ersetzungspunkte in Gelb hervorgehoben werden. Zeigen Sie mit der Maus auf `Sample_Table`, und in einem Infotipp wird eine Beschreibung der Ersetzung angezeigt. Doppelklicken Sie auf `Sample_Table`, und ändern Sie den Tabellennamen in `Shipper2`.  
  
5.  Wechseln Sie mithilfe der TAB-TASTE zum nächsten Ersetzungspunkt (`column_1`). Benennen Sie die Spalte in `Id` um. Führen Sie die gleichen Schritte aus, um `column_2` in `name` umzubenennen, ändern Sie den Datentyp in `nvarchar(128)`, und lassen Sie `NULL`-Werte zu.  
  
### <a name="to-outline-code"></a>So gliedern Sie Code  
  
1.  Beachten Sie das **–**-Zeichen neben der CREATE TABLE-Anweisung. Klicken Sie auf das **-**-Zeichen neben einem Abschnitt im Skript, um ihn auszublenden.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Transact\-SQL-Editor, und wählen Sie **Gliedern** und dann **Gliederung entfernen** aus, um die Gliederungsinformationen ohne Auswirkungen auf den zugrunde liegenden Code im Editor zu entfernen.  
  
3.  Um den Code erneut zu gliedern, klicken Sie mit der rechten Maustaste auf den Transact\-SQL-Editor, und wählen Sie **Gliedern** und dann **Automatische Gliederung starten** aus. Sie können auch **Alle Gliederungen umschalten** auswählen, um zwischen der Ansicht mit erweiterten und ausgeblendeten Abschnitten zu wechseln.  
  
