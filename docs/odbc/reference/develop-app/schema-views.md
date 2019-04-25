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
manager: craigg
ms.openlocfilehash: 782dec08b76a9e5a97719d6af39e2c30c0f92d19
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468617"
---
# <a name="schema-views"></a>Schemaansichten
Eine Anwendung kann aus dem DBMS entweder durch Aufrufen von ODBC-Katalogfunktionen oder INFORMATION_SCHEMA-Sichten mit Abrufen von Metadateninformationen. Durch den ANSI SQL-92-Standard definiert werden.  
  
 Wenn von DBMS und der Treiber unterstützt, bieten die INFORMATION_SCHEMA-Sichten eine leistungsfähigere und umfassende Möglichkeit zum Abrufen von Metadaten als die ODBC-Katalogfunktionen bereitstellen. Ausführen einer Anwendung kann ihr eigenes benutzerdefiniertes **wählen** -Anweisung für eine dieser Ansichten,-Ansichten verbinden können oder eine Union für Ansichten ausführen kann. Und bietet größere-Hilfsprogramm und eine größere Anzahl von Metadaten, werden die INFORMATION_SCHEMA-Sichten nicht häufig vom DBMS unterstützt. Dies möglicherweise ändern, wie die Kompatibilität mit SQL-92 Weitere DBMS und Zieltreiber erreichen.  
  
 Um zu bestimmen, welche Ansichten unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_INFO_SCHEMA_VIEWS. Zum Abrufen von Metadaten aus einer unterstützten Sicht führt die Anwendung eine **wählen** Anweisung, der angibt, die Schemainformationen, die erforderlich sind.
