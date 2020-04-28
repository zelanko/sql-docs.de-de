---
title: Standardkonforme Anwendungen und Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- standards-compliant applications and drivers [ODBC]
- ODBC drivers [ODBC], standards-compliant
- application features are standards-compliant [ODBC]
ms.assetid: a1145c4c-3094-4f3f-8cc2-e6bb1a930ab1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b4daf2e777b20b1b84c090757d0d84796a4cae1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299717"
---
# <a name="standards-compliant-applications-and-drivers"></a>Standardkonforme Anwendungen und Treiber
Eine standardkonforme Anwendung oder ein Standardtreiber entspricht der Open Group CAE-Spezifikation "Datenverwaltung: SQL-Befehlszeilenschnittstelle (CLI)" und der "ISO/IEC 9075-3:1995 (E)"-Schnittstelle (SQL/CLI).  
  
 ODBC *3. x* garantiert die folgenden Features:  
  
-   Eine Anwendung, die in die Spezifikationen "Open Group" und "ISO CLI" geschrieben wird, funktioniert mit einem ODBC *3. x* -Treiber oder einem Standard kompatiblen Treiber, wenn dieser mit den ODBC *3. x* -Header Dateien kompiliert und mit ODBC *3* . x-Bibliotheken verknüpft ist und wenn er über den ODBC *3. x* -Treiber-Manager Zugriff auf den Treiber erhält.  
  
-   Ein Treiber, der in die Open Group-und ISO CLI-Spezifikationen geschrieben wird, funktioniert mit einer ODBC *3. x* -Anwendung oder einer Standard kompatiblen Anwendung, wenn diese mit den ODBC *3. x* -Header Dateien kompiliert und mit ODBC *3* . x-Bibliotheken verknüpft ist, und wenn die Anwendung über den ODBC *3. x* -Treiber-Manager Zugriff auf den Treiber erhält.  
  
 Standardkonforme Anwendungen und Treiber werden mit dem ODBC_STD Compile-Flag kompiliert.  
  
 Standardkonforme Anwendungen weisen folgendes Verhalten auf:  
  
-   Wenn eine standardkonforme Anwendung **sqlzuzuordcenv** aufruft (was möglicherweise darauf liegt, dass **sqldepcenv** eine gültige Funktion in der Open Group-und ISO-CLI ist), wird der Aufruf **sqlzuzuordchandlestd** zur Kompilierzeit zugeordnet. Demzufolge wird von der Anwendung zur Laufzeit **sqlzuzugerlestd**aufgerufen. Während der Verarbeitung dieses Aufrufes wird vom Treiber-Manager das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut auf SQL_OV_ODBC3 festgelegt. Ein-Befehl von **sqlzuweichandlestd** entspricht einem **sqlzuordchandle** -Befehl mit dem *Typ* "SQL_HANDLE_ENV" und einem **SQLSetEnvAttr** -Befehl, um SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 festzulegen.  
  
-   Wenn eine standardkonforme Anwendung **SQLBindParam** aufruft (da **SQLBindParam** eine gültige Funktion in der Open Group-und der ISO-CLI ist), ordnet der ODBC *3. x* -Treiber-Manager den Aufruf dem entsprechenden-Aufruf in **SQLBindParameter**zu. (Siehe [SQLBindParam-Zuordnung](../../../odbc/reference/appendixes/sqlbindparam-mapping.md) in Anhang G: Treiber Richtlinien zur Abwärtskompatibilität.)  
  
-   Die ODBC *3. x* -Header Dateien enthalten Aliase für Informationstypen, die in Aufrufen von **SQLGetInfo**verwendet werden, um die ISO CLI auszurichten. Eine standardkonforme Anwendung kann diese Aliase anstelle der ODBC *3. x* -Informationstypen verwenden. Weitere Informationen finden Sie im nächsten Thema [Header Dateien](../../../odbc/reference/develop-app/header-files.md).  
  
-   Eine mit Standards kompatible Anwendung muss überprüfen, ob alle unterstützten Funktionen in dem Treiber unterstützt werden, mit dem Sie arbeiten wird. Das Festlegen des SQL_ATTR_CURSOR_SCROLLABLE Anweisungs Attributs auf SQL_SCROLLABLE und das Festlegen des SQL_ATTR_CURSOR_SENSITIVITY Statement-Attributs auf SQL_INSENSITIVE oder SQL_SENSITIVE sind Funktionen, die als optionale Features in den Standards verfügbar sind, aber nicht in der ODBC *3. x* -kernstufe enthalten sind und daher möglicherweise nicht von allen ODBC *3. x* -Treibern unterstützt werden. Wenn eine standardkonforme Anwendung diese Funktionen verwendet, sollte überprüft werden, ob der Treiber, mit dem Sie arbeiten wird, Sie unterstützt.
