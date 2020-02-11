---
title: Entwerfen von Datenbankdiagrammen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65536
- vdt.DatabaseDesigner
helpviewer_keywords:
- Database Diagram Designer
- Visual Database Tools [SQL Server], database diagrams
- database diagrams [SQL Server], designing
- diagrams [SQL Server], designing
ms.assetid: 6d2c14e1-3d73-4d10-ae5b-7f2b5d6c4ea8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e348ace954e19c3e213c7de1779cbfbcb1768887
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63316101"
---
# <a name="design-database-diagrams-visual-database-tools"></a>Entwerfen von Datenbankdiagrammen (Visual Database Tools)
  Der Datenbank-Designer ist ein visuelles Tool, mit dem Sie eine Datenbank, mit der eine Verbindung besteht, entwerfen und anzeigen lassen können. Beim Entwerfen einer Datenbank können Sie mithilfe des Datenbank-Designers Tabellen, Spalten, Schlüssel, Indizes, Beziehungen und Einschränkungen erstellen, bearbeiten oder löschen. Zur Darstellung einer Datenbank können Sie ein oder mehrere Diagramme erstellen, die die Tabellen, Spalten, Schlüssel oder Beziehungen innerhalb der Datenbank teilweise oder ganz anzeigen.  
  
 ![Datenbankdiagramm zur Illustration von Tabellenbeziehungen](../../database-engine/media//dv3w7c1.gif "Datenbankdiagramm zur Illustration von Tabellenbeziehungen")  
  
 Sie können für jede Datenbank beliebig viele Datenbankdiagramme erstellen, und jede Datenbanktabelle kann in einer beliebigen Anzahl von Diagrammen angezeigt werden. Daher können Sie verschiedene Diagramme erstellen, um unterschiedliche Bereiche der Datenbank darzustellen oder unterschiedliche Aspekte des Entwurfs hervorzuheben. Sie können z. B. ein umfangreiches Diagramm erstellen, in dem alle Tabellen und Spalten angezeigt werden, und ein kleineres Diagramm, in dem die Tabellen ohne ihre Spalten dargestellt sind.  
  
 Jedes erstellte Diagramm wird in der zugehörigen Datenbank gespeichert.  
  
## <a name="tables-and-columns-in-a-database-diagram"></a>Tabellen und Spalten in einem Datenbankdiagramm  
 Innerhalb eines Datenbankdiagramms können Tabellen mit drei unterschiedlichen Merkmalen angezeigt werden: einer Titelleiste, einem Zeilenselektor und einer Reihe von Eigenschaftenspalten.  
  
 **Titelleiste** In der Titelleiste wird der Name der Tabelle angezeigt.  
  
 Wenn Sie in einer Tabelle Änderungen vorgenommen und diese noch nicht gespeichert haben, wird am Ende des Tabellennamens ein Sternchen (*) angezeigt, um so auf ungespeicherte Änderungen hinzuweisen. Informationen zum Speichern von geänderten Tabellen und Diagrammen finden Sie unter [Verwenden von Datenbankdiagrammen &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
 **Zeilenauswahl** Sie können auf den Zeilenselektor klicken, um eine Daten Bank Spalte in der Tabelle auszuwählen. Der Zeilenselektor zeigt ein Symbol in Form eines Schlüssels an, wenn sich die Spalte im Primärschlüssel der Tabelle befindet. Informationen zu primär Schlüsseln finden Sie unter [Primary-und FOREIGN KEY-Einschränkungen](../../relational-databases/tables/primary-and-foreign-key-constraints.md).  
  
 **Eigenschafts Spalten** Der Satz von Eigenschafts Spalten ist nur in den bestimmten Ansichten der Tabelle sichtbar. Sie können sich eine Tabelle in fünf verschiedenen Sichten anzeigen lassen, um dann die Größe und das Layout des betreffenden Diagramms verwalten zu können.  
  
 Weitere Informationen zu Tabellensichten finden Sie unter [Anpassen des Umfangs der in Diagrammen angezeigten Informationen &#40;Visual Database Tools&#41;](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md).  
  
## <a name="relationships-in-a-database-diagram"></a>Beziehungen in einem Datenbankdiagramm  
 Innerhalb eines Datenbankdiagramms können Eigenschaften mit drei unterschiedlichen Merkmalen angezeigt werden: Endpunkte, eine bestimmte Linienart und verknüpfte Tabellen.  
  
 **Endpunkte** Die Endpunkte der Zeile geben an, ob die Beziehung eins-zu-eins-oder 1: n-Beziehung ist. Wenn eine Beziehung einen Schlüssel an einem Endpunkt und ein Unendlichkeitszeichen am anderen Endpunkt aufweist, handelt es sich um eine 1:n-Beziehung. Wenn eine Beziehung an jedem Endpunkt einen Schlüssel aufweist, handelt es sich um eine 1:1-Beziehung.  
  
 **Linienart** Die Zeile selbst (nicht ihre Endpunkte) gibt an, ob das Datenbank-Management System (DBMS) die referenzielle Integrität für die Beziehung erzwingt, wenn der Fremdschlüssel Tabelle neue Daten hinzugefügt werden. Bei einer durchgezogenen Linie erzwingt das DBMS die referenzielle Integrität für die Beziehung, wenn Zeilen in der Fremdschlüsseltabelle hinzugefügt oder geändert werden. Bei einer gepunkteten Linie erzwingt das DBMS keine referenzielle Integrität für die Beziehung, wenn Zeilen in der Fremdschlüsseltabelle hinzugefügt oder bearbeitet werden.  
  
 Verknüpfte **Tabellen** Die Beziehungs Linie gibt an, dass eine Fremdschlüssel Beziehung zwischen einer Tabelle und einer anderen Tabelle vorhanden ist. Bei einer 1:n-Beziehung ist die Fremdschlüsseltabelle die Tabelle neben dem Unendlichkeitszeichen der Linie. Wenn beide Endpunkte der Linie mit derselben Tabelle verbunden sind, handelt es sich um eine reflexive Beziehung. Weitere Informationen finden Sie unter [Zeichnen reflexiver Beziehungen &#40;Visual Database Tools&#41;](draw-reflexive-relationships-visual-database-tools.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Grundlagen des Besitzes von Datenbankdiagrammen &#40;Visual Database Tools&#41;](understand-database-diagram-ownership-visual-database-tools.md)  
  
 [Navigieren Sie im Daten Bank Diagramm-Designer &#40;Visual Database Tools&#41;](navigate-in-database-diagram-designer-visual-database-tools.md)  
  
 [Einrichten des Daten Bank Diagramm-Designers &#40;Visual Database Tools&#41;](set-up-database-diagram-designer-visual-database-tools.md)  
  
 [Aktualisieren von Datenbankdiagrammen aus älteren Versionen &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
  
 [Öffnen Sie den Daten Bank Diagramm-Designer &#40;Visual Database Tools&#41;](open-database-diagram-designer-visual-database-tools.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Daten Bank Diagrammen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Arbeiten mit Tabellen im Daten Bank Diagramm &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md)   
 [Verwenden von Diagrammlayout &#40;Visual Database Tools&#41;](work-with-diagram-layout-visual-database-tools.md)  
  
  
