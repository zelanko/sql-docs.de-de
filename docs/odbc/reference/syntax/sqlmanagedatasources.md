---
title: Sqlmanagedatasources | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b572a861af3479e1543be9fda9598cc7e25d36c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290218"
---
# <a name="sqlmanagedatasources"></a>SQLManageDataSources
**Konformitäts**  
 Eingeführte Version: ODBC 2,0  
  
 **Zusammenfassung**  
 **Sqlmanagedatasources** zeigt ein Dialogfeld an, in dem Benutzerdaten Quellen in den Systeminformationen einrichten, hinzufügen und löschen können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLManageDataSources(  
     HWND     hwnd);  
```  
  
## <a name="arguments"></a>Argumente  
 *HWND*  
 Der Handle des übergeordneten Fensters.  
  
## <a name="returns"></a>Rückgabe  
 **Sqlmanagedatasources** gibt false zurück, wenn *HWND* kein gültiges Fenster Handle ist. Andernfalls wird TRUE zurückgegeben.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlmanagedatasources** false zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Fehler beim **ConfigDSN** -Rückruf.|  
|ODBC_ERROR_INVALID__HWND|Ungültiges Fenster handle.|Das *HWND* -Argument war ungültig oder NULL.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="managing-data-sources"></a>Verwalten von Datenquellen  
 **Sqlmanagedatasources** zeigt zunächst das Dialogfeld **ODBC-Datenquellen-Administrator** an, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "ODBC-Datenquellen-Administrator"](../../../odbc/reference/syntax/media/ch23e.gif "CH23E")  
  
 Im Dialogfeld werden die Datenquellen angezeigt, die in den Systeminformationen unter drei Registerkarten aufgeführt sind: **Benutzer-DSN**, **System-DSN**und **Datei-DSN**. Wenn der Benutzer auf eine Datenquelle doppelklickt oder eine Datenquelle auswählt und auf **Konfigurieren**klickt, ruft **sqlmanagedatasources** **ConfigDSN** in der Setup-DLL mit der ODBC_CONFIG_DSN-Option auf.  
  
 Wenn der Benutzer auf **Hinzufügen**klickt, zeigt **sqlmanagedatasources** das Dialogfeld **neue Datenquelle erstellen** an, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "Neue Datenquelle erstellen"](../../../odbc/reference/syntax/media/ch23f.gif "CH23F")  
  
 Im Dialogfeld wird eine Liste der installierten Treiber angezeigt. Wenn der Benutzer auf einen Treiber doppelklickt oder einen Treiber auswählt und auf **OK**klickt, ruft **sqlmanagedatasources** **ConfigDSN** in der Setup-DLL auf und übergibt ihm die Option ODBC_ADD_DSN.  
  
 Wenn der Benutzer eine Datenquelle auswählt und auf **Entfernen**klickt, fragt **sqlmanagedatasources** , ob der Benutzer die Datenquelle löschen möchte. Wenn der Benutzer auf **Ja**klickt, ruft **sqlmanagedatasources** **ConfigDSN** in der Setup-DLL mit der ODBC_REMOVE_DSN-Option auf.  
  
 Das Dialogfeld **neue Datenquelle erstellen** wird verwendet, um eine Benutzerdaten Quelle, eine Systemdaten Quelle oder eine Datei Datenquelle hinzuzufügen oder zu löschen.  
  
## <a name="user-dsns"></a>Benutzer-DSNs  
 DSNs, die für einzelne Benutzer erstellt werden, werden als Benutzer-DSNs bezeichnet, um Sie von System-DSNs zu unterscheiden. Benutzer-DSNs werden in den Systeminformationen wie folgt registriert:  
  
 `HKEY_CURRENT_USERS`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbc.ini`  
  
## <a name="system-dsns"></a>System-DSNs  
 Im Dialogfeld **neue Datenquelle erstellen** können Sie dem lokalen Computer eine Systemdaten Quelle hinzufügen oder eine Systemdaten Quelle löschen oder die Konfiguration für eine Systemdaten Quelle festlegen.  
  
 Eine mit einem System-Datenquellen Namen (DSN) aufgelegte Datenquelle kann von mehreren Benutzern auf demselben Computer verwendet werden. Sie kann auch von einem systemweiten Dienst verwendet werden, der Zugriff auf die Datenquelle erhält, auch wenn kein Benutzer am Computer angemeldet ist.  
  
 Ein System-DSN wird im HKEY_LOCAL_MACHINE Eintrag in den Systeminformationen anstelle des HKEY_CURRENT_USER Eintrags registriert. Er ist nicht an einen Benutzer gebunden, der sich mit seinem bestimmten Benutzernamen und Kennwort anmeldet, aber von jedem Benutzer dieses Computers oder durch einen automatischen systemweiten Dienst verwendet werden kann. Der System-DSN ist jedoch an einen Computer gebunden. Die Verwendung von Remote-DSNs zwischen Computern wird nicht unterstützt. System-DSNs werden in den Systeminformationen wie folgt registriert:  
  
 HKEY_LOCAL_MACHINE Software ODBC ODBC. ini  
  
## <a name="file-dsns"></a>Datei-DSNs  
 Eine Datei Datenquelle hat keinen Datenquellen Namen, wie eine Computer Datenquelle, und ist nicht für einen Benutzer oder Computer registriert. Die Verbindungsinformationen für diese Datenquelle sind in einer DSN-Datei enthalten, die auf einen beliebigen Computer kopiert werden kann. Eine Datei Datenquelle kann Share fähig sein. in diesem Fall befindet sich die DSN-Datei in einem Netzwerk und kann gleichzeitig von mehreren Benutzern im Netzwerk verwendet werden, solange der Benutzer den entsprechenden Treiber installiert hat. Eine Datei Datenquelle kann auch unshare fähig sein. in diesem Fall kann Sie nur auf einem einzelnen Computer verwendet werden.  
  
 Weitere Informationen zu Datei Datenquellen finden Sie unter [Herstellen einer Verbindung mithilfe von Datei Datenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)oder unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="managing-drivers"></a>Verwalten von Treibern  
 Wenn der Benutzer im Dialogfeld **ODBC-Datenquellen-Administrator** auf die Registerkarte **Treiber** klickt, zeigt **sqlmanagedatasources** eine Liste der auf dem System installierten ODBC-Treiber sowie Informationen zu den Treibern an. Das angezeigte Datum ist das Erstellungsdatum des Treibers, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "ODBC-Datenquellen-Administrator", Registerkarte "Treiber"](../../../odbc/reference/syntax/media/ch23g.gif "ch23g")  
  
## <a name="tracing-options"></a>Ablaufverfolgungsoptionen  
 Wenn der Benutzer im Dialogfeld **ODBC-Datenquellen-Administrator** auf die Registerkarte Ablauf **Verfolgung** klickt, zeigt **sqlmanagedatasources** Ablauf Verfolgungs Optionen an, wie in der folgenden Abbildung dargestellt.  
  
 ![Registerkarte "Nachverfolgung des ODBC-Datenquellen-Administrators"](../../../odbc/reference/syntax/media/ch23h.gif "Ch23h")  
  
 Wenn der Benutzer jetzt auf Ablauf **Verfolgung starten** klickt und dann auf **OK**klickt, ermöglicht **sqlmanagedatasources** die manuelle Ablauf Verfolgung für alle Anwendungen, die aktuell auf dem Computer ausgeführt werden.  
  
 Wenn der Benutzer den Namen einer Ablauf Verfolgungs Datei im Textfeld **Protokolldatei Pfad** angibt und dann auf **OK**klickt, legt **sqlmanagedatasources** das **Tracefile** -Schlüsselwort im [ODBC]-Abschnitt der Systeminformationen auf den angegebenen Namen fest.  
  
> [!IMPORTANT]  
>  Die Unterstützung für Visual Studio Analyzer wurde ab Windows 8 entfernt (Visual Studio Analyzer war nur in früheren Versionen von Visual Studio enthalten.) Verwenden Sie für einen alternativen Mechanismus zur Problembehandlung die Auftrags Ablauf Verfolgung.  
  
 Wenn der Benutzer auf **Start Visual Studio Analyzer** und dann auf **OK**klickt, ist Visual Studio Analyzer aktiviert. Sie bleibt aktiviert, bis die Option zum **Abbrechen Visual Studio Analyzer** geklickt wird.  
  
 Weitere Informationen zur Ablauf Verfolgung finden Sie unter Ablauf [Verfolgung](../../../odbc/reference/develop-app/tracing.md). Weitere Informationen zu den Schlüsselwörtern **Trace** und **Tracefile** finden Sie unter [ODBC-Unterschlüssel](../../../odbc/reference/install/odbc-subkey.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Erstellen von Datenquellen|[Sqlkreatedatasource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|
