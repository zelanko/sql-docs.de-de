---
title: Schema Sichten | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67943757"
---
# <a name="schema-views"></a>Schemaansichten
Eine Anwendung kann Metadateninformationen aus dem DBMS abrufen, indem Sie entweder ODBC-Katalog Funktionen oder INFORMATION_SCHEMA Sichten aufruft. Die Sichten werden durch den ANSI SQL-92-Standard definiert.  
  
 Wenn Sie vom DBMS und dem Treiber unterstützt werden, bieten die INFORMATION_SCHEMA Sichten eine leistungsfähigere und umfassendere Methode zum Abrufen von Metadaten, die von den ODBC-Katalog Funktionen bereitgestellt werden. Eine Anwendung kann eine eigene benutzerdefinierte **Select** -Anweisung für eine dieser Sichten ausführen, Ansichten verknüpfen oder eine Union für Ansichten ausführen. Wenn Sie ein höheres Hilfsprogramm und eine größere Anzahl von Metadaten anbieten, werden INFORMATION_SCHEMA Sichten nicht häufig vom DBMS unterstützt. Dies kann sich ändern, wenn mehr DBMSs und Treiber die Kompatibilität mit SQL-92 erzielen.  
  
 Um zu ermitteln, welche Sichten unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit der SQL_INFO_SCHEMA_VIEWS-Option auf. Zum Abrufen von Metadaten aus einer unterstützten Ansicht führt die Anwendung eine **Select** -Anweisung aus, die die erforderlichen Schema Informationen angibt.
