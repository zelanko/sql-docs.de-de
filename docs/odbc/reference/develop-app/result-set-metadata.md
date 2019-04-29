---
title: Führen Sie die Set-Metadaten | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7dc88892fab2fd18dbcbec5ce54fa09c9c9b89e7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199388"
---
# <a name="result-set-metadata"></a>Resultsetmetadaten
*Metadaten* sind Daten, die andere Daten beschreiben. Resultsetmetadaten beschreiben beispielsweise das Resultset auf, wie z. B. die Anzahl der Spalten im Resultset, die Datentypen der Spalten, ihre Namen, Genauigkeit, NULL-Zulässigkeit und So weiter.  
  
 Interoperable Anwendungen ausführen können sollten immer überprüfen, die Metadaten der Spalten im Resultset. Die Metadaten für eine Spalte in einem Resultset unterscheiden sich aus den Metadaten für die Spalte, wie Sie von einer Katalogfunktion zurückgegeben. Nehmen wir beispielsweise an, dass eine aktualisierbare Spalte enthalten ist, in einem Resultset, die durch Verknüpfen von zwei Tabellen erstellt wurde. Während **SQLColumnPrivileges** wird angegeben, dass ein Benutzer kann die Spalte aktualisieren, die resultsetmetadaten möglicherweise nicht, wenn die Spalte auf der Seite "n" des Joins ist; viele Datenquellen können Spalten aktualisieren auf der Seite "1" für eine Verknüpfung, jedoch nicht auf die " n-Seite. Auch die Datentypen können nicht angenommen, dass übereinstimmen, da die Datenquelle den Datentyp höher beim Erstellen des Resultsets Stufen kann.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Wie werden Metadaten verwendet?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol und SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
