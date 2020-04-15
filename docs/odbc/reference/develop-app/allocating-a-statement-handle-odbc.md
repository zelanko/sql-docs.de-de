---
title: Zuweisen eines Anweisungshandles ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf9a15bc4622b15afa9838327edd90383a812270
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288430"
---
# <a name="allocating-a-statement-handle-odbc"></a>Zuordnen eines ODBC-Anweisungshandles
Bevor die Anwendung eine Anweisung ausführen kann, muss sie ein Anweisungshandle wie folgt zuweisen:  
  
1.  Die Anwendung deklariert eine Variable vom Typ HSTMT. Anschließend wird **SQLAllocHandle** aufund die Adresse dieser Variablen, das Handle der Verbindung, in der die Anweisung zugewiesen werden soll, und die SQL_HANDLE_STMT-Option übergibt. Beispiel:  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Der Treiber-Manager weist eine Struktur zu, in der Informationen über die Anweisung gespeichert werden sollen, und ruft **SQLAllocHandle** im Treiber mit der Option SQL_HANDLE_STMT auf.  
  
3.  Der Treiber weist eine eigene Struktur zu, in der Informationen über die Anweisung gespeichert werden sollen, und gibt das Treiberanweisungshandle an den Treiber-Manager zurück.  
  
4.  Der Treiber-Manager gibt das Driver Manager-Anweisungshandle an die Anwendung in der Anwendungsvariablen zurück.  
  
 Das Anweisungshandle identifiziert, welche Anweisung beim Aufrufen von ODBC-Funktionen verwendet werden soll. Weitere Informationen zu Anweisungshandles finden Sie unter [Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md).
