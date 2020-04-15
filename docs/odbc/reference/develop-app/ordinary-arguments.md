---
title: Gewöhnliche Argumente | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97362f93e91ccd8b592b4c05a0714b7602c1ba94
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282464"
---
# <a name="ordinary-arguments"></a>Normale Argumente
Wenn ein Katalogfunktionszeichenfolgenargument ein gewöhnliches Argument ist, wird es als Literalzeichenfolge behandelt. Ein gewöhnliches Argument akzeptiert weder ein Zeichenfolgensuchmuster noch eine Liste von Werten. Der Fall eines gewöhnlichen Arguments ist signifikant, und Zitatzeichen in der Zeichenfolge werden wörtlich genommen. Diese Argumente werden als gewöhnliche Argumente behandelt, wenn das Attribut SQL_ATTR_METADATA_ID-Anweisung auf SQL_FALSE festgelegt ist. Sie werden stattdessen als Bezeichnerargumente behandelt, wenn dieses Attribut auf SQL_TRUE festgelegt ist.  
  
 Wenn ein gewöhnliches Argument auf einen Nullzeiger festgelegt ist und das Argument ein erforderliches Argument ist, gibt die Funktion SQL_ERROR und SQLSTATE HY009 (Ungültige Verwendung von NULL-Zeiger) zurück. Wenn ein gewöhnliches Argument auf einen Nullzeiger festgelegt ist und das Argument kein erforderliches Argument ist, ist das Verhalten des Arguments treiberabhängig. Die erforderlichen Argumente sind in der folgenden Tabelle aufgeführt.  
  
|Funktion|Erforderliche Argumente|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**'SQLSpecialColumns'**|*TableName*|  
|**'SQLStatistics'**|*TableName*|
