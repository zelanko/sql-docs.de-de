---
title: Anweisungshandles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 730ead7bf90af3b6e6906fe184e0fa3312212137
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107260"
---
# <a name="statement-handles"></a>Anweisungshandles
Ein *Anweisung* ist am einfachsten vorstellen als SQL-Anweisung, wie z. B. **wählen \* aus Mitarbeiter**. Allerdings wird eine Anweisung ist mehr als nur eine SQL-Anweisung – Es besteht aus der alle Informationen, SQL-Anweisung, wie z. B. alle Resultsets, die von der Anweisung erstellt und in der Ausführung der Anweisung verwendeten Parametern zugeordnet. Eine Anweisung muss auch nicht um eine Anwendung definierte SQL-Anweisung zu erhalten. Wenn ein Katalog funktionieren wie z. B. **SQLTables** ausgeführt wird in einer Anweisung, führt es eine vordefinierte SQL-Anweisung, die eine Liste der Tabellennamen zurückgibt.  
  
 Jede Anweisung wird durch ein Anweisungshandle identifiziert. Eine Anweisung mit einer einzelnen Verbindung verknüpft ist können, und es mehrere Anweisungen für die Verbindung. Einige Treiber Beschränken der Anzahl aktiver Anweisungen, die sie unterstützen. die SQL_MAX_CONCURRENT_ACTIVITIES option **SQLGetInfo** gibt an, wie viele aktive Anweisungen, die ein Treiber, die über eine einzelne Verbindung unterstützt. Eine Anweisung definiert *active* verfügt es Ergebnisse ausstehen, in dem Ergebnisse sind, entweder ein Resultset oder die Anzahl der von betroffenen Zeilen eine **einfügen**, **UPDATE**, oder **Löschen** -Anweisung oder Daten mit mehreren Aufrufen an gesendet wird **SQLPutData**.  
  
 Innerhalb eines Codeabschnitts, die ODBC (des Treiber-Managers oder eines Treibers) implementiert, identifiziert das Anweisungshandle eine Struktur, die Informationen, wie z. B. enthält:  
  
-   Status von der Anweisung  
  
-   Die aktuelle auf Anweisungsebene-Diagnose  
  
-   Die Adressen der Anwendungsvariablen an die Anweisung Parameter gebunden und Resultsetspalten  
  
-   Die aktuellen Einstellungen der einzelnen Anweisung attribute  
  
 Anweisungshandles werden in den meisten ODBC-Funktionen verwendet. Sie werden vor allem in den Funktionen verwendet, um den Parameter gebunden und Resultsetspalten (**SQLBindParameter** und **SQLBindCol**), Vorbereiten und Ausführen von Anweisungen (**SQLPrepare** **SQLExecute**, und **SQLExecDirect**), Abrufen von Metadaten (**SQLColAttribute** und **SQLDescribeCol**), Abrufen Ergebnisse (**SQLFetch**), und rufen Sie die Diagnose (**SQLGetDiagField** und **SQLGetDiagRec**). Sie werden auch in Katalogfunktionen verwendet (**SQLColumns**, **SQLTables**usw.) und eine Reihe von weiteren Funktionen.  
  
 Anweisungshandle zugeordnet sind **SQLAllocHandle** und mit freigegebenen **SQLFreeHandle**.
