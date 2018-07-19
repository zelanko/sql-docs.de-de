---
title: 'Gewusst wie: Ausführen einer Teilabfrage | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84598f015ae1c70276f5ed546674aaa4b43e4bc3
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094177"
---
# <a name="how-to-execute-a-partial-query"></a>Vorgehensweise: Ausführen einer partiellen Abfrage
Mit dem Transact\-SQL-Editor können Sie ein bestimmtes Segment des Skripts markieren und als Einzelabfrage ausführen. Dies erleichtert das Debuggen von Abschnitten komplexer Abfragen.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-partially-execute-a-query"></a>So führen Sie eine partielle Abfrage aus  
  
1.  Doppelklicken Sie im **SQL Server-Objekt-Explorer** unter **Ansichten** auf **PerishableFruits**, um diese Ansicht im Transact\-SQL-Editor zu öffnen.  
  
2.  Markieren Sie das Segment `SELECT p.Id, p.Name FROM dbo.Product p` im Code, klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Abfrage ausführen**.  
  
3.  Alle Zeilen mit den angegebenen Feldern in der Tabelle `Products` werden im Bereich **Ergebnisse** zurückgegeben.  
  
