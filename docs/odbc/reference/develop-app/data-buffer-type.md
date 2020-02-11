---
title: Daten Puffertyp | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 615625ca396e5f2ae094962457cc9e746730ddcf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68067411"
---
# <a name="data-buffer-type"></a>Datenpuffertyp
Der C-Datentyp eines Puffers wird von der Anwendung angegeben. Bei einer einzelnen Variablen tritt dieser Fehler auf, wenn die-Variable von der Anwendung zugewiesen wird. Mit generischem Speicher, d. h. dem Speicher, auf den von einem Zeiger vom Typ "void" verwiesen wird, tritt dieser Fehler auf, wenn die Anwendung den Speicher in einen bestimmten Typ umwandelt Der Treiber ermittelt diesen Typ auf zwei Arten:  
  
-   **Argument des Datenpuffer Typs.** Puffer, die zum Übertragen von Parameterwerten und Resultsetdaten verwendet werden, wie z. b. der mit *targetvalueptr* in **SQLBindCol**gebundene Puffer, verfügen in der Regel über ein zugeordnetes Typargument, **z. b**. das *TargetType* -Argument in In diesem Argument übergibt die Anwendung den C-Typbezeichner, der dem Typ des Puffers entspricht. Im folgenden Befehl von **SQLBindCol**weist der Wert SQL_C_TYPE_DATE dem Treiber z. b. an, dass der *Datums* Puffer ein SQL_DATE_STRUCT ist:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Weitere Informationen zu typbezeichatoren finden Sie im Abschnitt " [Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md) " weiter unten in diesem Abschnitt.  
  
-   **Vordefinierter Typ.** Puffer, die zum Senden und Abrufen von Optionen oder Attributen verwendet werden, wie z. b. der Puffer, auf den das *infovalueptr* -Argument in **SQLGetInfo**zeigt, verfügen über einen Fixed-Typ, der von der angegebenen Option abhängt. Der Treiber geht davon aus, dass der Datenpuffer diesen Typ hat. Es liegt in der Verantwortung der Anwendung, einen Puffer dieses Typs zuzuordnen. Im folgenden Befehl von **SQLGetInfo**nimmt der Treiber z. b. an, dass der Puffer eine 32-Bit-Ganzzahl ist, da dies für die SQL_STRING_FUNCTIONS-Option erforderlich ist:  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Der Treiber verwendet den C-Datentyp, um die Daten im Puffer zu interpretieren.
