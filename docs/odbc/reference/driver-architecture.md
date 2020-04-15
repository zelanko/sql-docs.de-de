---
title: Treiberarchitektur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], architecture
ms.assetid: c5003413-0cc1-4f41-b877-a64e2f5ab118
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ffe2023f028357468700b9bd995d22129ba06817
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294220"
---
# <a name="driver-architecture"></a>Treiberarchitektur
Die Treiberarchitektur gliedert sich in zwei Kategorien, je nachdem, welche Software SQL-Anweisungen verarbeitet:  
  
-   **Dateibasierte Treiber** Der Treiber greift direkt auf die physischen Daten zu. In diesem Fall fungiert der Treiber sowohl als Treiber als auch als Datenquelle. Das heißt, es verarbeitet ODBC-Aufrufe und SQL-Anweisungen. DBASE-Treiber sind z. B. dateibasierte Treiber, da dBASE kein eigenständiges Datenbankmodul zur Verfügung stellt, das der Treiber verwenden kann. Es ist wichtig zu beachten, dass Entwickler von dateibasierten Treibern ihre eigenen Datenbankmodule schreiben müssen.  
  
-   **DBMS-basierte Treiber** Der Treiber greift über ein separates Datenbankmodul auf die physischen Daten zu. In diesem Fall verarbeitet der Treiber nur ODBC-Aufrufe; ES übergibt SQL-Anweisungen zur Verarbeitung an das Datenbankmodul. Oracle-Treiber sind beispielsweise DBMS-basierte Treiber, da Oracle über eine eigenständige Datenbank-Engine verfügt, die der Treiber verwendet. Wo sich das Datenbankmodul befindet, ist unerheblich. Es kann sich auf demselben Computer wie der Treiber oder ein anderer Computer im Netzwerk befinden. Es kann sogar über ein Gateway zugegriffen werden.  
  
 Treiberarchitektur ist in der Regel nur für Treiberautoren interessant; das heißt, die Treiberarchitektur macht in der Regel keinen Unterschied zur Anwendung. Die Architektur kann sich jedoch darauf auswirken, ob eine Anwendung DBMS-spezifische SQL verwenden kann. Microsoft Access stellt beispielsweise ein eigenständiges Datenbankmodul bereit. Wenn ein Microsoft Access-Treiber DBMS-basiert ist - er greift über dieses Modul auf die Daten zu - kann die Anwendung Microsoft Access-SQL-Anweisungen zur Verarbeitung an das Modul übergeben.  
  
 Wenn der Treiber jedoch dateibasiert ist , d. h. ein proprietäres Modul enthält, das direkt auf die Microsoft® Access .mdb-Datei zugreift - führen alle Versuche, Microsoft Access-spezifische SQL-Anweisungen an das Modul zu übergeben, wahrscheinlich zu Syntaxfehlern. Der Grund dafür ist, dass das proprietäre Modul wahrscheinlich nur ODBC SQL implementiert.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Dateibasierte Treiber](../../odbc/reference/file-based-drivers.md)  
  
-   [DBMS-basierte Treiber](../../odbc/reference/dbms-based-drivers.md)  
  
-   [Netzwerkbeispiel](../../odbc/reference/network-example.md)  
  
-   [Andere Treiberarchitekturen](../../odbc/reference/other-driver-architectures.md)
