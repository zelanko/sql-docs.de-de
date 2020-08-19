---
description: Was ist ein Cursor?
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a3fabe19ad59f7e1ee6b24f278c7a5edf1985db6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452542"
---
# <a name="what-is-a-cursor"></a>Was ist ein Cursor?
Vorgänge in einer relationalen Datenbank beziehen sich immer auf eine vollständige Gruppe von Zeilen. Die von einer SELECT-Anweisung zurückgegebene Gruppe von Zeilen besteht aus allen Zeilen, die die Bedingungen der WHERE-Klausel der Anweisung erfüllen. Diese vollständige Gruppe von Zeilen, die von der Anweisung zurückgegeben wird, wird als Resultset bezeichnet. Anwendungen, vor allem interaktive und Online Anwendungen, können nicht immer effektiv mit dem gesamten Resultset als Einheit arbeiten. Diese Anwendungen benötigen einen Mechanismus, um jeweils eine Zeile oder einen kleinen Zeilenblock zu bearbeiten. Cursor sind eine Erweiterung zu Resultsets und stellen diesen Mechanismus bereit.  
  
 Ein Cursor wird durch eine Cursor Bibliothek implementiert. Eine Cursor Bibliothek ist Software, die häufig als Teil eines Datenbanksystems oder einer Datenzugriffs-API implementiert wird und zum Verwalten von Attributen von Daten verwendet wird, die von einer Datenquelle (einem Resultset) zurückgegeben werden. Diese Attribute umfassen neben läufigkeits Verwaltung, Position im Resultset, Anzahl der zurückgegebenen Zeilen und ob vorwärts-oder rückwärts (oder beides) durch das Resultset (Scrollbarkeit) verschoben werden können.  
  
 Ein Cursor verfolgt die Position im Resultset nach und ermöglicht es Ihnen, mehrere Vorgänge zeilenweise für ein Resultset mit oder auszuführen, ohne zur ursprünglichen Tabelle zurückzukehren. Das heißt, dass Cursor konzeptionell ein Resultset zurückgeben, das auf Tabellen in den Datenbanken basiert. Der Cursor ist so benannt, weil er die aktuelle Position im Resultset anzeigt, genauso wie der Cursor auf einem Computerbildschirm die aktuelle Position anzeigt.  
  
 Es ist wichtig, sich mit dem Konzept der Cursor vertraut zu machen, bevor Sie fortfahren, um sich mit den Besonderheiten der Verwendung in ADO vertraut zu machen.  
  
 Mit Cursorn können Sie folgende Aktionen ausführen:  
  
-   Angeben der Positionierung an bestimmten Zeilen im Resultset.  
  
-   Abrufen einer Zeile oder eines Zeilen Blocks basierend auf der aktuellen Position des Resultsets.  
  
-   Ändern Sie die Daten in den Zeilen an der aktuellen Position im Resultset.  
  
-   Definieren Sie unterschiedliche Empfindlichkeitsstufen für Datenänderungen, die von anderen Benutzern vorgenommen wurden.  
  
 Stellen Sie sich z. b. eine Anwendung vor, die eine Liste der verfügbaren Produkte für einen potenziellen Käufer anzeigt. Der Käufer führt einen Bildlauf durch die Liste durch, um Produktdetails und Kosten anzuzeigen, und wählt schließlich ein Produkt für den Kauf aus. Für den Rest der Liste ist ein zusätzlicher Bildlauf und eine Auswahl erfolgt. Wenn sich der Käufer beschäftigt, werden die Produkte nacheinander angezeigt, aber die Anwendung verwendet einen Bild lauffähigen Cursor, um das Resultset nach oben und unten zu durchsuchen.  
  
 Cursor können auf verschiedene Arten verwendet werden:  
  
-   Ohne Zeilen.  
  
-   Mit einigen oder allen Zeilen in einer einzelnen Tabelle.  
  
-   Mit einigen oder allen Zeilen aus logisch verbundenen Tabellen.  
  
-   Schreibgeschützt oder aktualisierbar auf Cursor-oder Feldebene.  
  
-   Als vorwärts oder vollständig ScrollBar.  
  
-   Mit dem Cursor-Keyset, das sich auf dem Server befindet.  
  
-   Sensible Informationen zu zugrunde liegenden Tabellen Änderungen, die von anderen Anwendungen (z. b. Mitgliedschaft, Sortierung, Einfügungen, Updates und Löschungen) verursacht werden.  
  
-   Auf dem Server oder dem Client vorhanden.  
  
 Schreibgeschützte Cursor helfen Benutzern, das Resultset zu durchsuchen, und mit Lese-/schreibcursorn können einzelne Zeilen Aktualisierungen implementiert werden. Komplexe Cursor können mit Keysets definiert werden, die auf Basistabellen Zeilen zurückverweisen. Obwohl einige Cursor in Vorwärtsrichtung schreibgeschützt sind, können andere Benutzer hin und her wechseln und eine dynamische Aktualisierung des Resultsets auf der Grundlage von Änderungen bereitstellen, die andere Anwendungen an der Datenbank vornehmen.  
  
 Nicht alle Anwendungen müssen Cursor verwenden, um auf Daten zuzugreifen oder diese zu aktualisieren. Einige Abfragen erfordern einfach keine direkte Zeilen Aktualisierung mithilfe eines Cursors. Bei Cursorn sollte es sich um eine der letzten Verfahren handeln, die Sie zum Abrufen von Daten auswählen. Anschließend sollten Sie den möglichen Cursor mit der niedrigsten Auswirkung auswählen. Wenn Sie mithilfe einer gespeicherten Prozedur ein Resultset erstellen, kann das Resultset nicht mithilfe von Cursor Bearbeitungs-oder Update Methoden aktualisiert werden.  
  
## <a name="concurrency"></a>Parallelität  
 Bei einigen mehr Benutzer Anwendungen ist es sehr wichtig, dass die Daten, die dem Endbenutzer angezeigt werden, so aktuell wie möglich sind. Ein klassisches Beispiel für ein solches System ist ein Reservierungssystem für die Fluggesellschaft, bei dem viele Benutzer möglicherweise für denselben Arbeitsplatz auf einem bestimmten Flug (und somit einem einzelnen Datensatz) in Konflikt stehen. In einem solchen Fall muss der Anwendungs Entwurf gleichzeitige Vorgänge für einen einzelnen Datensatz verarbeiten.  
  
 In anderen Anwendungen ist Parallelität nicht so wichtig. In solchen Fällen können die Kosten für das aktuelle aufbewahren der Daten nicht gerechtfertigt werden.  
  
## <a name="position"></a>Position  
 Ein Cursor verfolgt auch die aktuelle Position in einem Resultset. Stellen Sie sich die Cursorposition als Zeiger auf den aktuellen Datensatz vor, ähnlich der Art, wie ein Array Index auf den Wert an dieser bestimmten Position im Array zeigt.  
  
## <a name="scrollability"></a>Bildlauffähigkeit  
 Der Cursor, der von der Anwendung verwendet wird, wirkt sich auch auf die Möglichkeit aus, die Zeilen in einem Resultset vorwärts und rückwärts zu bewegen. Dies wird manchmal als Scrollbarkeit bezeichnet. Die Möglichkeit, ein Resultset vorwärts *und* rückwärts zu bewegen, erhöht die Komplexität des Cursors und ist daher kostengünstiger zu implementieren. Aus diesem Grund sollten Sie nur bei Bedarf einen Cursor mit dieser Funktionalität anfordern.
