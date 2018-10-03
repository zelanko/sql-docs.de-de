---
title: Was ist ein Cursor? | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], about cursors
ms.assetid: 596eb4b6-c22f-4cde-b23f-172dd66c3161
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b58446a00300548b0b61defefb71d3207359787a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770770"
---
# <a name="what-is-a-cursor"></a>Was ist ein Cursor?
Vorgänge in einer relationalen Datenbank beziehen sich immer auf eine vollständige Gruppe von Zeilen. Die von einer SELECT-Anweisung zurückgegebene Gruppe von Zeilen besteht aus allen Zeilen, die die Bedingungen der WHERE-Klausel der Anweisung erfüllen. Diese vollständige Gruppe von Zeilen, die von der Anweisung zurückgegeben wird, wird als Resultset bezeichnet. Anwendungen, insbesondere über diejenigen, die interaktiv und online ist, sind bearbeitet nicht immer effektiv das gesamte Resultset als eine Einheit. Diese Anwendungen benötigen einen Mechanismus, um jeweils eine Zeile oder einen kleinen Zeilenblock zu bearbeiten. Cursor sind eine Erweiterung zu Resultsets und stellen diesen Mechanismus bereit.  
  
 Ein Cursor wird durch einen Cursor-Bibliothek implementiert. Eine Cursor-Bibliothek ist Software, die häufig als Bestandteil eines Datenbanksystems oder eine Datenzugriffs-API implementiert, die verwendet wird, zur Verwaltung von Attributen der Daten aus einer Datenquelle (ein Resultset) zurückgegeben. Diese Attribute umfassen die parallelitätsverwaltung, position im Resultset, Anzahl der Zeilen zurückgegeben, und gibt an, ob vorwärts oder rückwärts verschoben werden können (oder beides) legen Sie über das Ergebnis (bildlauffähigkeit).  
  
 Ein Cursor verfolgt des die Position im Resultset, und ermöglicht Ihnen, mehrere Vorgänge Zeile für Zeile mit einem Resultset mit oder ohne Rückgabe an die ursprüngliche Tabelle durchzuführen. Cursor zurück also im Prinzip ein Resultset basierend auf Tabellen in Datenbanken. Der Cursor ist so genannt, da wird von der aktuellen Position im Resultset, genau wie der Cursor auf einem Computerbildschirm aktuelle Position anzeigt.  
  
 Es ist wichtig, die mit dem Konzept von Cursorn vertraut wird, bevor Sie mit ihrer Verwendung in ADO die Einzelheiten erfahren Sie mehr.  
  
 Verwenden von Cursorn, können Sie die folgenden Schritte ausführen:  
  
-   Geben Sie die Positionierung an bestimmten Zeilen im Resultset.  
  
-   Abrufen einer Zeile oder einen Block von Zeilen auf Grundlage der aktuellen Position des Ergebnis-Satz.  
  
-   Ändern von Daten in den Zeilen an der aktuellen Position im Resultset.  
  
-   Definieren Sie verschiedene Ebenen der Vertraulichkeit, auf die von anderen Benutzern vorgenommene datenänderungen.  
  
 Betrachten Sie beispielsweise eine Anwendung, die eine Liste der verfügbaren Produkte für ein potenzieller Käufer anzeigt. Der Käufer scrollt durch die Liste, um Produktdetails und Kosten anzuzeigen, und schließlich wählt ein Produkt erworben. Zusätzliche Durchführen eines Bildlaufs und Auswahl tritt auf, für den Rest der Liste. Als Käufer betroffen ist, die Produkte angezeigt werden, einzeln nacheinander, aber die Anwendung einen bildlauffähigen Cursor verwendet, können Sie um das Resultset nach oben oder unten zu durchsuchen.  
  
 Sie können den Cursor in einer Vielzahl von Möglichkeiten verwenden:  
  
-   Ohne Zeilen überhaupt.  
  
-   Mit einigen oder allen Zeilen in einer einzelnen Tabelle.  
  
-   Mit einigen oder allen Zeilen aus logisch verknüpfte Tabellen.  
  
-   Als schreibgeschützt oder aktualisierbar Ebene der Cursor oder ein Feld.  
  
-   Als Vorwärtscursor oder voll bildlauffähigen Cursor.  
  
-   Mit das Keyset des Cursors befindet sich auf dem Server.  
  
-   Anfällig für den zugrunde liegenden Tabelle ändern, die von anderen Anwendungen (z. B. Mitgliedschaft, sortieren, einfügungen, Updates und löschungen) verursacht werden.  
  
-   Vorhandene auf dem Server oder Client.  
  
 Nur-Lese Cursor unterstützen von Benutzern über das Resultset navigieren und Lese-/Schreibzugriff, dass Cursor einzelne zeilenupdates implementieren können. Komplexe Cursor können mit Keysets definiert werden, die verweisen zurück auf die Tabellenzeilen basieren. Obwohl einige Cursor vorwärts, schreibgeschützt sind, können andere hin-und herwechseln und geben Sie eine dynamische Aktualisierung des Resultsets basierend auf Änderungen, die auf anderen Anwendungen in der Datenbank alle.  
  
 Nicht alle Anwendungen müssen Cursor an, die Zugriff oder Aktualisieren von Daten verwenden. Einige Abfragen erfordern keine einfach das Umleiten der Zeile zu aktualisieren, durch Verwenden eines Cursors. Cursor muss eine der letzten Techniken, die Sie auswählen, um Daten abzurufen, und wählen Sie dann den geringsten Auswirkungen Cursor möglich. Wenn Sie ein Resultset mit einer gespeicherten Prozedur erstellen, ist das Resultset nicht aktualisierbare Cursor verwenden bearbeiten oder Methoden zu aktualisieren.  
  
## <a name="concurrency"></a>Parallelität  
 In einigen Anwendungen von mehreren Benutzern ist es sehr wichtig, für die Daten angezeigt, die für den Endbenutzer so aktuell wie möglich sein. Ein klassisches Beispiel eines solchen Systems ist ein Fluglinien-Reservierungssystem, in denen viele Benutzer Absicherung werden können, für den gleichen Platz für einen bestimmten Flug (und somit einen einzelnen Datensatz). In einem Fall wie folgt muss das Anwendungsdesign gleichzeitige Vorgänge auf einem einzelnen Datensatz behandeln.  
  
 In anderen Anwendungen ist die Parallelität nicht so wichtig. In solchen Fällen kann nicht behalten, die die aktuellen Daten zu jeder Zeit der Aufwand gerechtfertigt sein.  
  
## <a name="position"></a>Position  
 Ein Cursor verfolgt des auch die aktuelle Position in einem Resultset. Stellen Sie sich die Cursorposition als Zeiger auf den aktuellen Datensatz, der ähnlich wie ein Array Index verweist auf den Wert an einer bestimmten Position im Array.  
  
## <a name="scrollability"></a>Bildlauffähigkeit  
 Der Typ des Cursors, die von der Anwendung verwendete wirkt sich auch die Möglichkeit, vorwärts und rückwärts durch die Zeilen in einem Resultset zu verschieben; Dies wird manchmal als scrolloptionen bezeichnet. Die Möglichkeit, die dann vorwärts bewegt, *und* rückwärts durch die ein Ergebnis Gruppe, die Komplexität des Cursors hinzugefügt, und ist daher teurer zu implementieren. Aus diesem Grund sollten Sie einen Cursor mit dieser Funktionalität, die nur bei Bedarf anfordern.
