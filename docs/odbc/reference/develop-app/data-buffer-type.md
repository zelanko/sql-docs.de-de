---
title: Datenpuffertyp | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b98ed2ab0865b98884f6dfa1ff20142540ff314
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305246"
---
# <a name="data-buffer-type"></a>Datenpuffertyp
Der C-Datentyp eines Puffers wird von der Anwendung angegeben. Bei einer einzelnen Variablen tritt dies auf, wenn die Anwendung die Variable zuweist. Bei generischem Speicher - d. h. Speicher, auf den ein Zeiger vom Typ void zeigt - tritt dies auf, wenn die Anwendung den Speicher auf einen bestimmten Typ umgibt. Der Treiber entdeckt diesen Typ auf zwei Arten:  
  
-   **Argument des Datenpuffertyps.** Puffer, die zum Übertragen von Parameterwerten und Resultsatzdaten verwendet werden, z. B. der mit *TargetValuePtr* in **SQLBindCol**gebundene Puffer, verfügen in der Regel über ein zugeordnetes Typargument, z. B. das *TargetType-Argument* in **SQLBindCol**. In diesem Argument übergibt die Anwendung den C-Typbezeichner, der dem Typ des Puffers entspricht. Im folgenden Aufruf von **SQLBindCol**teilt der Wert SQL_C_TYPE_DATE dem Treiber beispielsweise mit, dass der *Date-Puffer* ein SQL_DATE_STRUCT ist:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Weitere Informationen zu Typbezeichnern finden Sie im Abschnitt [Datentypen im ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md) weiter unten in diesem Abschnitt.  
  
-   **Vordefinierter Typ.** Puffer, die zum Senden und Abrufen von Optionen oder Attributen verwendet werden, z. B. der Puffer, auf den das *InfoValuePtr-Argument* in **SQLGetInfo**zeigt, haben einen festen Typ, der von der angegebenen Option abhängt. Der Treiber geht davon aus, dass der Datenpuffer von diesem Typ ist. Es liegt in der Verantwortung der Anwendung, einen Puffer dieses Typs zuzuweisen. Im folgenden Aufruf von **SQLGetInfo**geht der Treiber beispielsweise davon aus, dass es sich bei dem Puffer um eine 32-Bit-Ganzzahl handelt, da dies die SQL_STRING_FUNCTIONS Option erfordert:  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Der Treiber verwendet den Datentyp C, um die Daten im Puffer zu interpretieren.
