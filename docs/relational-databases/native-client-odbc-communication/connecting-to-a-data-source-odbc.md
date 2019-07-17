---
title: Herstellen einer Verbindung mit einer Datenquelle (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 092ff6fc878f9a53e6b39e4ca9e4ac1c348ffb83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134190"
---
# <a name="connecting-to-a-data-source-odbc"></a>Herstellen einer Verbindung mit einer Datenquelle (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Nach dem Zuweisen der Umgebungs- und Verbindungshandles und dem Festlegen der Verbindungsattribute stellt die Anwendung eine Verbindung zur Datenquelle oder zum Treiber her. Es gibt drei Funktionen, die Sie verwenden können, um eine Verbindung herzustellen:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 Weitere Informationen zum Herstellen von Verbindungen mit einer Datenquelle, einschließlich der verschiedenen verfügbaren Zeichenfolgenoptionen, finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect** ist die einfachste Verbindungsfunktion. Sie akzeptiert drei Parameter: Datenquellenname, Benutzer-ID und Kennwort. Verwendung **SQLConnect** Wenn diese drei Parameter enthalten alle Informationen, die für die Verbindung mit der Datenbank erforderlich. Zu diesem Zweck erstellen Sie eine Liste mit Datenquellen mithilfe von **SQLDataSources**; der Benutzer für eine Datenquelle, Benutzer-ID und Kennwort aufgefordert, und rufen dann **SQLConnect**.  
  
 **SQLConnect** wird davon ausgegangen, dass eine ODBC-Datenquellenname, Benutzer-ID und Kennwort ausreichend, um die Verbindung mit einer Datenquelle sind und die ODBC-Datenquelle sämtliche anderen Informationen enthält, die ODBC-Treiber benötigt, um die Verbindung herzustellen. Im Gegensatz zu [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) und [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** verwendet eine Verbindungszeichenfolge nicht.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect** wird verwendet, wenn mehr Informationen als die ODBC-Datenquellenname, Benutzer-ID und Kennwort erforderlich ist. Einer der Parameter für **SQLDriverConnect** ist eine Verbindungszeichenfolge, die treiberspezifische Informationen enthält. Sie können **SQLDriverConnect** anstelle von **SQLConnect** aus den folgenden Gründen:  
  
-   Um zum Zeitpunkt des Verbindungsaufbaus treiberspezifische Informationen anzugeben.  
  
-   Um anzugeben, dass der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordert.  
  
-   Um eine Verbindung herzustellen, ohne eine ODBC-Datenquelle zu verwenden.  
  
 Die **SQLDriverConnect** Verbindungszeichenfolge enthält eine Reihe von Schlüsselwort-Wert-Paaren, die alle von einem ODBC-Treiber unterstützten Verbindungsinformationen angeben. Bei allen vom Treiber unterstützten Verbindungsinformationen unterstützt jeder Treiber über die treiberspezifischen Schlüsselwörter hinaus die standardmäßigen ODBC-Schlüsselwörter (DSN, FILEDSN, DRIVER, UID, PWD und SAVEFILE). **SQLDriverConnect** herstellen, ohne dass eine Datenquelle verwendet werden können. Z. B. eine Anwendung, die mit der eine "DSN-lose" Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Aufrufen **SQLDriverConnect** mit einer Verbindungszeichenfolge, die definiert, die Anmelde-ID, Kennwort, Netzwerkbibliothek, Servernamen, um Herstellen einer Verbindung mit und die Standarddatenbank verwendet.  
  
 Bei Verwendung **SQLDriverConnect**, es gibt zwei Optionen für den Benutzer für die benötigten Verbindungsinformationen aufzufordern:  
  
-   Dialogfeld "Anwendung"  
  
     Sie können eine Anwendung Dialogfeld "erstellen", die Verbindungsinformationen aufgefordert, und ruft dann **SQLDriverConnect** mit einem Fensterhandle von NULL und *DriverCompletion* auf SQL_DRIVER_NOPROMPT festgelegt. Diese Parametereinstellungen verhindern, dass der ODBC-Treiber ein eigenes Dialogfeld öffnet. Diese Methode wird verwendet, wenn die Benutzeroberfläche der Anwendung gesteuert werden muss.  
  
-   Dialogfeld "Filter"  
  
     Sie können die Anwendung, übergeben ein gültiges Fensterhandle an codieren **SQLDriverConnect** und legen Sie die *DriverCompletion* -Parameter auf SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT oder SQL_DRIVER_COMPLETE_ Erforderlich. Der Treiber generiert dann ein Dialogfeld, um den Benutzer zur Eingabe von Verbindungsinformationen aufzufordern. Diese Methode vereinfacht den Anwendungscode.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**, z. B. **SQLDriverConnect**, verwendet eine Verbindungszeichenfolge. Indem jedoch **SQLBrowseConnect**, eine Anwendung kann eine vollständige Verbindungszeichenfolge iterativ mit der Datenquelle zur Laufzeit erstellen. Dadurch kann die Anwendung zwei Funktionen erfüllen:  
  
-   Erstellen eigener Dialogfelder, um zur Eingabe dieser Informationen aufzufordern, wodurch die Kontrolle über die Benutzeroberfläche beibehalten wird.  
  
-   Durchsuchen des Systems nach Datenquellen, die von einem bestimmten Treiber verwendet werden können. Dies sollte nach Möglichkeit in mehreren Schritten erfolgen.  
  
     Beispielsweise kann der Benutzer zunächst das Netzwerk nach Servern durchsuchen und, sobald er einen Server ausgewählt hat, diesen nach Datenbanken durchsuchen, auf die der Treiber zugreifen kann.  
  
 Wenn **SQLBrowseConnect** Abschluss eine erfolgreiche Verbindung wird eine Verbindungszeichenfolge, die bei nachfolgenden Aufrufen verwendet werden kann **SQLDriverConnect**.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber stets SQL_SUCCESS_WITH_INFO zurückgegeben. bei einem erfolgreichen **SQLConnect**, **SQLDriverConnect**, oder **SQLBrowseConnect**. Wenn eine ODBC-Anwendung aufruft **SQLGetDiagRec** nach dem Erhalt von SQL_SUCCESS_WITH_INFO den erhalten sie der folgenden Meldungen:  
  
 5701  
 Gibt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Kontext des Benutzers in die in der Datenquelle angegebene Standarddatenbank oder, wenn für die Datenquelle keine Standarddatenbank angegeben ist, in die Standarddatenbank der zur Verbindung verwendeten Anmelde-ID einfügt.  
  
 5703  
 Gibt die auf dem Server verwendete Sprache an.  
  
 Bei einer erfolgreichen Verbindung wird die folgende Meldung vom Systemadministrator zurückgegeben:  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 Sie können die Meldungen 5701 und 5703 ignorieren; sie dienen nur zu Informationszwecken. Den Rückgabecode SQL_SUCCESS_WITH_INFO hingegen sollten Sie nicht ignorieren, da auch andere Meldungen als 5701 oder 5703 zurückgegeben werden können. Angenommen, ein Treiber eine Verbindung mit einem Server mit einer Instanz von herstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit veralteten gespeicherten Prozeduren für Kataloginformationen, einer der Fehler durch zurückgegebene **SQLGetDiagRec** nach erfolgreichem SQL_SUCCESS_WITH_INFO ist:  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 Die Fehlerbehandlungsfunktion einer Anwendung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungen sollten Aufrufen **SQLGetDiagRec** bis SQL_NO_DATA zurückgegeben. Anschließend sollte die Funktion auf alle Meldungen mit einem *PfNative* -Code 5701 oder 5703.  
  
## <a name="see-also"></a>Siehe auch  
 [Kommunikation mit SQLServer &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
