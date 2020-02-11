---
title: Statisches SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e6d053e4d2a5520432c4c1debbafb35fdb17bc4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68016737"
---
# <a name="static-sql"></a>Statische SQL-Anweisungen
Das in [eingebettetes SQL-Beispiel](../../odbc/reference/embedded-sql-example.md) gezeigte eingebettete SQL-Beispiel wird als statisches SQL bezeichnet. Sie wird als statisches SQL bezeichnet, da die SQL-Anweisungen im Programm statisch sind. Das heißt, dass Sie sich nicht bei jedem Ausführen des Programms ändern. Wie im vorherigen Abschnitt beschrieben, werden diese Anweisungen kompiliert, wenn der Rest des Programms kompiliert wird.  
  
 Statisches SQL funktioniert in vielen Situationen gut und kann in jeder Anwendung verwendet werden, für die der Datenzugriff zur Programmentwurfs Zeit bestimmt werden kann. Beispielsweise verwendet ein Order-Entry-Programm immer dieselbe Anweisung, um einen neuen Auftrag einzufügen, und ein Reservierungssystem für die Fluggesellschaft verwendet immer dieselbe Anweisung, um den Status eines Arbeitsplatzes von verfügbar in reserviert zu ändern. Jede dieser Anweisungen wird durch die Verwendung von Host Variablen generalisiert. unterschiedliche Werte können in einem Verkaufsauftrag eingefügt werden, und unterschiedliche Arbeitsplätze können reserviert werden. Da solche Anweisungen im Programm hart codiert werden können, haben solche Programme den Vorteil, dass die Anweisungen zum Zeitpunkt der Kompilierung analysiert, überprüft und nur einmal optimiert werden müssen. Dies führt zu relativ schnellem Code.
