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
manager: craigg
ms.openlocfilehash: 33259a56faa19dda2403996b6d6d8930ec2a87be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705998"
---
# <a name="escape-sequences-in-odbc"></a>Escapesequenzen in ODBC
Eine Anzahl von Sprachfeatures wie äußere Joins und Aufrufe von Skalarfunktionen werden häufig von DBMS implementiert. Allerdings sind tendenziell die Syntax für diese Funktionen DBMS-spezifische, selbst wenn der standard-Syntax durch die verschiedene Standardorganisationen definiert werden. Aus diesem Grund werden in ODBC-Escapesequenzen, die standard-Syntax für die folgenden Sprachfunktionen enthalten definiert:  
  
-   Datum "," Time "," Timestamp "und" Datetime-Intervall-Literale  
  
-   Skalare Funktionen wie z. B. numerische Zeichenfolge und Funktionen für die typkonvertierung Daten  
  
-   WIE Prädikat Escape-Zeichen  
  
-   Äußere Joins  
  
-   Prozeduraufrufe  
  
 Die Escapesequenz für ODBC verwendeten lautet wie folgt aus:  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>Hinweise  
 Die Escape-Sequenz erkannt und analysiert von Treibern, die die Escapesequenzen mit speziellen DBMS-Grammatik zu ersetzen. Weitere Informationen zu escapesequenzsyntax, finden Sie unter [Escapesequenzen für ODBC](../../../odbc/reference/appendixes/odbc-escape-sequences.md) in Anhang C: SQL-Grammatik.  
  
> [!NOTE]  
>  In ODBC 2. *x*, dies war die Standardsyntax der Escapesequenz: **--(\*Hersteller (***Herstellername***), Product (***Produktnamens***) *** Erweiterung*  **\*)--**  
>   
>  Zusätzlich zu dieser Syntax eine Kurzsyntax des Formulars definiert wurde: **{***Erweiterung***}**  
>   
>  In ODBC 3. *x*die Langform der Escapesequenz ist veraltet und wird ausschließlich die Kurzform verwendet.  
  
 Da die Escapesequenzen, die vom Treiber auf die Syntax der DBMS-spezifische Eigenschaften zugeordnet sind, kann eine Anwendung, entweder die Escape-Sequenz oder die DBMS-spezifische Syntax verwenden. Anwendungen, die die DBMS-spezifische Syntax verwenden, werden jedoch nicht interoperabel sein. Wenn Sie die Escape-Sequenz zu verwenden, sollten Anwendungen sicherstellen, dass es sich bei der SQL_ATTR_NOSCAN-Anweisungsattribut deaktiviert ist, wird es standardmäßig. Andernfalls wird die Escape-Sequenz direkt an die Datenquelle gesendet werden, in denen sie in der Regel einen Syntaxfehler führt.  
  
 Treiber unterstützen nur die Escape-Sequenzen, die sie zum zugrunde liegenden Sprachfeatures zuordnen können. Z. B. wenn die Datenquelle keine äußeren Joins unterstützt, weder wird des Treibers. Um zu bestimmen, welche Escapesequenzen unterstützt werden, eine Anwendung ruft **SQLGetTypeInfo** und **SQLGetInfo**. Weitere Informationen finden Sie im nächsten Abschnitt [Date, Time und Timestamp-Literale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Datums-, Zeit- und Timestampliterale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [Aufrufe von Skalarfunktionen](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [Escapezeichen des LIKE-Prädikats](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [Äußere Joins](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md)
