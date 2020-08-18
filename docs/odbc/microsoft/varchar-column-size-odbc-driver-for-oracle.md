---
description: VARCHAR-Spaltengröße (ODBC-Treiber für Oracle)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c490487f0edb15fe7d7165b79c4c5f1730a0dd22
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449062"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>VARCHAR-Spaltengröße (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 In Oracle8 wurde die maximale Größe einer varchar-Spalte von 2000 auf 4000 Byte angehoben. Die Oracle 7.3. x-Client Software kann einen Parameterwert, der größer als 2000 Byte ist, nicht binden. Wenn Sie also eine Tabelle mit einer Spalte vom Typ "varchar" mit mehr als 2000 Bytes erstellen, können Sie keine parametrisierten Einfügungen, Updates, Löschungen und Abfragen mit Daten ausführen, die das 2000-Byte-Limit der Client Software überschreiten. Da sowohl der ODBC-Treiber für Oracle als auch der OLE DB-Anbieter für Oracle parametrisierte Einfügungen, Updates, Löschungen und Abfragen verwenden, werden in diesem Fall Ora-01026-Fehler gemeldet. Daten, die sich innerhalb der von der Oracle-Client Software erzwungenen Grenzwerte befinden, funktionieren. Um dieses 2000-Byte-Limit zu vermeiden, müssen Sie die Client Software auf Oracle8 (8.0.4.1.1 c oder höher) aktualisieren.
