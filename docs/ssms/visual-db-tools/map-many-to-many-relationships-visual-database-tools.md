---
title: Zuordnen von m:n-Beziehungen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], many-to-many
- junction tables [SQL Server]
- many-to-many relationships [SQL Server]
- mapping many-to-many relationships [SQL Server]
- database diagrams [SQL Server], relationships
ms.assetid: 2977cf92-98b5-48b2-b0fd-8fbc7040f2b4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6abe574ebfbe031d4a5ee1aa90698b566a4f84da
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65096653"
---
# <a name="map-many-to-many-relationships-visual-database-tools"></a>Zuordnen von m:n-Beziehungen (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Durch m:n-Beziehungen können Sie jede Zeile in einer Tabelle mit mehreren Zeilen in einer anderen Tabelle verknüpfen und umgekehrt. Sie können z. B. eine m:n-Beziehung zwischen der Tabelle `authors` und der Tabelle `titles` erstellen, um einerseits allen Autoren ihre Bücher und andererseits jedem Buch alle seine Autoren zuzuordnen. Das Erstellen einer 1:n-Beziehung von einer der beiden Tabellen würde fälschlicherweise angeben, dass jedes Buch nur einen Autor besitzen oder jeder Autor nur ein Buch schreiben kann.  
  
In Datenbanken werden n:n-Beziehungen zwischen Tabellen mithilfe von Jointabellen erstellt. Eine Jointabelle enthält die Primärschlüsselspalten der beiden zu verknüpfenden Tabellen. Erstellen Sie dann eine Beziehung von den Primärschlüsselspalten beider Tabellen zu den korrespondierenden Spalten in der Jointabelle. In der Datenbank Pubs handelt es sich bei der Tabelle `titleauthor` um eine Jointabelle.  
  
### <a name="to-create-a-many-to-many-relationship-between-tables"></a>So erstellen Sie eine m:n-Beziehung zwischen Tabellen  
  
1.  Fügen Sie im Datenbankdiagramm die Tabellen hinzu, zwischen denen Sie eine m:n-Beziehung erstellen möchten.  
  
2.  Erstellen Sie eine dritte Tabelle, indem Sie mit rechten Maustaste auf das Diagramm klicken und anschließend im Kontextmenü **Neue Tabelle** auswählen. Die neue Tabelle fungiert als Jointabelle.  
  
3.  Ändern Sie im Dialogfeld **Namen auswählen** den vom System zugewiesenen Tabellennamen. Die Jointabelle zwischen der Tabelle `titles` und der Tabelle `authors` heißt jetzt `titleauthors`.  
  
4.  Kopieren Sie die Primärschlüsselspalten aus den beiden anderen Tabellen in die Jointabelle. Sie können der Jointabelle wie jeder anderen Tabelle weitere Spalten hinzufügen.  
  
5.  Der Primärschlüssel in der Jointabelle muss sämtliche Primärschlüsselspalten aus den beiden anderen Tabellen enthalten. Detaillierte Informationen zu diesem Thema finden Sie unter [Vorgehensweise: Erstellen von Primärschlüsseln](https://msdn.microsoft.com/85c623ca-4656-4d70-a9db-ee4d897cd214).  
  
6.  Definieren Sie zwischen beiden Primärtabellen und der Jointabelle jeweils eine 1:n-Beziehung. Die Jointabelle muss in beiden Beziehungen die n-Seite darstellen. Detaillierte Informationen zu diesem Thema finden Sie unter [Vorgehensweise: Erstellen von Fremdschlüssel-Beziehungen](https://msdn.microsoft.com/867a54b8-5be4-46e6-9702-49ae6dabf67c).  
  
    > [!NOTE]  
    > Beim Erstellen einer Jointabelle in einem Datenbankdiagramm werden keine Daten aus den verknüpften Tabellen in die Jointabelle eingefügt. Informationen zum Einfügen von Daten in eine Tabelle finden Sie unter [Erstellen von Abfragen zum Einfügen von Ergebnissen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-insert-results-queries-visual-database-tools.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwenden von Datenbankdiagrammen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
  
