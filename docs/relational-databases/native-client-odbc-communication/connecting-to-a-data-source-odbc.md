---
title: Herstellen einer Verbindung mit einer Datenquelle (ODBC) | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ae59e0bdb005d296341970f4582100b15a0dfdf7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307711"
---
# <a name="connecting-to-a-data-source-odbc"></a>Herstellen einer Verbindung mit einer Datenquelle (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Nach dem Zuweisen der Umgebungs- und Verbindungshandles und dem Festlegen der Verbindungsattribute stellt die Anwendung eine Verbindung zur Datenquelle oder zum Treiber her. Es gibt drei Funktionen, die Sie verwenden können, um eine Verbindung herzustellen:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 Weitere Informationen zum Herstellen von Verbindungen mit einer Datenquelle, einschließlich der verschiedenen verfügbaren Verbindungszeichenfolgenoptionen, finden Sie unter [Verwenden von Verbindungszeichenfolgenschlüsselwörtern mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect** ist die einfachste Verbindungsfunktion. Sie akzeptiert drei Parameter: Datenquellenname, Benutzer-ID und Kennwort. Verwenden Sie **SQLConnect,** wenn diese drei Parameter alle Informationen enthalten, die zum Herstellen einer Verbindung mit der Datenbank erforderlich sind. Erstellen Sie dazu eine Liste von Datenquellen mit **SQLDataSources**; den Benutzer zur Eingabe einer Datenquelle, einer Benutzer-ID und eines Kennworts aufzufordern; und rufen Sie dann **SQLConnect auf.**  
  
 **SQLConnect** geht davon aus, dass ein Datenquellenname, eine Benutzer-ID und ein Kennwort ausreichen, um eine Verbindung mit einer Datenquelle herzustellen, und dass die ODBC-Datenquelle alle anderen Informationen enthält, die der ODBC-Treiber zum Herstellen der Verbindung benötigt. Im Gegensatz zu [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) und [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)verwendet **SQLConnect** keine Verbindungszeichenfolge.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect** wird verwendet, wenn mehr Informationen als der Datenquellenname, die Benutzer-ID und das Kennwort erforderlich sind. Einer der Parameter für **SQLDriverConnect** ist eine Verbindungszeichenfolge, die treiberspezifische Informationen enthält. Aus den folgenden Gründen können Sie **SQLDriverConnect** anstelle von **SQLConnect** verwenden:  
  
-   Um zum Zeitpunkt des Verbindungsaufbaus treiberspezifische Informationen anzugeben.  
  
-   Um anzugeben, dass der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordert.  
  
-   Um eine Verbindung herzustellen, ohne eine ODBC-Datenquelle zu verwenden.  
  
 Die **SQLDriverConnect-Verbindungszeichenfolge** enthält eine Reihe von Schlüsselwort-Wert-Paaren, die alle Verbindungsinformationen angeben, die von einem ODBC-Treiber unterstützt werden. Bei allen vom Treiber unterstützten Verbindungsinformationen unterstützt jeder Treiber über die treiberspezifischen Schlüsselwörter hinaus die standardmäßigen ODBC-Schlüsselwörter (DSN, FILEDSN, DRIVER, UID, PWD und SAVEFILE). **SQLDriverConnect** kann verwendet werden, um eine Verbindung ohne Datenquelle herzustellen. Beispielsweise kann eine Anwendung, die eine "DSN-less"-Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu einer Instanz von herstellen soll, **SQLDriverConnect** mit einer Verbindungszeichenfolge aufrufen, die die Anmelde-ID, das Kennwort, die Netzwerkbibliothek, den Servernamen, mit dem eine Verbindung hergestellt werden soll, und die zu verwendende Standarddatenbank definiert.  
  
 Bei verwendung von **SQLDriverConnect**gibt es zwei Optionen, um den Benutzer zur Eingabe aller erforderlichen Verbindungsinformationen aufzufragen:  
  
-   Dialogfeld "Anwendung"  
  
     Sie können ein Anwendungsdialogfeld erstellen, das zur Eingabe von Verbindungsinformationen auffordert, und dann **SQLDriverConnect** mit einem NULL-Fensterhandle aufrufen und *DriverCompletion* auf SQL_DRIVER_NOPROMPT festgelegt. Diese Parametereinstellungen verhindern, dass der ODBC-Treiber ein eigenes Dialogfeld öffnet. Diese Methode wird verwendet, wenn die Benutzeroberfläche der Anwendung gesteuert werden muss.  
  
-   Dialogfeld "Filter"  
  
     Sie können die Anwendung codieren, um ein gültiges Fensterhandle an **SQLDriverConnect** zu übergeben, und den *Parameter DriverCompletion* auf SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT oder SQL_DRIVER_COMPLETE_REQUIRED festlegen. Der Treiber generiert dann ein Dialogfeld, um den Benutzer zur Eingabe von Verbindungsinformationen aufzufordern. Diese Methode vereinfacht den Anwendungscode.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**verwendet, z. B. **SQLDriverConnect**, eine Verbindungszeichenfolge. Mit **SQLBrowseConnect**kann eine Anwendung jedoch eine vollständige Verbindungszeichenfolge iterativ mit der Datenquelle zur Laufzeit erstellen. Dadurch kann die Anwendung zwei Funktionen erfüllen:  
  
-   Erstellen eigener Dialogfelder, um zur Eingabe dieser Informationen aufzufordern, wodurch die Kontrolle über die Benutzeroberfläche beibehalten wird.  
  
-   Durchsuchen des Systems nach Datenquellen, die von einem bestimmten Treiber verwendet werden können. Dies sollte nach Möglichkeit in mehreren Schritten erfolgen.  
  
     Beispielsweise kann der Benutzer zunächst das Netzwerk nach Servern durchsuchen und, sobald er einen Server ausgewählt hat, diesen nach Datenbanken durchsuchen, auf die der Treiber zugreifen kann.  
  
 Wenn **SQLBrowseConnect** eine erfolgreiche Verbindung abschließt, wird eine Verbindungszeichenfolge zurückgegeben, die bei nachfolgenden Aufrufen von **SQLDriverConnect**verwendet werden kann.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client ODBC-Treiber gibt immer SQL_SUCCESS_WITH_INFO für eine erfolgreiche **SQLConnect**, **SQLDriverConnect**oder **SQLBrowseConnect**zurück. Wenn eine ODBC-Anwendung **SQLGetDiagRec** aufruft, nachdem sie SQL_SUCCESS_WITH_INFO erhalten hat, kann sie die folgenden Meldungen empfangen:  
  
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
  
 Sie können die Meldungen 5701 und 5703 ignorieren; sie dienen nur zu Informationszwecken. Den Rückgabecode SQL_SUCCESS_WITH_INFO hingegen sollten Sie nicht ignorieren, da auch andere Meldungen als 5701 oder 5703 zurückgegeben werden können. Wenn ein Treiber z. B. eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung zu einem Server herstellt, auf dem eine Instanz mit veralteten gespeicherten Katalogprozeduren ausgeführt wird, lautet einer der Fehler, die nach einer SQL_SUCCESS_WITH_INFO über **SQLGetDiagRec** zurückgegeben werden:  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 Die Fehlerbehandlungsfunktion einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anwendung für Verbindungen sollte **SQLGetDiagRec** aufrufen, bis sie SQL_NO_DATA zurückgibt. Es sollte dann auf andere Nachrichten als die mit einem *pfNative-Code* von 5701 oder 5703 reagieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kommunikation mit SQL Server &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
