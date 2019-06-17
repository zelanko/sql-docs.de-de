---
title: Transaktionsunterstützung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], degree of support
ms.assetid: d56e1458-8da2-4d73-a777-09e045c30a33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be133079c1b6beffd484942eb9ae058c14dd5c1f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63306035"
---
# <a name="transaction-support"></a>Transaktionsunterstützung.
Das Maß an Unterstützung für Transaktionen wird-Treiber definiert. ODBC soll für eine einzelne Benutzer oder desktop-Datenbank implementiert werden, die nicht erforderlich, mehrere Updates auf ihre Daten zu verwalten. Führen Sie darüber hinaus einige Datenbanken, die Transaktionen unterstützen, nur für die Anweisungen (Data Manipulation Language, DML) von SQL; Es gibt Einschränkungen oder spezielle Transaktionssemantik im Hinblick auf die Verwendung der Windows-Verwaltungsinstrumentation (Data Definition Language, Datendefinitionssprache), wenn eine Transaktion aktiv ist. D. h. möglicherweise Unterstützung von Transaktionen für mehrere gleichzeitige Updates an Tabellen jedoch nicht für die Anzahl und die Definition von Tabellen während einer Transaktion ändern.  
  
 Eine Anwendung, ob Transaktionen unterstützt werden, bestimmt, ob DDL in einer Transaktion und alle Spezialeffekte einschließlich DDL in einer Transaktion kann durch Aufrufen von aufgenommen werden kann **SQLGetInfo** mit der Option SQL_TXN_CAPABLE. Weitere Informationen finden Sie unter den [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung.  
  
 Wenn der Treiber keine Transaktionen unterstützt, aber die Anwendung muss die Möglichkeit, die (mit einer anderen ODBC-API) sperren und Entsperren von Daten, können Anwendungen durch Sperren und entsperren Datensätzen und Tabellen, die je nach Bedarf die Unterstützung von Transaktionen erzielen. Zum Implementieren der Konto-Transfer-Beispiel würde die Anwendung sperren die Einträge für beide Konten, kopieren Sie die aktuellen Werte, belasten Sie das erste Konto, das zweite Konto Guthaben und Entsperren die Datensätze. Wenn alle Schritte fehlgeschlagen ist, würde die Anwendung die Konten, die mit den Kopien zurückgesetzt.  
  
 Sogar von Datenquellen, die Transaktionen unterstützen möglicherweise nicht mehr als eine Transaktion zu einem Zeitpunkt innerhalb einer bestimmten Umgebung zu unterstützen. -Anwendungen rufen **SQLGetInfo** mit der Option SQL_MULTIPLE_ACTIVE_TXN, um festzustellen, ob eine Datenquelle gleichzeitige aktive Transaktionen auf mehr als eine Verbindung in der gleichen Umgebung unterstützen kann. Da eine Transaktion pro Verbindung vorhanden ist, ist dies nur interessant, Anwendungen, die mehrere Verbindungen mit der gleichen Datenquelle haben.
