---
title: 'Lektion 1: Konvertieren einer Tabelle in eine hierarchische Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0dc3ade6d7473dc354131772c9d17d504afcabd2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175420"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Lektion 1: Konvertieren einer Tabelle in eine hierarchische Struktur
  Kunden mit Tabellen, die hierarchische Beziehungen mithilfe von Selbstjoins darstellen, können diese Tabellen in eine hierarchische Struktur konvertieren, indem Sie diese Lektion als Richtlinie verwenden. Es ist relativ einfach, die von dieser Darstellung zu einer mit migrieren `hierarchyid`. Nach der Migration verfügen die Benutzer über ein grundlegendes Verständnis hierarchischer Darstellungen, die für effizientere Abfragen auf verschiedene Weise indiziert werden können.  
  
 Dieser Lektion werden Sie eine vorhandene Tabelle untersucht, erstellt eine neue Tabelle mit einer `hierarchyid` Spalte füllt die Tabelle mit den Daten aus der Quelltabelle und schließlich werden drei indizierungsstrategien dargestellt. Diese Lektion enthält die folgenden Themen:  
  
-   [Untersuchen der aktuellen Struktur der Mitarbeitertabelle](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Auffüllen einer Tabelle mit vorhandenen hierarchischen Daten](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Optimieren der NewOrg-Tabelle](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Zusammenfassung: Konvertieren einer Tabelle in eine hierarchische Struktur](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Für diese Lektion benötigen Sie die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Untersuchen der aktuellen Struktur der Mitarbeitertabelle](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Erstellen und Verwalten von Daten in einer hierarchischen Tabelle](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
