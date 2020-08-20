---
description: Verhaltensänderungen
title: Verhaltensänderungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 6fb5501d362cb46f3616e58c5a4994bab86e00ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461622"
---
# <a name="behavioral-changes"></a>Verhaltensänderungen
Verhaltensänderungen sind die Änderungen, bei denen die *Syntax* der-Schnittstelle unverändert bleibt, aber die *Semantik* geändert hat. Für diese Änderungen wird die Funktionalität in ODBC 2 verwendet. *x* verhält sich anders als die gleiche Funktionalität in ODBC 3. *x*.  
  
 Gibt an, ob eine Anwendung ODBC 2 aufweist. *x* -Verhalten oder ODBC 3. Das *x* -Verhalten wird durch das SQL_ATTR_ODBC_VERSION Environment-Attribut bestimmt. Dieser 32-Bit-Wert ist auf SQL_OV_ODBC2 festgelegt, um ODBC 2 zu präsentieren. *x* -Verhalten und SQL_OV_ODBC3, um ODBC 3 zu präsentieren. *x* -Verhalten.  
  
 Das SQL_ATTR_ODBC_VERSION Environment-Attribut wird durch einen **SQLSetEnvAttr**-Befehl festgelegt. Nachdem eine Anwendung **SQLAllocHandle** aufgerufen hat, um ein Umgebungs Handle zuzuordnen, muss Sie**SQLSetEnvAttr** sofort aufrufen, um das Verhalten festzulegen, das Sie zeigt. (Folglich gibt es einen neuen Umgebungszustand, in dem das Umgebungs Handle in einem zugeordneten, aber versionlosen Zustand beschrieben wird.) Weitere Informationen finden Sie unter [Anhang B: ODBC-Status Übergangs Tabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Eine Anwendung gibt an, welches Verhalten mit dem SQL_ATTR_ODBC_VERSION-Umgebungs Attribut hervorgeht, aber das-Attribut hat keine Auswirkung auf die Verbindung der Anwendung mit einem ODBC 2. *x* oder ODBC 3. *x* -Treiber Ein ODBC 3. die *x* -Anwendung kann eine Verbindung mit einem ODBC 2-Server herstellen. *x* oder 3. *x* -Treiber, unabhängig von der Einstellung des Umgebungs Attributs.  
  
 ODBC 3. *x* -Anwendungen sollten nie **sqlzugecenv**aufruft. Wenn der Treiber-Manager z. b. einen-Befehl an **sqlzugewiesene cenv**empfängt, wird die Anwendung als ODBC 2 erkannt. *x* -Anwendung.  
  
 Das SQL_ATTR_ODBC_VERSION-Attribut wirkt sich auf drei verschiedene Aspekte von ODBC 3 aus. Verhalten des *x* -Treibers:  
  
-   SQLSTATEs  
  
-   Datentypen für Date, Time und Zeitstempel  
  
-   Das *CatalogName* -Argument in **SQLTables** akzeptiert Suchmuster in ODBC 3. *x*, jedoch nicht in ODBC 2. *x*  
  
 Die Einstellung des SQL_ATTR_ODBC_VERSION Environment-Attributs wirkt sich nicht auf **SQLSetParam** oder **SQLBindParam**aus. **SQLColAttribute** ist von diesem Bit ebenfalls nicht betroffen. Obwohl **SQLColAttribute** Attribute zurückgibt, die von der ODBC-Version (Date Type, Precision, Scale und length) betroffen sind, wird das beabsichtigte Verhalten durch den Wert des *fieldidentifier* -Arguments festgelegt. Wenn *fieldidentifier* gleich SQL_DESC_TYPE ist, gibt **SQLColAttribute** ODBC 3 zurück. *x* Codes für Date, Time und Timestamp; Wenn *fieldidentifier* gleich SQL_COLUMN_TYPE ist, gibt **SQLColAttribute** ODBC 2 zurück. *x* Codes für Date, Time und TIMESTAMP.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [SQLSTATE-Zuordnungen](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Änderungen des Datentyps „datetime“](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
