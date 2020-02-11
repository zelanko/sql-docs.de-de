---
title: Überprüfen der Funktions Unterstützung und-Variabilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 21495e538a554a477336d1a92926c11fe762c5af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68062665"
---
# <a name="checking-feature-support-and-variability"></a>Überprüfung der Funktionsunterstützung und Variabilität
Zum Überprüfen der Funktions Unterstützung und-Variabilität werden im allgemeinen **SQLGetInfo**, **SQLGetFunctions**und **SQLGetTypeInfo**aufgerufen. Ein guter Ausgangspunkt sind die API-und SQL-Grammatik-Konformitäts Ebenen des Treibers. Diese beschreiben eine umfassende Funktions Unterstützung. Die Anwendung kann dann **SQLGetInfo** mit anderen Optionen aufrufen, um die Unterstützung oder Varianz von Features zu ermitteln, die Sie benötigt, und **SQLGetFunctions** , um zu bestimmen, ob Funktionen, die über die zurückgegebene Übereinstimmungs Ebene hinaus erforderlich sind, unterstützt werden, und **SQLGetTypeInfo** , um zu bestimmen, welche SQL  
  
 Eine Anwendung kann ermitteln, ob eine Anweisung oder ein Verbindungs Attribut durch Aufrufen von **SQLSetStmtAttr** oder **SQLSetConnectAttr** mit diesem Attribut unterstützt wird. Wenn die Funktion SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt, wird das Attribut unterstützt. Wenn SQL_ERROR und SQLSTATE HYC00 (optionales Feature nicht implementiert) zurückgegeben wird, wird das-Attribut nicht unterstützt.  
  
 Anwendungen können auch eine begrenzte Menge an Informationen bestimmen, bevor Sie eine Verbindung mit dem Treiber herstellen, indem Sie **SQLDrivers**aufrufen.
