---
title: Verhaltensänderungen und ODBC 3.x-Treiber | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4d8343573261d74a6a0c652cf425b12da91f7cb0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292364"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Verhaltensänderungen und ODBC 3.x-Treiber
Das Umgebungsattribut SQL_ATTR_ODBC_VERSION zeigt dem Treiber an, ob es ODBC *2.x-Verhalten* oder ODBC *3.x-Verhalten* aufweisen muss. Wie das SQL_ATTR_ODBC_VERSION Umgebungsattribut s. festgelegt wird, hängt von der Anwendung ab. ODBC *3.x-Anwendungen* müssen **SQLSetEnvAttr** aufrufen, um dieses Attribut zu setzen, nachdem sie **SQLAllocHandle** aufrufen, um ein Umgebungshandle zuzuweisen, und bevor sie **SQLAllocHandle** aufrufen, um ein Verbindungshandle zuzuweisen. Wenn dies nicht der Fall ist, gibt der Treiber-Manager SQLSTATE HY010 (Funktionssequenzfehler) für den letztgenannten Aufruf von **SQLAllocHandle**zurück.  
  
> [!NOTE]  
>  Weitere Informationen zu Verhaltensänderungen und der Funktionsweise einer Anwendung finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 ODBC *2.x-Anwendungen* und ODBC *2.x-Anwendungen,* die mit den ODBC *3.x-Headerdateien* neu kompiliert wurden, rufen **SQLSetEnvAttr**nicht auf. Sie rufen jedoch **SQLAllocEnv** anstelle von **SQLAllocHandle** auf, um ein Umgebungshandle zuzuweisen. Wenn die Anwendung **SQLAllocEnv** im Treiber-Manager aufruft, ruft der Treiber-Manager **daher SQLAllocHandle** und **SQLSetEnvAttr** im Treiber auf. Daher können ODBC *3.x-Treiber* immer darauf zählen, dass dieses Attribut festgelegt wird.  
  
 Wenn eine standardkonforme Anwendung, die mit dem ODBC_STD Kompilierungsflag kompiliert wird, **SQLAllocEnv** aufruft (was auftreten kann, weil **SQLAllocEnv** in ISO nicht veraltet ist), wird der Aufruf **SQLAllocHandleStd** zur Kompilierungszeit zugeordnet. Zur Laufzeit ruft die Anwendung **SQLAllocHandleStd**auf. Der Treiber-Manager legt das SQL_ATTR_ODBC_VERSION-Umgebungsattribut auf SQL_OV_ODBC3 fest. Ein Aufruf von **SQLAllocHandleStd** entspricht einem Aufruf von **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV und einem Aufruf von **SQLSetEnvAttr,** um SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 festzulegen.  
  
 In bestimmten Treiberarchitekturen muss der Treiber je nach Verbindung entweder als ODBC *2.x-Treiber* oder als ODBC *3.x-Treiber* angezeigt werden. Der Treiber ist in diesem Fall möglicherweise kein Treiber, sondern ein Layer, der sich zwischen dem Treiber-Manager und einem anderen Treiber befindet. Beispielsweise könnte es einen Treiber imitieren, wie ODBC Spy. In einem anderen Beispiel kann es als Gateway fungieren, z. B. EDA/SQL. Um als ODBC *3.x-Treiber* angezeigt zu werden, muss ein solcher Treiber **SQLAllocHandle**exportieren und als ODBC *2.x-Treiber* angezeigt werden, **SQLAllocConnect**, **SQLAllocEnv**und **SQLAllocStmt**exportieren können. Wenn eine Umgebung, Verbindung oder Anweisung zugewiesen werden soll, überprüft der Treiber-Manager, ob dieser Treiber **SQLAllocHandle**exportiert. Da der Treiber dies tut, ruft der Treiber-Manager **SQLAllocHandle** im Treiber auf. Wenn der Treiber mit einem ODBC *2.x-Treiber* arbeitet, muss der Treiber den Aufruf von **SQLAllocHandle** **SQLAllocConnect**, **SQLAllocEnv**oder **SQLAllocStmt**, entsprechend zuordnen. Es darf auch nichts mit dem **SQLSetEnvAttr-Aufruf** tun, wenn er sich als ODBC *2.x-Treiber* verhält.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [datetime-Datentyp](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Abwärtskompatibilität von C-Datentypen](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Lesezeichen mit fester Länge](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [SQLGetInfo-Unterstützung](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Rückgabe von SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Calling SQLSetPos to Insert Data (Aufrufen von SQLSetPos zum Einfügen von Daten)](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Laden nach Ordnungszahl](../../../odbc/reference/appendixes/loading-by-ordinal.md)
