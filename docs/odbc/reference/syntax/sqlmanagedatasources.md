---
title: SQLManageDataSources | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLManageDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLManageDataSources
helpviewer_keywords:
- SQLManageDataSources [ODBC]
ms.assetid: ac6d186f-b394-406c-94c4-c6331d1ca468
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 529c503bc10d3ed0b69a4c280c7fa63e72893f8f
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536567"
---
# <a name="sqlmanagedatasources"></a>SQLManageDataSources
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLManageDataSources** zeigt ein Dialogfeld mit dem Benutzer können einrichten, hinzufügen und Löschen von Datenquellen in den Systeminformationen an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLManageDataSources(  
     HWND     hwnd);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwnd*  
 [Eingabe] Handle des übergeordneten Fensters.  
  
## <a name="returns"></a>Rückgabewert  
 **SQLManageDataSources** gibt "false" zurück, wenn *Hwnd* ist es sich nicht um ein gültiges Fensterhandle. Andernfalls wird "true" zurückgegeben.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLManageDataSources** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* Fehler|Der Aufruf von **ConfigDSN** ist fehlgeschlagen.|  
|ODBC_ERROR_INVALID__HWND|Ungültiges Fenster-handle|Die *Hwnd* Argument war ungültig oder NULL.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="managing-data-sources"></a>Verwalten von Datenquellen  
 **SQLManageDataSources** zeigt zu Beginn der **ODBC-Datenquellenadministrator** Dialogfeld wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld für die ODBC-Datenquellenadministrator](../../../odbc/reference/syntax/media/ch23e.gif "CH23E")  
  
 Das Dialogfeld zeigt die Datenquellen aufgeführt, die in den Systeminformationen auf drei Registerkarten: **Benutzer-DSN**, **System-DSN**, und **Datei-DSN**. Wenn der Benutzer eine Datenquelle doppelklickt oder eine Datenquelle klickt und **konfigurieren**, **SQLManageDataSources** Aufrufe **ConfigDSN** im Setup-DLL-Datei mit den ODBC_CONFIG_ DSN-Option.  
  
 Wenn der Benutzer klickt **hinzufügen**, **SQLManageDataSources** zeigt die **neue Datenquelle erstellen** Dialogfeld, in der folgenden Abbildung gezeigt.  
  
 ![Erstellen Sie im Dialogfeld Neue Datenquelle](../../../odbc/reference/syntax/media/ch23f.gif "CH23F")  
  
 Das Dialogfeld zeigt einer Liste der installierten Treiber. Wenn der Benutzer einen Treiber doppelklickt oder ein Treibers klickt und **OK**, **SQLManageDataSources** Aufrufe **ConfigDSN** in der Setup-DLL und übergibt es die ODBC_ADD_DSN-Option.  
  
 Wenn der Benutzer eine Datenquelle wählt, und klickt auf **entfernen**, **SQLManageDataSources** gefragt, ob der Benutzer die Datenquelle löschen möchte. Wenn der Benutzer klickt **Ja**, **SQLManageDataSources** Aufrufe **ConfigDSN** in der Setup-DLL mit der Option ODBC_REMOVE_DSN.  
  
 Die **neue Datenquelle erstellen** Dialogfeld wird zum Hinzufügen oder Löschen einer Datenquelle für den Benutzer, eine Systemdatenquelle oder eine Datei als Datenquelle verwendet.  
  
## <a name="user-dsns"></a>Benutzer-DSNs  
 Werden aufgerufen für einzelne Benutzer erstellten DSNs Benutzer-DSNs, um sie von System-DSNs zu unterscheiden. Benutzer-DSNs werden in den Systeminformationen wie folgt registriert:  
  
 `HKEY_CURRENT_USERS`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbc.ini`  
  
## <a name="system-dsns"></a>System-DSNs  
 Die **neue Datenquelle erstellen** Dialogfeld können Sie eine Systemdatenquelle auf Ihrem lokalen Computer oder löschen Sie einen hinzufügen oder die Konfiguration für eine Systemdatenquelle festzulegen.  
  
 Eine Datenquelle mit einer System-Datenquellennamen (DSN) einrichten kann durch mehrere Benutzer auf dem gleichen Computer verwendet werden. Sie können auch von einem Dienst systemweiten verwendet werden die klicken Sie dann die Datenquelle zugreifen können, auch wenn kein Benutzer mit dem Computer angemeldet ist.  
  
 System-DSN wird in der HKEY_LOCAL_MACHINE-Eintrag in die Systeminformationen und nicht in der HKEY_CURRENT_USER-Eintrag registriert. Es ist nicht an ein Benutzer meldet sich mit seinem bestimmten Benutzernamen und Kennwort kann jedoch verwendet werden von jedem Benutzer des Computers oder von einem Dienst für automatische systemweiten gebunden. System-DSN ist, jedoch an einem Computer gebunden. Die Möglichkeit der Verwendung von remote-DSNs zwischen Computern wird nicht unterstützt. System-DSNs werden in den Systeminformationen wie folgt registriert:  
  
 HKEY_LOCAL_MACHINE    SOFTWARE       ODBC          Odbc.ini  
  
## <a name="file-dsns"></a>Datei-DSNs  
 Eine Datenquelle einen Datenquellennamen ein, keinen ist eine Datenquelle für den Computer, und nicht auf einen Benutzer oder Computer registriert ist. Die Verbindungsinformationen für diese Datenquelle ist in einer DSN-Datei enthalten, die auf einem beliebigen Computer kopiert werden können. Eine Dateidatenquelle möglich freigegeben ist, befindet sich in diesem Fall die DSN-Datei in einem Netzwerk, und gleichzeitig verwendet werden kann von mehreren Benutzern im Netzwerk als der Benutzer den entsprechenden Treiber installiert wurde. Eine Datenquelle kann auch Dateidatenquelle, werden in diesem Fall können sie nur auf einem einzelnen Computer verwendet werden.  
  
 Weitere Informationen zu Datei-Datenquellen, finden Sie unter [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), oder finden Sie unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="managing-drivers"></a>Verwalten von Treibern  
 Klickt der Benutzer die **Treiber** Registerkarte die **ODBC-Datenquellenadministrator** Dialogfeld **SQLManageDataSources** zeigt eine Liste der auf dem System installierten ODBC-Treiber sowie Informationen zu den Treiber. Das Datum angezeigt, ist das Erstellungsdatum des Treibers aus, wie in der folgenden Abbildung dargestellt.  
  
 ![Registerkarte für ODBC-Datenquellenadministrator Treiber](../../../odbc/reference/syntax/media/ch23g.gif "ch23g")  
  
## <a name="tracing-options"></a>Ablaufverfolgungsoptionen  
 Klickt der Benutzer die **Ablaufverfolgung** Registerkarte die **ODBC-Datenquellenadministrator** Dialogfeld **SQLManageDataSources** Ablaufverfolgungsoptionen, zeigt, wie im folgenden Beispiel Abbildung.  
  
 ![ODBC-Datenquellenadministrator Registerkarte](../../../odbc/reference/syntax/media/ch23h.gif "Ch23h")  
  
 Wenn der Benutzer klickt **Ablaufverfolgung jetzt starten** und klickt dann auf **OK**, **SQLManageDataSources** aktiviert die Ablaufverfolgung manuell für alle Anwendungen, die derzeit auf dem Computer ausgeführt.  
  
 Wenn der Benutzer gibt an, den Namen einer Ablaufverfolgungsdatei in die **Protokolldatei Pfad** Textfeld und klickt dann auf **OK**, **SQLManageDataSources** legt die **TraceFile** Schlüsselwort im Abschnitt [ODBC] die Systeminformationen für den angegebenen Namen.  
  
> [!IMPORTANT]  
>  Unterstützung für Visual Studio Analyzer wurde ab Windows 8 (Visual Studio Analyzer wurde nur in früheren Versionen von Visual Studio enthalten.) entfernt. Verwenden Sie eine Alternative zur Problembehandlung Mechanismus BID-Verfolgung.  
  
 Wenn der Benutzer klickt **starten Sie Visual Studio Analyzer** und klickt dann auf **OK**, Visual Studio Analyzer aktiviert ist. Es bleibt aktiviert, bis **beenden Sie Visual Studio Analyzer** geklickt wird.  
  
 Weitere Informationen über die Ablaufverfolgung finden Sie unter [Ablaufverfolgung](../../../odbc/reference/develop-app/tracing.md). Weitere Informationen zu den **Ablaufverfolgung** und **TraceFile** Schlüsselwörtern finden Sie unter [Unterschlüssel für ODBC](../../../odbc/reference/install/odbc-subkey.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Erstellen von Datenquellen|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|
