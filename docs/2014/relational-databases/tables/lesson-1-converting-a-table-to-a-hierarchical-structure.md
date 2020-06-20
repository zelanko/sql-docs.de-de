---
title: 'Lektion 1: Konvertieren einer Tabelle in eine hierarchische Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd6f1d123bca9f9f0c10288e0b58dd075c7b0949
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068063"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Lektion 1: Konvertieren einer Tabelle in eine hierarchische Struktur
  Kunden mit Tabellen, die hierarchische Beziehungen mithilfe von Selbstjoins darstellen, können diese Tabellen in eine hierarchische Struktur konvertieren, indem Sie diese Lektion als Richtlinie verwenden. Es ist relativ leicht, von dieser Darstellung zu einer mit `hierarchyid` zu migrieren. Nach der Migration verfügen die Benutzer über ein grundlegendes Verständnis hierarchischer Darstellungen, die für effizientere Abfragen auf verschiedene Weise indiziert werden können.  
  
 In dieser Lektion wird eine vorhandene Tabelle untersucht und eine neue Tabelle mit einer `hierarchyid`-Spalte erstellt. Daraufhin wird diese Tabelle mit den Daten der Quelltabelle gefüllt, und schließlich werden drei Indizierungsstrategien dargestellt. Diese Lektion enthält die folgenden Themen:  
  
-   [Untersuchen der aktuellen Struktur der Mitarbeitertabelle](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Auffüllen einer Tabelle mit vorhandenen hierarchischen Daten](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Optimieren der NewOrg-Tabelle](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Zusammenfassung: Konvertieren einer Tabelle in eine hierarchische Struktur](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Für diese Lektion benötigen Sie die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Untersuchen der aktuellen Struktur der Mitarbeitertabelle](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Erstellen und Verwalten von Daten in einer hierarchischen Tabelle](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
