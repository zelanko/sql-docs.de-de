---
title: Kopieren von Tabellen von einem Datenbankdiagramm in ein anderes
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 887cc2cdb2d70b0d69599d75d8534907552cb201
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75254393"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a>Kopieren von Tabellen von einem Datenbankdiagramm in ein anderes Datenbankdiagramm (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Sie können eine Tabelle innerhalb derselben Datenbank von einem Datenbankdiagramm in ein anderes kopieren.  
  
Durch das Kopieren einer Tabelle von einem Datenbankdiagramm in ein anderes Diagramm wird letzterem ein Verweis auf die Tabelle hinzugefügt. Die Tabelle wird jedoch nicht in die Datenbank dupliziert. Wenn Sie beispielsweise die Tabelle `authors` von einem Datenbankdiagramm in ein anderes kopieren, verweisen beide Diagramme auf dieselbe Tabelle `authors` in der Datenbank.  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a>So kopieren Sie eine Tabelle von einem anderen Datenbankdiagramm  
  
1.  Vergewissern Sie sich, dass Sie mit der Datenbank verbunden sind, deren Tabelle Sie kopieren möchten.  
  
2.  Öffnen Sie im Ausgangsdiagramm sowohl das Ausgangs- als auch das Zieldiagramm, und markieren Sie die Tabelle, die in das Zieldiagramm kopiert werden soll.  
  
3.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Kopieren** . Dadurch wird die ausgewählte Tabellendefinition in die Zwischenablage kopiert.  
  
4.  Wechseln Sie zum Zieldiagramm. Dieses Diagramm muss sich in derselben Datenbank befinden wie das Ausgangsdiagramm.  
  
5.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Einfügen** . Der Inhalt der Zwischenablage wird nun an der neuen Stelle angezeigt und bleibt hervorgehoben, bis Sie auf eine andere Stelle klicken. Wenn Beziehungen zwischen den ausgewählten Tabellen und anderen Tabellen im Zieldiagramm bestehen, werden automatisch Beziehungslinien gezogen.  
  
Wenn Sie die Tabelle in einem der beiden Diagramme bearbeiten, wirken sich die Änderungen auf beide Diagramme aus. Ähnliches gilt für das Speichern der Tabelle. Wenn Sie die Tabelle in einem der beiden Diagramme speichern, gilt sie in beiden Diagrammen nicht mehr als "verändert".  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwenden von Datenbankdiagrammen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Hinzufügen von Tabellen zu Diagrammen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
