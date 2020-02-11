---
title: Escapesequenzen in ODBC | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17183a7eacdc5348eea0ddcd7aee4cc493249e77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68051119"
---
# <a name="escape-sequences-in-odbc"></a>Escapesequenzen in ODBC
Eine Reihe von sprach Features, wie z. b. äußere Joins und skalarfunktionsaufrufe, werden häufig von DBMSs implementiert. Die Syntaxen für diese Features sind jedoch tendenziell DBMS-spezifisch, auch wenn standardmäßige Syntaxen durch die verschiedenen Standardtexte definiert werden. Aus diesem Grund definiert ODBC Escapesequenzen, die Standard Syntaxen für die folgenden sprach Features enthalten:  
  
-   Datums-, Uhrzeit-, timestamp-und DateTime-Intervall Literale  
  
-   Skalarfunktionen wie z. b. numerische, Zeichen folgen-und Datentyp-Konvertierungs Funktionen  
  
-   LIKE-Prädikat-Escapezeichen  
  
-   Äußere Joins  
  
-   Prozedur Aufrufe  
  
 Die von ODBC verwendete Escapesequenz lautet wie folgt:  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die Escapesequenz wird von Treibern erkannt und analysiert, die die Escapesequenzen durch DBMS-spezifische Grammatik ersetzen. Weitere Informationen zur Escapesequenzsyntax finden Sie unter [ODBC](../../../odbc/reference/appendixes/odbc-escape-sequences.md) -Escapesequenzen in Anhang C: SQL-Grammatik.  
  
> [!NOTE]  
>  In ODBC 2. *x*, dies war die Standard Syntax der Escapesequenz: **--\*(Hersteller**_Name_**), Produkt**_Erweiterung_ __**** ** \*** (Produktname))--  
>   
>  Zusätzlich zu dieser Syntax wurde eine Kurzform-Syntax im folgenden Format definiert: **{**_Extension_**}**  
>   
>  In ODBC 3. *x*, die lange Form der Escapesequenz ist veraltet, und die Kurzform wird exklusiv verwendet.  
  
 Da die Escapesequenzen vom Treiber der DBMS-spezifischen Syntax zugeordnet werden, kann eine Anwendung entweder die Escapesequenz oder DBMS-spezifische Syntax verwenden. Anwendungen, die die DBMS-spezifische Syntax verwenden, sind jedoch nicht interoperabel. Bei Verwendung der Escapesequenz sollten Anwendungen sicherstellen, dass das Attribut der SQL_ATTR_NOSCAN Anweisung deaktiviert ist, was standardmäßig ist. Andernfalls wird die Escapesequenz direkt an die Datenquelle gesendet, wo Sie in der Regel einen Syntax Fehler verursacht.  
  
 Treiber unterstützen nur die Escapesequenzen, die den zugrunde liegenden Sprachfunktionen zugeordnet werden können. Wenn die Datenquelle z. b. keine äußeren Joins unterstützt, ist keiner der Treiber. Um zu ermitteln, welche Escapesequenzen unterstützt werden, ruft eine Anwendung **sqlgettypeingefo** und **SQLGetInfo**auf. Weitere Informationen finden Sie im nächsten Abschnitt, [Datums-, Uhrzeit-und Timestamp-Literale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Datums-, Zeit- und Zeitstempelliterale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [Aufrufe von Skalarfunktionen](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [Escapezeichen des LIKE-Prädikats](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [Äußere Verknüpfungen](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md)
