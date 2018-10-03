---
title: Änderungen am Verhalten | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: abe670570dd2219247da0c70b2b62e1de4e60341
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757184"
---
# <a name="behavioral-changes"></a>Verhaltensänderungen
Änderungen am Verhalten werden diese Änderungen für die die *Syntax* der Schnittstelle bleibt gleich, aber die *Semantik* geändert haben. Für diese Änderungen der Funktionalität in ODBC 2. verwendet. *x* verhält sich anders als die gleiche Funktionalität in ODBC 3. *X*.  
  
 Gibt an, ob eine Anwendung ODBC 2. weist. *x* Verhalten oder ODBC 3. *X* Verhalten wird durch das Attribut der SQL_ATTR_ODBC_VERSION Umgebung bestimmt. Dieser 32-Bit-Wert wird auf SQL_OV_ODBC2 zu ODBC 2. festgelegt. *x* Verhalten und SQL_OV_ODBC3 zu ODBC 3. *X* Verhalten.  
  
 SQL_ATTR_ODBC_VERSION umgebungsattributs wird festgelegt, durch einen Aufruf von **SQLSetEnvAttr**. Nachdem eine Anwendung ruft **SQLAllocHandle** um ein Umgebungshandle zuzuordnen, muss er Aufrufen**SQLSetEnvAttr** sofort auf das Verhalten festgelegt, es weist. (Daher besteht ein neue Umgebung Zustand, beschreiben Sie das Umgebungshandle in ein zugeordnetes, aber versionless, Status.) Weitere Informationen finden Sie unter [Anhang B: ODBC-Übergang-Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Eine Anwendung gibt an, welches Verhalten, die sie mit dem Umgebungsattribut SQL_ATTR_ODBC_VERSION, aber das Attribut weist keine Auswirkungen auf die Verbindung der Anwendung mit einer ODBC 2. hat. *x* oder ODBC-3. *X* Treiber. Eine ODBC-3. *x* Anwendung verbinden kann, entweder einer ODBC 2. *X* oder 3. *X* -Treiber verwenden, unabhängig davon, welche die Einstellung des umgebungsattributs.  
  
 ODBC 3. *x* Anwendungen sollten niemals Aufrufen **SQLAllocEnv**. Als Ergebnis, wenn der Treiber-Manager einen Aufruf empfängt **SQLAllocEnv**, erkennt die Anwendung als einer ODBC 2. *X* Anwendung.  
  
 Das Attribut SQL_ATTR_ODBC_VERSION wirkt sich auf drei verschiedene Aspekte von einer ODBC-3. *x* des Treibers Verhalten:  
  
-   SQLSTATEs  
  
-   Datentypen für Datum, Uhrzeit und Zeitstempel  
  
-   Die *CatalogName* -Argument in **SQLTables** Suchmuster in ODBC 3. akzeptiert. *X*, aber nicht in der ODBC-2. *x*  
  
 Die Einstellung des umgebungsattributs SQL_ATTR_ODBC_VERSION wirkt sich nicht **SQLSetParam** oder **SQLBindParam**. **SQLColAttribute** wird auch von dieses Bit nicht beeinflusst. Obwohl **SQLColAttribute** Attribute, die betroffen sind, gibt das beabsichtigte Verhalten wird von der Version von ODBC (Datentyp, Genauigkeit, Dezimalstellen und Länge), durch den Wert bestimmt die *FieldIdentifier*Argument. Wenn *FieldIdentifier* gleich SQL_DESC_TYPE, **SQLColAttribute** gibt zurück, die ODBC 3. *X* Codes für Datum, Uhrzeit und Zeitstempel; beim *FieldIdentifier* gleich SQL_COLUMN_TYPE, **SQLColAttribute** gibt zurück, die ODBC 2. *X* Codes für Date, Time und Timestamp.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [SQLSTATE-Zuordnungen](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Änderungen des Datentyps „datetime“](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
