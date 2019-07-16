---
title: Den Standards entsprechende Anwendungen und Treiber | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4980cfe64a5a8e8404c6b5b0bdc8b1aba484f0c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107329"
---
# <a name="standards-compliant-applications-and-drivers"></a>Standardkonforme Anwendungen und Treiber
Eine Standards kompatible Anwendung oder der Treiber ist eine, die die Open Group CAE-Spezifikation entspricht "Datenverwaltung: SQL-Call-Level-Interface (CLI)"und dem ISO/IEC 9075-3:1995 (E)-Call-Level-Interface (SQL/CLI).  
  
 ODBC *3.x* garantiert die folgenden Funktionen:  
  
-   Eine Anwendung geschrieben, um die Open Group und ISO-CLI-Spezifikationen funktioniert mit einer ODBC- *3.x* Treiber oder eine Standards kompatible beim Kompilieren mit der ODBC-Treiber *3.x* Header-Dateien und verknüpft mit ODBC *3.x* Bibliotheken, und wenn sie den Zugriff auf den über die ODBC-Treiber erhält *3.x* -Treiber-Manager.  
  
-   Mit einer ODBC-Treiber geschrieben, um die Open Group und ISO-CLI-Spezifikationen funktioniert *3.x* Anwendung oder eine Standards kompatible Anwendung, wenn die Kompilierung mit der ODBC *3.x* Header-Dateien und verknüpft mit dem ODBC- *3.x* Bibliotheken, und wenn die Anwendung erhält Zugriff auf den über die ODBC-Treiber *3.x* -Treiber-Manager.  
  
 Den Standards entsprechende Anwendungen und Treiber werden mit dem Flag für ODBC_STD Kompilierung kompiliert.  
  
 Den Standards entsprechende Anwendungen weisen folgende Verhalten:  
  
-   Wenn eine Standards kompatible Anwendung aufruft, **SQLAllocEnv** (das kann auftreten, weil **SQLAllocEnv** ist eine gültige Funktion in der Open Group und ISO-CLI), der Aufruf zugeordnet ist  **SQLAllocHandleStd** zum Zeitpunkt der Kompilierung. Zur Laufzeit ruft die Anwendung daher **SQLAllocHandleStd**. Im Verlauf der Verarbeitung dieser Aufruf wird der Treiber-Manager das SQL_ATTR_ODBC_VERSION-Umgebung-Attribut auf SQL_OV_ODBC3 fest. Ein Aufruf von **SQLAllocHandleStd** ist gleichbedeutend mit einem Aufruf von **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_ENV und einem Aufruf von **SQLSetEnvAttr** SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 festgelegt.  
  
-   Wenn eine Standards kompatible Anwendung aufruft, **SQLBindParam** (das kann auftreten, weil **SQLBindParam** ist eine gültige Funktion in der Open Group und ISO-CLI), die ODBC *3.x* Treiber-Manager, ordnet den Aufruf an den entsprechenden Aufruf in **SQLBindParameter**. (Finden Sie unter [SQLBindParam-Zuordnung](../../../odbc/reference/appendixes/sqlbindparam-mapping.md) in Anhang G: Treiber-Richtlinien für Abwärtskompatibilität.)  
  
-   Die ISO-CLI die ODBC ausgerichtet *3.x* Headerdateien enthalten Aliase für Informationstypen, die in Aufrufen verwendet **SQLGetInfo**. Eine Standards kompatible Anwendung kann diese Aliase verwenden, anstatt die ODBC *3.x* Informationstypen. Weitere Informationen finden Sie im nächste Thema, [Headerdateien](../../../odbc/reference/develop-app/header-files.md).  
  
-   Eine Standards kompatible Anwendung muss überprüfen Sie, ob alle Features, die es unterstützt in der Treiber unterstützt werden, mit denen sie zusammenarbeiten werden. Das Anweisungsattribut SQL_ATTR_CURSOR_SCROLLABLE auf SQL_SCROLLABLE und Einstellung festlegen Anweisungsattribut den SQL_ATTR_CURSOR_SENSITIVITY auf SQL_INSENSITIVE oder SQL_SENSITIVE sind Funktionen, die als optionale Funktionen in den Standards verfügbar sind. jedoch nicht enthalten sind, die ODBC *3.x* Core level und daher möglicherweise nicht unterstützt alle ODBC *3.x* Treiber. Eine Standards kompatible Anwendung dieser Funktionen verwendet, sollten sie sicher, dass der Treiber, dem er arbeitet unterstützt.
