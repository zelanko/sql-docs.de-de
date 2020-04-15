---
title: Verhaltensänderungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], behavioral changes
- behavioral changes [ODBC]
- compatibility [ODBC], behavioral changes
ms.assetid: a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e4a433531d90eb0f89d9a5e446464b13fd02526
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283440"
---
# <a name="behavioral-changes"></a>Verhaltensänderungen
Verhaltensänderungen sind die Änderungen, für die die *Syntax* der Schnittstelle gleich bleibt, aber die *Semantik* hat sich geändert. Für diese Änderungen die in ODBC 2 verwendete Funktionalität. *x* verhält sich anders als die gleiche Funktionalität in ODBC 3. *x*.  
  
 Gibt an, ob eine Anwendung ODBC 2 aufweist. *x-Verhalten* oder ODBC 3. *das x-Verhalten* wird durch das SQL_ATTR_ODBC_VERSION Umgebungsattribut bestimmt. Dieser 32-Bit-Wert wird auf SQL_OV_ODBC2 eingestellt, um ODBC 2 auszustellen. *x-Verhalten* und SQL_OV_ODBC3 ODBC 3 ausstellen. *x* Verhalten.  
  
 Das SQL_ATTR_ODBC_VERSION Umgebungsattribut wird durch einen Aufruf von **SQLSetEnvAttr**festgelegt. Nachdem eine Anwendung **SQLAllocHandle** aufruft, um ein Umgebungshandle zuzuweisen, muss sie**SQLSetEnvAttr** sofort aufrufen, um das auftretende Verhalten festzulegen. (Daher gibt es einen neuen Umgebungsstatus, um das Umgebungshandle in einem zugewiesenen, aber versionslosen Zustand zu beschreiben.) Weitere Informationen finden Sie in [Anhang B: ODBC-Zustandsübergangstabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Eine Anwendung gibt an, welches Verhalten sie mit dem SQL_ATTR_ODBC_VERSION Umgebungsattribut anzeigt, aber das Attribut hat keine Auswirkungen auf die Verbindung der Anwendung mit einem ODBC 2. *x* oder ODBC 3. *x-Treiber.* Ein ODBC 3. *x-Anwendung* kann eine Verbindung mit einem ODBC 2 herstellen. *x* oder 3. *x-Treiber,* unabhängig von der Einstellung des Umgebungsattributs.  
  
 ODBC 3. *x-Anwendungen* sollten **SQLAllocEnv**niemals aufrufen. Wenn der Treiber-Manager daher einen Aufruf an **SQLAllocEnv**empfängt, erkennt er die Anwendung als ODBC 2. *x* Anwendung.  
  
 Das attribut SQL_ATTR_ODBC_VERSION wirkt sich auf drei verschiedene Aspekte eines ODBC 3 aus. *x* Fahrerverhalten:  
  
-   SQLSTATEs  
  
-   Datentypen für Datum, Uhrzeit und Zeitstempel  
  
-   Das *Argument CatalogName* in **SQLTables** akzeptiert Suchmuster in ODBC 3. *x*, jedoch nicht in ODBC 2. *x*  
  
 Die Einstellung des SQL_ATTR_ODBC_VERSION Umgebungsattributs wirkt sich nicht auf **SQLSetParam** oder **SQLBindParam**aus. **SQLColAttribute** ist auch von diesem Bit nicht betroffen. Obwohl **SQLColAttribute** Attribute zurückgibt, die von der Version von ODBC betroffen sind (Datumstyp, Genauigkeit, Skalierung und Länge), wird das beabsichtigte Verhalten durch den Wert des *FieldIdentifier-Arguments* bestimmt. Wenn *FieldIdentifier* SQL_DESC_TYPE entspricht, gibt **SQLColAttribute** odBC 3 zurück. *x-Codes* für Datum, Uhrzeit und Zeitstempel; Wenn *FieldIdentifier* SQL_COLUMN_TYPE entspricht, gibt **SQLColAttribute** odBC 2 zurück. *x-Codes* für Datum, Uhrzeit und Zeitstempel.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [SQLSTATE-Zuordnungen](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Änderungen des Datentyps „datetime“](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
