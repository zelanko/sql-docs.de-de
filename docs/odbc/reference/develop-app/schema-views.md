---
title: Schema-Ansichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1e2dd512ab529f1fb5d216f4a2e459cd601d40e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67943757"
---
# <a name="schema-views"></a>Schemaansichten
Eine Anwendung kann aus dem DBMS entweder durch Aufrufen von ODBC-Katalogfunktionen oder INFORMATION_SCHEMA-Sichten mit Abrufen von Metadateninformationen. Durch den ANSI SQL-92-Standard definiert werden.  
  
 Wenn von DBMS und der Treiber unterstützt, bieten die INFORMATION_SCHEMA-Sichten eine leistungsfähigere und umfassende Möglichkeit zum Abrufen von Metadaten als die ODBC-Katalogfunktionen bereitstellen. Ausführen einer Anwendung kann ihr eigenes benutzerdefiniertes **wählen** -Anweisung für eine dieser Ansichten,-Ansichten verbinden können oder eine Union für Ansichten ausführen kann. Und bietet größere-Hilfsprogramm und eine größere Anzahl von Metadaten, werden die INFORMATION_SCHEMA-Sichten nicht häufig vom DBMS unterstützt. Dies möglicherweise ändern, wie die Kompatibilität mit SQL-92 Weitere DBMS und Zieltreiber erreichen.  
  
 Um zu bestimmen, welche Ansichten unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_INFO_SCHEMA_VIEWS. Zum Abrufen von Metadaten aus einer unterstützten Sicht führt die Anwendung eine **wählen** Anweisung, der angibt, die Schemainformationen, die erforderlich sind.
