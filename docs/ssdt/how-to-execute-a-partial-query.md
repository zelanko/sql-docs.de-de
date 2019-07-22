---
title: 'Gewusst wie: Ausführen einer Teilabfrage | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2f7861e3ef232dd3f244c9c325468e6ba4d51d16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67929610"
---
# <a name="how-to-execute-a-partial-query"></a>Gewusst wie: Ausführen einer Teilabfrage
Mit dem Transact\-SQL-Editor können Sie ein bestimmtes Segment des Skripts markieren und als Einzelabfrage ausführen. Dies erleichtert das Debuggen von Abschnitten komplexer Abfragen.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-partially-execute-a-query"></a>So führen Sie eine partielle Abfrage aus  
  
1.  Doppelklicken Sie im **SQL Server-Objekt-Explorer** unter **Ansichten** auf **PerishableFruits**, um diese Ansicht im Transact\-SQL-Editor zu öffnen.  
  
2.  Markieren Sie das Segment `SELECT p.Id, p.Name FROM dbo.Product p` im Code, klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Abfrage ausführen**.  
  
3.  Alle Zeilen mit den angegebenen Feldern in der Tabelle `Products` werden im Bereich **Ergebnisse** zurückgegeben.  
  
