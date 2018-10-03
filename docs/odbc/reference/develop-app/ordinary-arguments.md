---
title: Normale Argumente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31d83b00fd70cd54587a19ebfea7310154167493
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706687"
---
# <a name="ordinary-arguments"></a>Normale Argumente
Wenn ein Zeichenfolgenargument für Katalog-Funktion ein normales Argument ist, wird es als Zeichenfolgenliteral behandelt. Ein normales Argument akzeptiert, weder ein Zeichenfolgenmuster für die Suche als auch eine Liste von Werten. Ein normales Argument die Groß-/Kleinschreibung spielt und Anführungszeichen in der Zeichenfolge wörtlich genommen werden. Diese Argumente werden als normale Argumente behandelt, wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_FALSE festgelegt ist; Sie werden stattdessen als bezeichnerargumente behandelt, wenn dieses Attribut auf SQL_TRUE festgelegt ist.  
  
 Wenn ein normales Argument auf einen null-Zeiger festgelegt ist, und das Argument ein erforderliches Argument ist, gibt die Funktion SQL_ERROR zurück, und SQLSTATE HY009 (Ungültige Verwendung von null-Zeiger). Wenn ein normales Argument auf einen null-Zeiger festgelegt ist, und das Argument kein erforderliches Argument ist, ist das Argument des Verhalten treiberabhängig. Die erforderlichen Argumente werden in der folgenden Tabelle aufgeführt.  
  
|Funktion|Erforderliche Argumente|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
