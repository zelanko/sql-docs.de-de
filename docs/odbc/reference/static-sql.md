---
title: Statische SQL-Anweisungen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: cd82e2c3c44f05a27e9d14442d8d0fb58e1986cc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63232052"
---
# <a name="static-sql"></a>Statische SQL-Anweisungen
Siehe eingebettete SQL [eingebettete SQL-Beispiel](../../odbc/reference/embedded-sql-example.md) wird als statische SQL-Anweisungen bezeichnet. Es heißt statische SQL-Anweisungen, da die SQL-Anweisungen in der Anwendung statisch sind; Sie, also nicht jedes Mal ändern, die das Programm ausgeführt wird. Wie im vorherigen Abschnitt beschrieben wird, werden diese Anweisungen kompiliert, wenn der Rest des Programms kompiliert wird.  
  
 Statische SQL-Anweisungen funktioniert gut in vielen Situationen und kann verwendet werden, in jeder Anwendung, die für die Datenzugriff zur Entwurfszeit Programm bestimmt werden kann. Z. B. eine Order-Eintrag-Anwendung verwendet immer der gleichen Anweisung zum Einfügen einer neuen Bestellung, und ein Fluglinien-Reservierungssystem verwendet immer die gleiche Anweisung so ändern Sie den Status des einen Arbeitsplatz aus zur reserviert. Alle diese Anweisungen wird durch die Verwendung von Hostvariablen generalisiert werden; unterschiedliche Werte in einem Verkaufsauftrag eingefügt werden können, und verschiedene Plätze reserviert werden können. Da diese Anweisungen in der Anwendung hartcodiert sein können, müssen solche Programme den Vorteil, den dass die Anweisungen analysiert, überprüft und nur einmal zum Zeitpunkt der Kompilierung optimiert werden müssen. Dies führt zu einer relativ schnellen Code bevorzugen.
