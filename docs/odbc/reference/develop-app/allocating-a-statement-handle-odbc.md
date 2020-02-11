---
title: Zuordnen eines Anweisungs Handles (ODBC) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d50b0a31aed4935c805ca30620575ccff70d4a0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077202"
---
# <a name="allocating-a-statement-handle-odbc"></a>Zuordnen eines ODBC-Anweisungshandles
Bevor die Anwendung eine-Anweisung ausführen kann, muss Sie wie folgt ein Anweisungs Handle zuordnen:  
  
1.  Die Anwendung deklariert eine Variable vom Typ HSTMT. Anschließend wird **SQLAllocHandle** aufgerufen und die Adresse dieser Variablen, das Handle der Verbindung, in der die Anweisung zugeordnet werden soll, und die SQL_HANDLE_STMT Option weitergeleitet. Beispiel:  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Der Treiber-Manager ordnet eine Struktur zu, in der Informationen über die-Anweisung gespeichert werden, und ruft **sqlzugewiesene CHandle** im Treiber mit der SQL_HANDLE_STMT-Option auf.  
  
3.  Der Treiber weist seine eigene Struktur zu, in der Informationen über die Anweisung gespeichert werden, und gibt das Treiber Anweisungs Handle an den Treiber-Manager zurück.  
  
4.  Der Treiber-Manager gibt das Treiber-Manager-Anweisungs Handle an die Anwendung in der Anwendungsvariablen zurück.  
  
 Das Anweisungs Handle identifiziert, welche Anweisung beim Aufrufen von ODBC-Funktionen verwendet werden soll. Weitere Informationen zu Anweisungs Handles finden Sie unter [Anweisungs Handles](../../../odbc/reference/develop-app/statement-handles.md).
