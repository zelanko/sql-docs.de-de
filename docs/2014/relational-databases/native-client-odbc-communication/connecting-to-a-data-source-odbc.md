---
title: Herstellen einer Verbindung mit einer Datenquelle (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: e0192e3b4bf295ad0590b26a6f3e77d94d76acd9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63075182"
---
# <a name="connecting-to-a-data-source-odbc"></a>Herstellen einer Verbindung mit einer Datenquelle (ODBC)
  Nach dem Zuweisen der Umgebungs- und Verbindungshandles und dem Festlegen der Verbindungsattribute stellt die Anwendung eine Verbindung zur Datenquelle oder zum Treiber her. Es gibt drei Funktionen, die Sie verwenden können, um eine Verbindung herzustellen:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 Weitere Informationen zum Herstellen von Verbindungen mit einer Datenquelle, einschließlich der verschiedenen Optionen für Verbindungs Zeichenfolgen, finden [Sie unter Verwenden von Verbindungs Zeichenfolgen-Schlüsselwörtern mit SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLCONNECT** ist die einfachste Verbindungsfunktion. Sie akzeptiert drei Parameter: Datenquellenname, Benutzer-ID und Kennwort. Verwenden Sie **SQLCONNECT** , wenn diese drei Parameter alle Informationen enthalten, die zum Herstellen einer Verbindung mit der Datenbank erforderlich sind. Erstellen Sie dazu eine Liste mit Datenquellen mithilfe von **SQLDataSources**. Benutzer zur Eingabe einer Datenquelle, Benutzer-ID und eines Kennworts auffordern und dann **SQLCONNECT**aufzurufen.  
  
 **SQLCONNECT** geht davon aus, dass ein Datenquellen Name, eine Benutzer-ID und ein Kennwort zum Herstellen einer Verbindung mit einer Datenquelle ausreichen und dass die ODBC-Datenquelle alle anderen Informationen enthält, die der ODBC-Treiber zum Herstellen der Verbindung benötigt. Im Gegensatz zu [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) und [sqlbrowseconnetct](../native-client-odbc-api/sqlbrowseconnect.md)verwendet **SQLCONNECT** keine Verbindungs Zeichenfolge.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect** wird verwendet, wenn mehr Informationen als Name der Datenquelle, Benutzer-ID und Kennwort erforderlich sind. Einer der Parameter für **SQLDriverConnect** ist eine Verbindungs Zeichenfolge, die Treiber spezifische Informationen enthält. Sie können **SQLDriverConnect** anstelle von **SQLCONNECT** aus den folgenden Gründen verwenden:  
  
-   Um zum Zeitpunkt des Verbindungsaufbaus treiberspezifische Informationen anzugeben.  
  
-   Um anzugeben, dass der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordert.  
  
-   Um eine Verbindung herzustellen, ohne eine ODBC-Datenquelle zu verwenden.  
  
 Die **SQLDriverConnect** -Verbindungs Zeichenfolge enthält eine Reihe von Schlüsselwort-Wert-Paaren, mit denen alle von einem ODBC-Treiber unterstützten Verbindungsinformationen angegeben werden. Bei allen vom Treiber unterstützten Verbindungsinformationen unterstützt jeder Treiber über die treiberspezifischen Schlüsselwörter hinaus die standardmäßigen ODBC-Schlüsselwörter (DSN, FILEDSN, DRIVER, UID, PWD und SAVEFILE). **SQLDriverConnect** kann verwendet werden, um eine Verbindung ohne Datenquelle herzustellen. Beispielsweise kann eine Anwendung, die so konzipiert ist, dass Sie eine DSN-lose Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von herstellt, **SQLDriverConnect** mit einer Verbindungs Zeichenfolge aufruft, die die Anmelde-ID, das Kennwort, die Netzwerk Bibliothek, den Servernamen für die Verbindung und die zu verwendende Standarddatenbank definiert.  
  
 Bei der Verwendung von **SQLDriverConnect**stehen zwei Optionen zur Verfügung, um den Benutzer zur Eingabe von erforderlichen Verbindungsinformationen aufzufordern:  
  
-   Dialogfeld "Anwendung"  
  
     Sie können ein Anwendungs Dialogfeld erstellen, in dem Sie zur Eingabe von Verbindungsinformationen aufgefordert werden, und dann **SQLDriverConnect** mit einem NULL-Fenster Handle und *DriverCompletion* auf SQL_DRIVER_NOPROMPT festlegen. Diese Parametereinstellungen verhindern, dass der ODBC-Treiber ein eigenes Dialogfeld öffnet. Diese Methode wird verwendet, wenn die Benutzeroberfläche der Anwendung gesteuert werden muss.  
  
-   Dialogfeld "Filter"  
  
     Sie können die Anwendung so codieren, dass Sie ein gültiges Fenster Handle an **SQLDriverConnect** übergibt, und den *DriverCompletion* -Parameter auf SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT oder SQL_DRIVER_COMPLETE_REQUIRED festlegen. Der Treiber generiert dann ein Dialogfeld, um den Benutzer zur Eingabe von Verbindungsinformationen aufzufordern. Diese Methode vereinfacht den Anwendungscode.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **Sqlbrowseconnetct**verwendet, wie **SQLDriverConnect**, eine Verbindungs Zeichenfolge. Mithilfe von **sqlbrowseconnetct**kann eine Anwendung jedoch zur Laufzeit eine vollständige Verbindungs Zeichenfolge iterativ mit der Datenquelle erstellen. Dadurch kann die Anwendung zwei Funktionen erfüllen:  
  
-   Erstellen eigener Dialogfelder, um zur Eingabe dieser Informationen aufzufordern, wodurch die Kontrolle über die Benutzeroberfläche beibehalten wird.  
  
-   Durchsuchen des Systems nach Datenquellen, die von einem bestimmten Treiber verwendet werden können. Dies sollte nach Möglichkeit in mehreren Schritten erfolgen.  
  
     Beispielsweise kann der Benutzer zunächst das Netzwerk nach Servern durchsuchen und, sobald er einen Server ausgewählt hat, diesen nach Datenbanken durchsuchen, auf die der Treiber zugreifen kann.  
  
 Wenn **sqlbrowseconnetct** eine erfolgreiche Verbindung abschließt, wird eine Verbindungs Zeichenfolge zurückgegeben, die bei nachfolgenden Aufrufen von **SQLDriverConnect**verwendet werden kann.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber gibt bei erfolgreicher Ausführung von **SQLCONNECT**, **SQLDriverConnect**oder **sqlbrowseconnct**immer SQL_SUCCESS_WITH_INFO zurück. Wenn eine ODBC-Anwendung nach dem Abrufen von SQL_SUCCESS_WITH_INFO **SQLGetDiagRec** aufruft, kann Sie folgende Meldungen erhalten:  
  
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
  
 Sie können die Meldungen 5701 und 5703 ignorieren; sie dienen nur zu Informationszwecken. Den Rückgabecode SQL_SUCCESS_WITH_INFO hingegen sollten Sie nicht ignorieren, da auch andere Meldungen als 5701 oder 5703 zurückgegeben werden können. Wenn ein Treiber z. b. eine Verbindung mit einem Server herstellt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem eine Instanz von mit veralteten gespeicherten Katalog Prozeduren ausgeführt wird, ist einer der Fehler, der durch **SQLGetDiagRec** nach einer SQL_SUCCESS_WITH_INFO zurückgegeben wird,  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 Die Fehler Behandlungs Funktion einer Anwendung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungen sollte **SQLGetDiagRec** aufrufen, bis SQL_NO_DATA zurückgegeben wird. Anschließend sollte Sie auf alle Nachrichten reagieren, die nicht mit einem *pfNative* -Code von 5701 oder 5703 zu tun haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kommunikation mit SQL Server &#40;ODBC-&#41;](communicating-with-sql-server-odbc.md)  
  
  
