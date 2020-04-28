---
title: Gewöhnliche Argumente | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282464"
---
# <a name="ordinary-arguments"></a>Normale Argumente
Wenn ein Katalog Funktions-Zeichen folgen Argument ein normales Argument ist, wird es als Literalzeichenfolge behandelt. Ein normales Argument akzeptiert weder ein Zeichen folgen-Suchmuster noch eine Liste von Werten. Die Groß-/Kleinschreibung eines normalen Arguments ist signifikant, und Anführungszeichen in der Zeichenfolge werden buchstäblich verwendet. Diese Argumente werden als normale Argumente behandelt, wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_FALSE festgelegt ist. Sie werden stattdessen als bezeichnerargumente behandelt, wenn dieses Attribut auf SQL_TRUE festgelegt ist.  
  
 Wenn ein normales Argument auf einen NULL-Zeiger festgelegt ist und das Argument ein erforderliches Argument ist, gibt die Funktion SQL_ERROR und SQLSTATE HY009 zurück (Ungültige Verwendung des NULL-Zeigers). Wenn ein normales Argument auf einen NULL-Zeiger festgelegt ist und das Argument kein erforderliches Argument ist, ist das Verhalten des Arguments Treiber abhängig. Die erforderlichen Argumente sind in der folgenden Tabelle aufgeführt.  
  
|Funktion|Erforderliche Argumente|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, Datei *Name*|  
|**SQLPrimaryKeys**|*TableName*|  
|**'SQLSpecialColumns'**|*TableName*|  
|**'SQLStatistics'**|*TableName*|
