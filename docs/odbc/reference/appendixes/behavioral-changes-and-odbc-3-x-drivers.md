---
title: Verhaltensänderungen und ODBC 3.x-Treibern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_attr_odbc_version [ODBC]
- backward compatibility [ODBC], behavioral changes
- compatibility [ODBC], behavioral changes
ms.assetid: 88a503cc-bff7-42d9-83ff-8e232109ed06
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e386aa60489fe3edb2caac3cb49ebad263ffdfac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740048"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Verhaltensänderungen und ODBC 3.x-Treiber
Umgebungsattributs gibt SQL_ATTR_ODBC_VERSION an den Treiber an, ob sie ODBC 2. aufweisen muss. *x* Verhalten oder ODBC 3.*.x* Verhalten. Wie umgebungsattributs SQL_ATTR_ODBC_VERSION festgelegt wird, hängt von der Anwendung ab. ODBC 3.*.x* müssen Anwendungen Aufrufen **SQLSetEnvAttr** , dieses Attribut festzulegen, nachdem sie rufen **SQLAllocHandle** ein Umgebungshandle und vor dem Aufruf von  **SQLAllocHandle** ein Verbindungshandle zuordnen. Wenn sie nicht dies tun, gibt der Treiber-Manager SQLSTATE HY010 (Funktion Sequenzfehler) auf dem letzten Aufruf von **SQLAllocHandle**.  
  
> [!NOTE]  
>  Weitere Informationen zu verhaltensänderungen und wie eine Anwendung fungiert, finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 ODBC-2. *x* Anwendungen und ODBC 2. *X* Anwendungen erneut kompiliert, mit der ODBC 3.*.x* rufen Sie Headerdateien nicht **SQLSetEnvAttr**. Allerdings rufen sie **SQLAllocEnv** anstelle von **SQLAllocHandle** ein Umgebungshandle zuordnen. Wenn daher die Anwendung ruft **SQLAllocEnv** im Treiber-Manager, der Treiber-Manager ruft **SQLAllocHandle** und **SQLSetEnvAttr** im Treiber. Daher ODBC 3.*.x* Treiber immer Zuständen dieses Attribut festgelegt wird.  
  
 Wenn eine Standards kompatible Anwendung mit dem Flag für die Kompilierung ODBC_STD Aufrufe kompiliert **SQLAllocEnv** (die auftreten, da **SQLAllocEnv** ist nicht als veraltet markiert ISO-Datei), der Aufruf zugeordnet ist  **SQLAllocHandleStd** zum Zeitpunkt der Kompilierung. Zur Laufzeit ruft die Anwendung **SQLAllocHandleStd**. Der Treiber-Manager legt umgebungsattributs SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 fest. Ein Aufruf von **SQLAllocHandleStd** ist gleichbedeutend mit einem Aufruf von **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_ENV und einem Aufruf von **SQLSetEnvAttr** SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 festgelegt.  
  
 In bestimmten Treiberarchitekturen besteht es müssen für den Treiber als entweder einer ODBC 2. angezeigt werden. *x* Treiber oder eine ODBC 3.*.x* -Treiber verwenden, abhängig von der Verbindung. Der Treiber in diesem Fall nicht tatsächlich möglicherweise einen Treiber jedoch eine Ebene, die zwischen der Treiber-Manager und einem anderen Treiber befindet. Es kann beispielsweise einen Treiber, wie ODBC Spy imitieren. In einem anderen Beispiel könnte es als Gateway wie EDA/SQL fungieren. Als eine ODBC 3. angezeigt werden *.x* -Treiber können so ein Treiber muss für den export **SQLAllocHandle**, und als einer ODBC 2. angezeigt werden. *X* -Treiber verwenden, muss für den export **SQLAllocConnect**, **SQLAllocEnv**, und **SQLAllocStmt**. Wenn eine Umgebung, Verbindung oder Anweisung ist, die zugeordnet werden, überprüft der Treiber-Manager, um festzustellen, ob dieser Treiber exportiert **SQLAllocHandle**. Da der Treiber der Fall ist, die Treiber-Manager ruft **SQLAllocHandle** im Treiber. Wenn der Treiber mit einer ODBC 2. funktioniert. *x* -Treiber verwenden, muss der Treiber den Aufruf von zugeordnet **SQLAllocHandle** zu **SQLAllocConnect**, **SQLAllocEnv**, oder  **SQLAllocStmt**je nach Bedarf. Sie müssen auch nichts mit der **SQLSetEnvAttr** aufgerufen werden, wenn Sie als einer ODBC 2. verhält. *X* Treiber.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [datetime-Datentyp](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Abwärtskompatibilität von C-Datentypen](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Lesezeichen mit fester Länge](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [SQLGetInfo-Unterstützung](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Rückgabe von SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Calling SQLSetPos to Insert Data (Aufrufen von SQLSetPos zum Einfügen von Daten)](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Laden nach Ordnungszahl](../../../odbc/reference/appendixes/loading-by-ordinal.md)
