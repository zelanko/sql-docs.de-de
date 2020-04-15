---
title: Ergebnissatzmetadaten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b78cdeb4c8b3522f4677c0277401cd9395a36a5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300080"
---
# <a name="result-set-metadata"></a>Resultsetmetadaten
*Metadaten* sind Daten, die andere Daten beschreiben. Beispielsweise beschreiben Resultsetmetadaten das Resultset, z. B. die Anzahl der Spalten im Resultset, die Datentypen dieser Spalten, ihre Namen, Genauigkeit, NULL-Zulässigkeit usw.  
  
 Interoperable Anwendungen sollten immer die Metadaten von Ergebnissatzspalten überprüfen. Die Metadaten für eine Spalte in einem Resultset können von den Metadaten für die Spalte abweichen, die von einer Katalogfunktion zurückgegeben werden. Angenommen, eine aktualisierbare Spalte wird in ein Resultset einbezogen, das durch Verbinden von zwei Tabellen erstellt wurde. Obwohl **SQLColumnPrivileges** darauf hinweisen kann, dass ein Benutzer die Spalte aktualisieren kann, können die Metadaten des Resultsets möglicherweise nicht, wenn sich die Spalte auf der "n"-Seite der Verknüpfung befindet. Viele Datenquellen können Spalten auf der "einen" Seite einer Verknüpfung aktualisieren, aber nicht auf der "n"-Seite. Selbst Datentypen können nicht als identisch angenommen werden, da die Datenquelle den Datentyp beim Erstellen des Resultsets heraufstufen kann.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Wie werden Metadaten verwendet?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol und SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
