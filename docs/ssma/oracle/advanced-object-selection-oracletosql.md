---
title: Erweiterte Objektauswahl (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c978fba4-c953-4ed0-a21d-1b38e7225552
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 36bf17e1667596582ed60fd6c35d6f74fc81a231
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264543"
---
# <a name="advanced-object-selection--oracletosql"></a>Erweiterte Objektauswahl (OracleToSQL)
Die **Objektabschnitt erweiterte** Dialogfeld können Sie das Filtern von Datenbankobjekten mit Zeichenfolgen und Teilzeichenfolgen in den Namen, und klicken Sie dann zu aktivieren oder deaktivieren Sie diese Objekte. SSMA führt konvertieren und Migrieren von Vorgängen für ausgewählte Objekte.  
  
Um dieses Dialogfeld zuzugreifen, mit der rechten Maustaste in einem Metadaten-Explorer, und wählen Sie dann **erweiterte Objektauswahl**.  
  
Wenn Sie das Dialogfeld zum ersten Mal öffnen, klicken Sie auf **Unterkategorien Elemente anzeigen** , alle Objekte anzuzeigen, die Metadaten, die in das Projekt geladen haben. Sie können Zeichenfolgen zum Filtern der Elemente anschließend eingeben. Geben Sie beispielsweise die Zeichenfolge "Company", um alle Elemente mit dem Namen anzuzeigen, die diese Zeichenfolge enthalten.  
  
Bevor Sie dieses Dialogfeld verwenden, empfiehlt es sich um SSMA alle Metadaten, die durch Konvertieren von Schemas oder Speichern des Projekts laden zu erzwingen.  
  
## <a name="options"></a>Optionen  
**Alle Elemente aktivieren**  
Fügt ein Häkchen neben allen Elementen hinzu. Diese Elemente werden sofort in den Metadaten-Explorer ausgewählt werden.  
  
**Deaktivieren Sie alle Elemente**  
Entfernt das Häkchen neben allen Elementen. Diese Elemente werden in den Metadaten-Explorer sofort gelöscht.  
  
**Modus der Listenansicht**  
Zeigt gefilterten Elemente in einer Liste.  
  
**Tabelle-Ansichtsmodus**  
Zeigt gefilterten Elemente in einer Tabelle.  
  
**Nur die geladenen Elemente angezeigt**  
Schaltet die Anzeige der Kategorien oder Elemente. Wenn diese Schaltfläche aktiviert ist, zeigt der SSMA alle Elemente, die die Filterkriterien erfüllen, und diejenigen, die zuvor geladen wurden entsprechen. Wenn diese Schaltfläche nicht ausgewählt ist, zeigt der SSMA die Kategorie-Ordner.  
  
**Filter**  
Geben Sie die Zeichenfolge, die Sie zum Filtern von Elementen verwenden möchten. Geben Sie z. B. um alle verfügbaren Elemente suchen, die die Zeichenfolge "ID" im Elementnamen, die Zeichenfolge "ID" in der **Filter** Feld.  
  
Wenn Elemente den Filterkriterien entsprechen, werden die Kategorien oder die Elemente angezeigt, während der Eingabe der Zeichenfolge. Um die entsprechenden Elemente anzuzeigen, wird empfohlen, dass Sie auf die **nur geladen Elemente angezeigt** Schaltfläche.  
  
**Filter löschen**  
Löscht die **Filter** Feld.  
  
