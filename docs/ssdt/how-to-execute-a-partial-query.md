---
title: Ausführen einer Teilabfrage
description: Dieser Artikel enthält weitere Informationen zum Debuggen von Abschnitten in komplexen Abfragen. Er beschreibt, wie Sie mit dem Transact-SQL-Editor ein bestimmtes Skriptsegment markieren und als Einzelabfrage ausführen.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: f9aaa7712726b37d03c7d7de0994bb8abe01a7d9
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2020
ms.locfileid: "85518800"
---
# <a name="how-to-execute-a-partial-query"></a>Gewusst wie: Ausführen einer Teilabfrage

Mit dem Transact\-SQL-Editor können Sie ein bestimmtes Segment des Skripts markieren und als Einzelabfrage ausführen. Dies erleichtert das Debuggen von Abschnitten komplexer Abfragen.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
## <a name="to-partially-execute-a-query"></a>So führen Sie eine partielle Abfrage aus  
  
1. Doppelklicken Sie im **SQL Server-Objekt-Explorer** unter **Ansichten** auf **PerishableFruits**, um diese Ansicht im Transact\-SQL-Editor zu öffnen.  
  
2. Markieren Sie das Segment `SELECT p.Id, p.Name FROM dbo.Product p` im Code, klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Abfrage ausführen**.  
  
3. Alle Zeilen mit den angegebenen Feldern in der Tabelle `Products` werden im Bereich **Ergebnisse** zurückgegeben.