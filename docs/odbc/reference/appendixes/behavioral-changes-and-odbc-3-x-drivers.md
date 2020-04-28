---
title: Verhaltensänderungen und ODBC 3. x-Treiber | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292364"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Verhaltensänderungen und ODBC 3.x-Treiber
Das Umgebungs Attribut SQL_ATTR_ODBC_VERSION gibt dem Treiber an, ob es das ODBC *2. x* -oder ODBC *3. x* -Verhalten aufweisen muss. Wie das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut festgelegt wird, hängt von der Anwendung ab. ODBC *3. x* -Anwendungen müssen **SQLSetEnvAttr** aufzurufen, um dieses Attribut festzulegen, nachdem Sie **SQLAllocHandle** aufgerufen haben, um ein Umgebungs Handle zuzuordnen, und bevor Sie **SQLAllocHandle** zum Zuordnen eines Verbindungs Handles aufruft. Wenn dies nicht der Fall ist, gibt der Treiber-Manager SQLSTATE HY010 (Funktions Sequenz Fehler) bei letzterem **sqlzuzuweisung**-aufrufsbefehl zurück.  
  
> [!NOTE]  
>  Weitere Informationen zu Verhaltensänderungen und zur Funktionsweise einer Anwendung finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 ODBC *2. x* -Anwendungen und ODBC *2. x* -Anwendungen, die mit den ODBC *3. x* -Header Dateien neu kompiliert wurden, nennen nicht **SQLSetEnvAttr**. Allerdings wird **sqlallocenv** anstelle von **SQLAllocHandle** aufgerufen, um ein Umgebungs Handle zuzuordnen. Wenn die Anwendung **sqlzugecenv** im Treiber-Manager aufruft, ruft der Treiber-Manager daher im Treiber **sqlzuweisung** und **SQLSetEnvAttr** auf. Daher können ODBC *3. x* -Treiber immer darauf anrechnen, dass dieses Attribut festgelegt wird.  
  
 Wenn eine mit dem ODBC_STD Compile-Flag kompilierte standardkonforme Anwendung **sqlzuzuordcenv** aufruft (was möglicherweise darauf liegt, dass **sqldepcenv** in ISO nicht als veraltet markiert ist), wird der Aufruf zum Zeitpunkt der Kompilierung **sqlzuordchandlestd** zugeordnet. Zur Laufzeit ruft die Anwendung **sqlzugewiesene chandlestd**auf. Der Treiber-Manager legt das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut auf SQL_OV_ODBC3 fest. Ein-Befehl von **sqlzuweichandlestd** entspricht einem **sqlzuordchandle** -Befehl mit dem *Typ* "SQL_HANDLE_ENV" und einem **SQLSetEnvAttr** -Befehl, um SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 festzulegen.  
  
 In bestimmten Treiber Architekturen muss der Treiber abhängig von der Verbindung entweder als ODBC *2. x* -Treiber oder ODBC *3. x* -Treiber angezeigt werden. Der Treiber ist in diesem Fall möglicherweise kein Treiber, sondern eine Ebene, die sich zwischen dem Treiber-Manager und einem anderen Treiber befindet. Beispielsweise kann ein Treiber wie ODBC Spy imitiert werden. In einem anderen Beispiel kann es als Gateway, wie z. b. EDA/SQL, fungieren. Um als ODBC *3. x* -Treiber angezeigt zu werden, muss ein solcher Treiber **sqlzuzugchandle**exportieren können und als ODBC *2. x* -Treiber angezeigt werden. er muss in der Lage sein, **sqlzuzugcconnect**, **sqlzuzugcenv**und **sqlzugcstmt**zu exportieren. Wenn eine Umgebung, eine Verbindung oder eine Anweisung zugeordnet werden soll, überprüft der Treiber-Manager, ob der Treiber **sqlzuordchandle**exportiert. Da der Treiber dies durchführt, ruft der Treiber-Manager **sqlzugewiesene CHandle** im Treiber auf. Wenn der Treiber mit einem ODBC *2. x* -Treiber arbeitet, muss der Treiber den Befehl **sqlzuordchandle** entsprechend **sqlzugcconnect**, **sqlzuordcenv**oder **sqlzuordcstmt**zuordnen. Es muss auch nichts mit dem **sqlstenvattr** -Befehl durchführen, wenn er sich als ODBC *2. x* -Treiber verhält.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [datetime-Datentyp](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Abwärtskompatibilität von C-Datentypen](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Lesezeichen mit fester Länge](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [SQLGetInfo-Unterstützung](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Rückgabe von SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Calling SQLSetPos to Insert Data (Aufrufen von SQLSetPos zum Einfügen von Daten)](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Laden nach Ordnungszahl](../../../odbc/reference/appendixes/loading-by-ordinal.md)
