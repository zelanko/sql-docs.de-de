---
title: SQL Server Native Client (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 48fc5ccd2973a530010975171a90f35a2f18a7e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73760251"
---
# <a name="sql-server-native-client-odbc"></a>SQL Server Native Client (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC ist eine Standarddefinition einer API (Application Programming Interface, Schnittstelle für Anwendungsprogrammierung), die für den Zugriff auf Daten in relationalen oder ISAM-Datenbanken (Indexed Sequential Access Method, indizierte sequenzielle Zugriffsmethode) verwendet wird. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt ODBC (über den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber) als eine der systemeigenen APIs für das Schreiben von C- und C++-Anwendungen, die mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kommunizieren.  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Programme, die mithilfe des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treibers geschrieben wurden, kommunizieren mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über Funktionsaufrufe in C. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifischen Versionen der ODBC-Funktionen werden im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber implementiert. Der Treiber übergibt SQL-Anweisungen an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und gibt die Ergebnisse der Anweisungen an die Anwendung zurück.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber entspricht der Spezifikation für Microsoft Win32 ODBC 3.51. Der Treiber unterstützt Anwendungen, die mit früheren Versionen von ODBC gemäß ODBC 3.51-Spezifikation geschrieben wurden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Datenquellennamen und 64-Bit-Betriebssysteme](../../../relational-databases/native-client/odbc/data-source-names-and-64-bit-operating-systems.md)  
  
-   [Erstellen einer SQL Server Native Client-ODBC-Treiberanwendung](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
-   [Kommunikation mit SQL Server &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [Ausführen von Abfragen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [Verarbeitungsergebnisse &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
-   [Verwenden von Cursorn &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [Ausführen von Transaktionen &#40;ODBC-&#41;](https://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
-   [Behandlung von Fehlern und Meldungen](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [Ausführen gespeicherter Prozeduren](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [Verwenden von Katalogfunktionen](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  
  
-   [Ausführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [Verwalten von Text und Imagespalten](../../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [Leistungsprofilerstellung des ODBC-Treibers](../../../relational-databases/native-client/odbc/profiling-odbc-driver-performance.md)  
  
-   [Tabellenwert Parameter &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [Datums-und Uhrzeit Verbesserungen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [Große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
-   [FILESTREAM-Unterstützung &#40;ODBC-&#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [Dienstprinzipalnamen (SPN) in Clientverbindungen (ODBC)](../../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Unterstützung für sparsespalten &#40;ODBC-&#41;](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)  
  
-   [SQL Server Native Client &#40;ODBC-&#41; Referenz](https://msdn.microsoft.com/library/06b7edee-8636-49d9-9b5c-2c710bf4fa2d)  
  
-   [ODBC How-to Topics](../../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client Programmierung](../../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Installieren von SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  
