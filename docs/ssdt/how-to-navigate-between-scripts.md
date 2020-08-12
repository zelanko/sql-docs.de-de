---
title: Navigation zwischen Skripts
description: Hier erfahren Sie, wie Sie im Transact-SQL-Editor zwischen Skripts navigieren. Sehen Sie sich Beispiele an, die die Verwendung von Tools wie „Zu Definition wechseln“ und „Alle Verweise suchen“ darstellen.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.editor.howto.navigate
ms.assetid: 8664bde5-86ff-4e8b-b5a6-af003316f6ad
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: f0b21634e2655d67812d9c6096c9d63633130c7a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896627"
---
# <a name="how-to-navigate-between-scripts"></a>Gewusst wie: Navigation zwischen Skripts

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
  
