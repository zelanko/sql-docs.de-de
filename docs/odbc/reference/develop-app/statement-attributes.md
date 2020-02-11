---
title: Anweisungs Attribute | Microsoft-Dokumentation
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
ms.openlocfilehash: c74f1a79ef79b682bc2900d671e07bbe34c4dbf5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107274"
---
# <a name="statement-attributes"></a>Anweisungsattribute
Anweisungs Attribute sind Merkmale der-Anweisung. Ob z. b. Lesezeichen verwendet werden sollen und welche Art von Cursor mit dem Resultset der Anweisung verwendet werden soll, sind Anweisungs Attribute.  
  
 Anweisungs Attribute werden mit **SQLSetStmtAttr** und ihren aktuellen Einstellungen festgelegt, die mit **SQLGetStmtAttr**abgerufen werden. Es ist nicht erforderlich, dass eine Anwendung Anweisungs Attribute einrichtet. Alle Anweisungs Attribute verfügen über Standardwerte, von denen einige Treiber spezifisch sind.  
  
 Wenn ein Anweisungs Attribut festgelegt werden kann, hängt vom Attribut selbst ab. Die SQL_ATTR_CONCURRENCY-, SQL_ATTR_CURSOR_TYPE-, SQL_ATTR_SIMULATE_CURSOR-und SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribute müssen festgelegt werden, bevor die-Anweisung ausgeführt wird. Die Attribute SQL_ATTR_ASYNC_ENABLE und SQL_ATTR_NOSCAN Anweisung können jederzeit festgelegt werden, aber erst nach der erneuten Verwendung der Anweisung angewendet werden. SQL_ATTR_MAX_LENGTH-, SQL_ATTR_MAX_ROWS-und SQL_ATTR_QUERY_TIMEOUT-Anweisungs Attribute können jederzeit festgelegt werden, aber es ist Treiber spezifisch, unabhängig davon, ob Sie angewendet werden, bevor die-Anweisung wieder verwendet wird. Die restlichen Anweisungs Attribute können jederzeit festgelegt werden.  
  
> [!NOTE]  
>  Die Möglichkeit, Anweisungs Attribute auf Verbindungs Ebene durch Aufrufen von **SQLSetConnectAttr** festzulegen, wurde in ODBC 3 als veraltet markiert. *x*. ODBC 3. *x* -Anwendungen sollten nie Anweisungs Attribute auf Verbindungs Ebene festlegen. ODBC 3. *x* -Treiber müssen diese Funktionalität nur unterstützen, wenn Sie mit ODBC 2 arbeiten sollten. *x* -Anwendungen. Weitere Informationen finden Sie unter [SQLSetConnectOption-Zuordnung](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) in Anhang G: Treiber Richtlinien für Abwärtskompatibilität.  
>   
>  Eine Ausnahme hiervon sind die Attribute "SQL_ATTR_METADATA_ID" und "SQL_ATTR_ASYNC_ENABLE", die sowohl Verbindungs Attribute als auch Anweisungs Attribute sind und entweder auf der Verbindungs Ebene oder auf der Anweisungs Ebene festgelegt werden können.  
>   
>  Keines der Anweisungs Attribute, die in ODBC 3 eingeführt wurden. *x* (außer SQL_ATTR_METADATA_ID) kann auf der Verbindungs Ebene festgelegt werden.  
  
 Weitere Informationen finden Sie in der Beschreibung der [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) -Funktion.
