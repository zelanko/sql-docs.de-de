---
title: Escape-Sequenzen in ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC]
- SQL statements [ODBC], escape sequences
- escape sequences [ODBC], about escape sequences
ms.assetid: cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4d41b0c03ecbe6de63cba1a28a1f39f12a42dc86
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300420"
---
# <a name="escape-sequences-in-odbc"></a>Escapesequenzen in ODBC
Eine Reihe von Sprachfeatures, z. B. äußere Verknüpfungen und skalare Funktionsaufrufe, werden häufig von DBMS implementiert. Die Syntaxen für diese Features sind jedoch in der Regel DBMS-spezifisch, selbst wenn Standardsyntaxen von den verschiedenen Standardtexten definiert werden. Aus diesem Grund definiert ODBC Escapesequenzen, die Standardsyntaxen für die folgenden Sprachfeatures enthalten:  
  
-   Datums-, Uhrzeit-, Zeitstempel- und Datumszeitintervallliterale  
  
-   Skalare Funktionen wie numerische, Zeichenfolgen- und Datentypkonvertierungsfunktionen  
  
-   LIKE Prädikat Fluchtcharakter  
  
-   Äußere Joins  
  
-   Prozeduraufrufe  
  
 Die von ODBC verwendete Escape-Sequenz ist wie folgt:  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die Escapesequenz wird von Treibern erkannt und analysiert, die die Escapesequenzen durch DBMS-spezifische Grammatik ersetzen. Weitere Informationen zur Escapesequenzsyntax finden Sie unter [ODBC Escape Sequences](../../../odbc/reference/appendixes/odbc-escape-sequences.md) in Anhang C: SQL Grammar.  
  
> [!NOTE]  
>  In ODBC 2. *x*, dies war die Standardsyntax der Escape-Sequenz: **--(\*vendor(**_vendor-name_**), product(**_product-name_**)**_extension_ ** \*)--**  
>   
>  Zusätzlich zu dieser Syntax wurde eine Kurzschriftsyntax der Form **definiert:**_extension_**}**  
>   
>  In ODBC 3. *x*, die lange Form der Escape-Sequenz ist veraltet, und die Kurzschriftform wird ausschließlich verwendet.  
  
 Da die Escapesequenzen vom Treiber DBMS-spezifischen Syntaxen zugeordnet werden, kann eine Anwendung entweder die Escapesequenz oder die DBMS-spezifische Syntax verwenden. Anwendungen, die die DBMS-spezifische Syntax verwenden, sind jedoch nicht interoperabel. Bei Verwendung der Escapesequenz sollten Anwendungen sicherstellen, dass das Attribut SQL_ATTR_NOSCAN Anweisung deaktiviert ist, was standardmäßig der Fall ist. Andernfalls wird die Escapesequenz direkt an die Datenquelle gesendet, wo sie in der Regel einen Syntaxfehler verursacht.  
  
 Treiber unterstützen nur die Escapesequenzen, die sie den zugrunde liegenden Sprachfeatures zuordnen können. Wenn die Datenquelle z. B. keine äußeren Verknüpfungen unterstützt, wird der Treiber auch nicht. Um zu bestimmen, welche Escapesequenzen unterstützt werden, ruft eine Anwendung **SQLGetTypeInfo** und **SQLGetInfo**auf. Weitere Informationen finden Sie im nächsten [Abschnitt, Datum, Uhrzeit und Zeitstempelliterale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Datums-, Zeit- und Zeitstempelliterale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [Aufrufe von Skalarfunktionen](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [Escapezeichen des LIKE-Prädikats](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [Äußere Verknüpfungen](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md)
