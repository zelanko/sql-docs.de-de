---
title: Microsoft ODBC Desktop-Datenbanktreiber | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302981"
---
# <a name="microsoft-odbc-desktop-database-drivers"></a>Microsoft ODBC Desktop-Datenbanktreiber
ODBC ist eine API, die strukturierte Abfragesprache (SQL) als Datenbankzugriffs Sprache verwendet. Sie können auf eine Vielzahl von Datenbank-Managementsystemen (DBMSs) mit demselben ODBC-Quellcode zugreifen, der direkt in den Quellcode einer Anwendung integriert ist. Mit den Microsoft ODBC Desktop-Daten Bank Treibern kann ein Benutzer einer ODBC-fähigen Anwendung eine Desktop Datenbank über die ODBC-Schnittstelle öffnen, Abfragen und aktualisieren.  
  
 Die Microsoft ODBC Desktop-Datenbanktreiber sind ein auf Microsoft Jet basierender Satz von ODBC-Treibern. Während Microsoft ODBC Desktop-Datenbanktreiber 2,0 sowohl 16-Bit-als auch 32-Bit-Treiber enthalten, enthalten die Versionen 3,0 und höher nur 32-Bit-Treiber, die unter Windows 95 oder höher, Windows NT-Arbeitsstation oder Server Version 4,0, Windows 2000 Professional oder Windows 2000 Server funktionieren. Diese Treiber ermöglichen den Zugriff auf die folgenden Typen von Datenquellen:  
  
-   Microsoft Access  
  
-   Microsoft Excel  
  
-   Gewissen  
  
-   dBASE  
  
-   Text  
  
 Ausführliche Dokumentation zum Microsoft Visual FoxPro-® ODBC-Treiber finden Sie unter [Visual FoxPro-ODBC-Treiber](../../odbc/microsoft/visual-foxpro-odbc-driver.md) .  
  
> [!NOTE]  
>  Der Zugriff auf andere Datenquellen, z. b. Lotus 1-2-3, Microsoft Exchange und HTML, wird durch installierbare ISAM-Treiber (IISAM) ermöglicht. Weitere Informationen zu diesen Treibern finden Sie im Abschnitt "zugreifen auf externe Daten" in der *Microsoft Jet Datenbank-Engine Programmierer-Referenz*. ODBC Desktop-Datenbanktreiber 4,0 unterstützen keine Btrieve-und EMS-Datenformate.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Architektur der Desktop-Datenbanktreiber](../../odbc/microsoft/desktop-database-drivers-architecture.md)  
  
-   [Versionsgeschichte der Desktop-Datenbanktreiber](../../odbc/microsoft/history-of-the-desktop-database-drivers.md)  
  
-   [Produkt Support](../../odbc/microsoft/product-support.md)  
  
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
