---
title: 'Gewusst wie: Navigieren zwischen Skripts | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.editor.howto.navigate
ms.assetid: 8664bde5-86ff-4e8b-b5a6-af003316f6ad
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b06fbf69aa5a9d1c9354907f953d0fa98e8f9d40
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085672"
---
# <a name="how-to-navigate-between-scripts"></a>Vorgehensweise: Navigieren zwischen Skripts
Der Transact\-SQL-Editor für die Offlineentwicklung stellt zwei nützliche Navigationstools bereit, die Benutzern von Visual Studio bereits vertraut sind: „Gehe zu Definition“ und „Alle Verweise suchen“. Sie können z. B. mit der rechten Maustaste auf einen Tabellennamen klicken und mit der Option "Alle Verweise suchen" alle Verweise auf die Tabelle im Projekt auflisten. Sie können auf ein Suchergebnis doppelklicken, um zur jeweiligen Codedatei zu wechseln. In dieser Datei können Sie wiederum mit der rechten Maustaste auf den Tabellennamen klicken und "Gehe zu Definition" auswählen, um zurück zur Tabellendefinition zu wechseln.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-navigate-between-scripts"></a>So navigieren Sie zwischen Skripts  
  
1.  Erweitern Sie im **Projektmappen-Explorer** den Ordner **Funktionen**, und doppelklicken Sie auf **GetProductsBySupplier.sql**.  
  
2.  Klicken Sie in dieser Codezeile mit der rechten Maustaste auf `Products`, und wählen Sie **Gehe zu Definition** aus.  
  
    ```  
    SELECT * from Products p  
    ```  
  
3.  "Products.sql" wird automatisch geöffnet. Dabei wird die Position angezeigt, an der der `Products`-Typ definiert wird.  
  
4.  Wechseln Sie zurück zu "GetProductsBySupplier.sql". Wählen Sie dieses Mal im Kontextmenü für `Products` die Option **Alle Verweise suchen** aus. Im Bereich **Ergebnisse der Symbolsuche** wird eine Liste der Positionen angezeigt, an denen auf die Tabelle `Products` verwiesen wird. Wenn Sie auf eines der Suchergebnisse doppelklicken, springen Sie zur Position des Verweises.  
  
