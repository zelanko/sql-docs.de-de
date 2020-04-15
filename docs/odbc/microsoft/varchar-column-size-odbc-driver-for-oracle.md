---
title: VARCHAR-Säulengröße (ODBC-Treiber für Oracle) | Microsoft Docs
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
ms.openlocfilehash: f11e1de3171521c57c80beb207d33e67d26d3e33
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304825"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>VARCHAR-Spaltengröße (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 In Oracle8 wurde die maximale Größe einer VARCHAR-Spalte von 2000 auf 4000 Bytes erhöht. Die Oracle 7.3.x-Clientsoftware kann keinen Parameterwert von mehr als 2000 Byte binden. Wenn Sie daher eine Tabelle mit einer VARCHAR-Spalte mit mehr als 2000 Bytes erstellen, können Sie keine parametrisierten Einfügungen, Aktualisierungen, Löschungen und Abfragen mit Daten durchführen, die die 2000-Byte-Grenze der Clientsoftware überschreiten. Da sowohl der ODBC-Treiber für Oracle als auch der OLE DB-Anbieter für Oracle parametrisierte Einfügungen, Updates, Löschungen und Abfragen verwenden, melden sie in diesem Fall ORA-01026-Fehler. Daten, die innerhalb der von der Oracle-Clientsoftware erzwungenen Grenzen liegen, funktionieren. Um dieses 2000-Byte-Limit zu vermeiden, müssen Sie Ihre Clientsoftware auf Oracle8 (8.0.4.1.1c oder höher) aktualisieren.
