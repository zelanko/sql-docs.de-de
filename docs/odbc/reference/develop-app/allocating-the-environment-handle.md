---
title: Zuweisen des Umwelthandles | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e33b850b2786960a368720deaf89a2203c7dd159
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303003"
---
# <a name="allocating-the-environment-handle"></a>Zuordnen des Umgebungshandles
Die erste Aufgabe für jede ODBC-Anwendung besteht darin, den Treiber-Manager zu laden. Wie dies geschieht, ist betriebssystemabhängig. Auf einem Computer, auf dem Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT Workstation/Windows 2000 Professional oder Microsoft Windows® 95/98 ausgeführt wird, verknüpft die Anwendung entweder die Treiber-Manager-Bibliothek oder ruft **LoadLibrary** auf, um die Treiber-Manager-DLL zu laden.  
  
 Die nächste Aufgabe, die ausgeführt werden muss, bevor eine Anwendung eine andere ODBC-Funktion aufrufen kann, besteht darin, die ODBC-Umgebung zu initialisieren und ein Umgebungshandle wie folgt zuzuweisen:  
  
1.  Die Anwendung deklariert eine Variable vom Typ SQLHENV. Anschließend wird **SQLAllocHandle** aufund die Adresse dieser Variablen und die Option SQL_HANDLE_ENV. Beispiel:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Der Treiber-Manager weist eine Struktur zu, in der Informationen über die Umgebung gespeichert werden sollen, und gibt das Umgebungshandle in der Variablen zurück.  
  
 Der Treiber-Manager ruft **SQLAllocHandle** derzeit nicht im Treiber auf, da er nicht weiß, welchen Treiber er aufrufen soll. Es verzögert den Aufruf von **SQLAllocHandle** im Treiber, bis die Anwendung eine Funktion zum Herstellen einer Verbindung mit einer Datenquelle aufruft. Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [Die Rolle des Treiber-Managers im Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Wenn die Anwendung odBC verwendet hat, wird das Umgebungshandle mit **SQLFreeHandle**frei. Nach dem Freilassen der Umgebung ist es ein Anwendungsprogrammierfehler, das Handle der Umgebung in einem Aufruf einer ODBC-Funktion zu verwenden. dies hat undefinierte, aber wahrscheinlich fatale Folgen.  
  
 Wenn **SQLFreeHandle** aufgerufen wird, gibt der Treiber die Struktur frei, die zum Speichern von Informationen über die Umgebung verwendet wird. Beachten Sie, dass **SQLFreeHandle** erst dann für ein Umgebungshandle aufgerufen werden kann, nachdem alle Verbindungshandles für dieses Umgebungshandle freigegeben wurden.  
  
 Weitere Informationen zum Umgebungshandle finden Sie unter [Umgebungshandles](../../../odbc/reference/develop-app/environment-handles.md).
