---
title: Statische SQL | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55710d8ea734cba86ae5e4daa725f75e94e65a64
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81279902"
---
# <a name="static-sql"></a>Statische SQL-Anweisungen
Die eingebettete SQL, die in [Embedded SQL-Beispiel](../../odbc/reference/embedded-sql-example.md) angezeigt wird, wird als statischeSQL bezeichnet. Es wird als static SQL bezeichnet, da die SQL-Anweisungen im Programm statisch sind. das heißt, sie ändern sich nicht jedes Mal, wenn das Programm ausgeführt wird. Wie im vorherigen Abschnitt beschrieben, werden diese Anweisungen kompiliert, wenn der Rest des Programms kompiliert wird.  
  
 Statisches SQL funktioniert in vielen Situationen gut und kann in jeder Anwendung verwendet werden, für die der Datenzugriff zur Programmentwurfszeit bestimmt werden kann. Beispielsweise verwendet ein Auftragserfassungsprogramm immer dieselbe Anweisung, um einen neuen Auftrag einzufügen, und ein Reservierungssystem für Fluggesellschaften verwendet immer dieselbe Anweisung, um den Status eines Sitzplatzes von verfügbar in reserviert zu ändern. Jede dieser Anweisungen würde durch die Verwendung von Hostvariablen verallgemeinert werden. verschiedene Werte können in einen Auftrag eingefügt werden, und verschiedene Sitzplätze können reserviert werden. Da solche Anweisungen im Programm hartcodiert werden können, haben solche Programme den Vorteil, dass die Anweisungen nur einmal zur Kompilierung analysiert, validiert und optimiert werden müssen. Dies führt zu relativ schnellem Code.
