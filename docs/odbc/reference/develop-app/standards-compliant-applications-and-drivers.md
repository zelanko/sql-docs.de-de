---
title: Standardkonforme Anwendungen und Treiber | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299717"
---
# <a name="standards-compliant-applications-and-drivers"></a>Standardkonforme Anwendungen und Treiber
Eine standardkonforme Anwendung oder ein treiber entspricht der Open Group CAE Specification "Data Management: SQL Call-Level Interface (CLI)" und der ISO/IEC 9075-3:1995 (E) Call-Level Interface (SQL/CLI).  
  
 ODBC *3.x* garantiert folgende Funktionen:  
  
-   Eine Anwendung, die in die Open Group- und ISO CLI-Spezifikationen geschrieben wurde, funktioniert mit einem ODBC *3.x-Treiber* oder einem standardkonformen Treiber, wenn sie mit den ODBC *3.x-Headerdateien* kompiliert und mit ODBC *3.x-Bibliotheken* verknüpft wird und wenn sie über den ODBC *3.x-Treiber-Manager* Zugriff auf den Treiber erhält.  
  
-   Ein Treiber, der in die Open Group- und ISO CLI-Spezifikationen geschrieben wurde, funktioniert mit einer ODBC *3.x-Anwendung* oder einer standardkonformen Anwendung, wenn er mit den ODBC *3.x-Headerdateien* kompiliert und mit ODBC *3.x-Bibliotheken* verknüpft wird und wenn die Anwendung über den ODBC *3.x-Treiber-Manager* Zugriff auf den Treiber erhält.  
  
 Standardkonforme Anwendungen und Treiber werden mit dem ODBC_STD Kompilierungsflag kompiliert.  
  
 Standardkonforme Anwendungen weisen das folgende Verhalten auf:  
  
-   Wenn eine standardkonforme Anwendung **SQLAllocEnv** aufruft (was auftreten kann, da **SQLAllocEnv** eine gültige Funktion in der Open Group und ISO CLI ist), wird der Aufruf **SQLAllocHandleStd** zur Kompilierungszeit zugeordnet. Daher ruft die Anwendung zur Laufzeit **SQLAllocHandleStd**auf. Während der Verarbeitung dieses Aufrufs legt der Treiber-Manager das SQL_ATTR_ODBC_VERSION-Umgebungsattribut auf SQL_OV_ODBC3. Ein Aufruf von **SQLAllocHandleStd** entspricht einem Aufruf von **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV und einem Aufruf von **SQLSetEnvAttr,** um SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 festzulegen.  
  
-   Wenn eine standardkonforme Anwendung **SQLBindParam** aufruft (was auftreten kann, weil **SQLBindParam** eine gültige Funktion in der Open Group und ISO CLI ist), ordnet der ODBC *3.x-Treiber-Manager* den Aufruf dem entsprechenden Aufruf in **SQLBindParameter**zu. (Siehe [SQLBindParam-Zuordnung](../../../odbc/reference/appendixes/sqlbindparam-mapping.md) in Anhang G: Treiberrichtlinien für Die Abwärtskompatibilität.)  
  
-   Um an der ISO-CLI auszurichten, enthalten die ODBC *3.x-Headerdateien* Aliase für Informationstypen, die in Aufrufen von **SQLGetInfo**verwendet werden. Eine standardkonforme Anwendung kann diese Aliase anstelle der ODBC *3.x-Informationstypen* verwenden. Weitere Informationen finden Sie im nächsten [Thema, Headerfiles](../../../odbc/reference/develop-app/header-files.md).  
  
-   Eine standardkonforme Anwendung muss überprüfen, ob alle unterstützten Funktionen in dem Treiber unterstützt werden, mit dem sie arbeiten wird. Das Attribut SQL_ATTR_CURSOR_SCROLLABLE-Anweisung auf SQL_SCROLLABLE und das SQL_ATTR_CURSOR_SENSITIVITY-Anweisungsattribut auf SQL_INSENSITIVE oder SQL_SENSITIVE sind Funktionen, die als optionale Features in den Standards verfügbar sind, aber nicht in der ODBC *3.x* Core-Ebene enthalten sind und daher möglicherweise nicht von allen ODBC *3.x-Treibern* unterstützt werden. Wenn eine standardkonforme Anwendung diese Funktionen verwendet, sollte sie überprüfen, ob der Treiber, mit dem sie arbeitet, sie unterstützt.
