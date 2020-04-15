---
title: Microsoft ODBC Desktop-Datenbanktreiber | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- Jet-based ODBC drivers [ODBC]
- ODBC desktop database drivers [ODBC], about desktop database drivers
- desktop database drivers [ODBC]
- Jet-based ODBC drivers [ODBC], about Jet-based ODBC drivers
- desktop database drivers [ODBC], about desktop database drivers
ms.assetid: 4e505c65-a8dd-4283-ae28-313d8a3aa046
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 99da8943f738d879a0a1bb66f6cfdbd6156c17ee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302981"
---
# <a name="microsoft-odbc-desktop-database-drivers"></a>Microsoft ODBC Desktop-Datenbanktreiber
ODBC ist eine API, die Structured Query Language (SQL) als Datenbankzugriffssprache verwendet. Sie können auf eine Vielzahl von Datenbankverwaltungssystemen (DBMS) mit demselben ODBC-Quellcode zugreifen, der direkt in den Quellcode einer Anwendung integriert ist. Mit den Microsoft ODBC-Desktopdatenbanktreibern kann ein Benutzer einer ODBC-fähigen Anwendung eine Desktopdatenbank über die ODBC-Schnittstelle öffnen, abfragen und aktualisieren.  
  
 Die Microsoft ODBC-Desktopdatenbanktreiber sind ein Aufsatz von ODBC-Treibern, die auf Microsoft Jet basieren. Während Microsoft ODBC Desktop Database Drivers 2.0 sowohl 16-Bit- als auch 32-Bit-Treiber enthalten, enthalten die Versionen 3.0 und höher nur 32-Bit-Treiber, die unter Windows 95 oder höher funktionieren, Windows NT Workstation oder Server Version 4.0, Windows 2000 Professional oder Windows 2000 Server. Diese Treiber bieten Zugriff auf die folgenden Arten von Datenquellen:  
  
-   Microsoft Access  
  
-   Microsoft Excel  
  
-   Paradox  
  
-   Dbase  
  
-   Text  
  
 Ausführliche Dokumentation zum Microsoft Visual FoxPro® ODBC-Treiber finden Sie unter [Visual FoxPro ODBC-Treiber.](../../odbc/microsoft/visual-foxpro-odbc-driver.md)  
  
> [!NOTE]  
>  Der Zugriff auf andere Datenquellen wie Lotus 1-2-3, Microsoft Exchange und HTML wird durch installierbare ISAM-Treiber (IISAM) ermöglicht. Weitere Informationen zu diesen Treibern finden Sie unter "Zugriff auf externe Daten" in der Referenz des *Microsoft Jet Database Engine-Programmierers*. ODBC Desktop Database Drivers 4.0 unterstützen keine Btrieve- und EMS-Datenformate.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Architektur der Desktop-Datenbanktreiber](../../odbc/microsoft/desktop-database-drivers-architecture.md)  
  
-   [Versionsgeschichte der Desktop-Datenbanktreiber](../../odbc/microsoft/history-of-the-desktop-database-drivers.md)  
  
-   [Produktsupport](../../odbc/microsoft/product-support.md)  
  
-   [Implementieren der Desktop-Datenbanktreiber](../../odbc/microsoft/implementing-desktop-database-drivers.md)  
  
-   [Überlegungen zur Programmierung von Microsoft Access-Treibern](../../odbc/microsoft/microsoft-access-driver-programming-considerations.md)  
  
-   [Überlegungen zur Programmierung von Microsoft Excel-Treibern](../../odbc/microsoft/microsoft-excel-driver-programming-considerations.md)  
  
-   [Überlegungen zur Programmierung von Paradox-Treibern](../../odbc/microsoft/paradox-driver-programming-considerations.md)  
  
-   [Überlegungen zur Programmierung von dBASE-Treibern](../../odbc/microsoft/dbase-driver-programming-considerations.md)  
  
-   [Überlegungen zur Programmierung von Textdateitreibern](../../odbc/microsoft/text-file-driver-programming-considerations.md)  
  
-   [Zusätzliche unterstützte ODBC-SQL-Grammatik](../../odbc/microsoft/additional-supported-odbc-sql-grammar.md)  
  
-   [Einschränkungen](../../odbc/microsoft/limitations.md)  
  
-   [ODBC-Fehler](../../odbc/microsoft/odbc-errors.md)  
  
-   [Unterstützte ODBC-API-Funktionen](../../odbc/microsoft/supported-odbc-api-functions.md)
