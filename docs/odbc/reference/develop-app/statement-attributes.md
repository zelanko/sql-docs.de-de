---
title: Anweisungsattribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e669f02eeb76ba529c75851ce8bf6ff9a7831a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149086"
---
# <a name="statement-attributes"></a>Anweisungsattribute
Anweisungsattribute sind Eigenschaften der Anweisung. Sind Sie Anweisungsattribute z. B., ob mit Lesezeichen und welche Art von Cursor für die Verwendung mit der Anweisung Ergebnis festgelegt.  
  
 Anweisungsattribute werden mit festgelegt **SQLSetStmtAttr** und ihre aktuellen Einstellungen abgerufen werden, mit **SQLGetStmtAttr**. Es ist nicht erforderlich, dass eine Anwendung Anweisungsattribute festlegen. Alle Anweisungsattribute haben Standardwerte, von die einige Treiber-spezifisch sind.  
  
 Wenn ein Anweisungsattribut festgelegt werden kann, hängt das Attribut selbst ab. Die Anweisungsattribute SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR und SQL_ATTR_USE_BOOKMARKS müssen festgelegt werden, bevor die Anweisung ausgeführt wird. Die Anweisungsattribute SQL_ATTR_ASYNC_ENABLE und SQL_ATTR_NOSCAN können zu einem beliebigen Zeitpunkt festgelegt werden, jedoch werden nicht angewendet werden, bis die Anweisung erneut verwendet wird. SQL_ATTR_MAX_LENGTH und SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT Anweisungsattribute können zu einem beliebigen Zeitpunkt festgelegt werden, aber es ist treiberspezifisch gibt an, ob sie angewendet werden, bevor die Anweisung erneut verwendet wird. Die verbleibenden Anweisungsattribute können zu einem beliebigen Zeitpunkt festgelegt werden.  
  
> [!NOTE]  
>  Die Fähigkeit zum Festlegen von Anweisungsattribute auf der Verbindungsebene durch Aufrufen von **SQLSetConnectAttr** in ODBC 3. veraltet. *X*. ODBC 3. *x* Anwendungen sollten auf der Verbindungsebene Anweisungsattribute festlegen. ODBC 3. *x* Treiber müssen nur diese Funktion unterstützen, wenn sie mit ODBC 2. funktionieren sollte. *X* Anwendungen. Weitere Informationen finden Sie unter [SQLSetConnectOption-Zuordnung](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
>   
>  Eine Ausnahme ist die SQL_ATTR_METADATA_ID und SQL_ATTR_ASYNC_ENABLE-Attribute, die sind-Verbindungsattributen und Anweisungsattribute und entweder auf der Verbindungsebene oder Anweisungsebene festgelegt werden können.  
>   
>  Keines der Anweisungsattribute, die in ODBC 3. eingeführt. *x* (mit Ausnahme von SQL_ATTR_METADATA_ID) kann auf der Verbindungsebene festgelegt werden.  
  
 Weitere Informationen finden Sie unter den [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) funktionsbeschreibung.
