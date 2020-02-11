---
title: Varchar-Spaltengröße (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3a3156c3f71eb4b3f7b8319da5d5fec7514f08b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087957"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>VARCHAR-Spaltengröße (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 In Oracle8 wurde die maximale Größe einer varchar-Spalte von 2000 auf 4000 Byte angehoben. Die Oracle 7.3. x-Client Software kann einen Parameterwert, der größer als 2000 Byte ist, nicht binden. Wenn Sie also eine Tabelle mit einer Spalte vom Typ "varchar" mit mehr als 2000 Bytes erstellen, können Sie keine parametrisierten Einfügungen, Updates, Löschungen und Abfragen mit Daten ausführen, die das 2000-Byte-Limit der Client Software überschreiten. Da sowohl der ODBC-Treiber für Oracle als auch der OLE DB-Anbieter für Oracle parametrisierte Einfügungen, Updates, Löschungen und Abfragen verwenden, werden in diesem Fall Ora-01026-Fehler gemeldet. Daten, die sich innerhalb der von der Oracle-Client Software erzwungenen Grenzwerte befinden, funktionieren. Um dieses 2000-Byte-Limit zu vermeiden, müssen Sie die Client Software auf Oracle8 (8.0.4.1.1 c oder höher) aktualisieren.
