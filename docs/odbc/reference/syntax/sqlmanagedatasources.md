---
title: SQLManageDataSources | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290218"
---
# <a name="sqlmanagedatasources"></a>SQLManageDataSources
**Konformität**  
 Eingeführte Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLManageDataSources** zeigt ein Dialogfeld an, mit dem Benutzer Datenquellen in den Systeminformationen einrichten, hinzufügen und löschen können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLManageDataSources(  
     HWND     hwnd);  
```  
  
## <a name="arguments"></a>Argumente  
 *Hwnd*  
 [Eingabe] Übergeordnetes Fensterhandle.  
  
## <a name="returns"></a>Rückgabe  
 **SQLManageDataSources** gibt FALSE zurück, wenn *hwnd* kein gültiges Fensterhandle ist. Andernfalls wird TRUE zurückgegeben.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLManageDataSources** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Der Aufruf von **ConfigDSN** ist fehlgeschlagen.|  
|ODBC_ERROR_INVALID__HWND|Ungültiges Fensterhandle|Das *hwnd-Argument* war ungültig oder NULL.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="managing-data-sources"></a>Verwalten von Datenquellen  
 **SQLManageDataSources** zeigt zunächst das Dialogfeld **ODBC Data Source Administrator** an, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "ODBC-Datenquellen-Administrator"](../../../odbc/reference/syntax/media/ch23e.gif "CH23E")  
  
 Das Dialogfeld zeigt die in den Systeminformationen aufgelisteten Datenquellen unter drei Registerkarten **an: Benutzer-DSN**, **System-DSN**und **Datei-DSN**. Wenn der Benutzer auf eine Datenquelle doppelklickt oder eine Datenquelle auswählt und auf **Konfigurieren**klickt, ruft **SQLManageDataSources** **ConfigDSN** in der Setup-DLL mit der Option ODBC_CONFIG_DSN auf.  
  
 Wenn der Benutzer auf **Hinzufügen**klickt, zeigt **SQLManageDataSources** das Dialogfeld **Neue Datenquelle erstellen** an, das in der folgenden Abbildung angezeigt wird.  
  
 ![Dialogfeld "Neue Datenquelle erstellen"](../../../odbc/reference/syntax/media/ch23f.gif "CH23F")  
  
 Im Dialogfeld wird eine Liste der installierten Treiber angezeigt. Wenn der Benutzer auf einen Treiber doppelklickt oder einen Treiber auswählt und auf **OK**klickt, ruft **SQLManageDataSources** **ConfigDSN** in der Setup-DLL auf und übergibt ihm die Option ODBC_ADD_DSN.  
  
 Wenn der Benutzer eine Datenquelle auswählt und auf **Entfernen**klickt, fragt **SQLManageDataSources,** ob der Benutzer die Datenquelle löschen möchte. Wenn der Benutzer auf **Ja**klickt, ruft **SQLManageDataSources** **ConfigDSN** in der Setup-DLL mit der Option ODBC_REMOVE_DSN auf.  
  
 Das Dialogfeld **Neue Datenquelle erstellen** wird verwendet, um eine Benutzerdatenquelle, eine Systemdatenquelle oder eine Dateidatenquelle hinzuzufügen oder zu löschen.  
  
## <a name="user-dsns"></a>Benutzer-DSNs  
 DSNs, die für einzelne Benutzer erstellt wurden, werden Benutzer-DSNs genannt, um sie von System-DSNs zu unterscheiden. Benutzer-DSNs werden in den Systeminformationen wie folgt registriert:  
  
 `HKEY_CURRENT_USERS`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbc.ini`  
  
## <a name="system-dsns"></a>System-DSNs  
 Im Dialogfeld **Neue Datenquelle** erstellen können Sie dem lokalen Computer eine Systemdatenquelle hinzufügen oder eine löschen oder die Konfiguration für eine Systemdatenquelle festlegen.  
  
 Eine Datenquelle, die mit einem Systemdatenquellennamen (DSN) eingerichtet wurde, kann von mehr als einem Benutzer auf demselben Computer verwendet werden. Es kann auch von einem systemweiten Dienst verwendet werden, der dann Zugriff auf die Datenquelle erhalten kann, auch wenn kein Benutzer am Computer angemeldet ist.  
  
 Ein System-DSN wird im HKEY_LOCAL_MACHINE Eintrag in den Systeminformationen und nicht im HKEY_CURRENT_USER Eintrag registriert. Sie ist nicht an einen Benutzer gebunden, der sich mit seinem benutzerdefinierten Benutzernamen und Kennwort anmeldet, sondern kann von jedem Benutzer dieses Computers oder von einem automatischen systemweiten Dienst verwendet werden. Das System DSN ist jedoch an eine Maschine gebunden. Es unterstützt nicht die Möglichkeit, Remote-DSNs zwischen Computern zu verwenden. System-DSNs werden in den Systeminformationen wie folgt registriert:  
  
 HKEY_LOCAL_MACHINE SOFTWARE ODBC Odbc.ini  
  
## <a name="file-dsns"></a>Datei-DSNs  
 Eine Dateidatenquelle hat keinen Datenquellennamen, ebenso wie eine Computerdatenquelle, und ist nicht für einen Benutzer oder Computer registriert. Die Verbindungsinformationen für diese Datenquelle sind in einer DSN-Datei enthalten, die auf jeden Computer kopiert werden kann. Eine Dateidatenquelle kann gemeinsam genutzt werden, in diesem Fall befindet sich die DsN-Datei in einem Netzwerk und kann gleichzeitig von mehreren Benutzern im Netzwerk verwendet werden, solange der Benutzer den entsprechenden Treiber installiert hat. Eine Dateidatenquelle kann auch nicht mehr gemeinsam genutzt werden können, in diesem Fall kann sie nur auf einem einzelnen Computer verwendet werden.  
  
 Weitere Informationen zu Dateidatenquellen finden Sie unter [Verbinden mit Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)oder [sqlDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="managing-drivers"></a>Verwalten von Treibern  
 Wenn der Benutzer im Dialogfeld **ODBC Data Source Administrator** auf die Registerkarte **Treiber** klickt, zeigt **SQLManageDataSources** eine Liste der auf dem System installierten ODBC-Treiber sowie Informationen zu den Treibern an. Das angezeigte Datum ist das Erstellungsdatum des Treibers, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "ODBC-Datenquellen-Administrator", Registerkarte "Treiber"](../../../odbc/reference/syntax/media/ch23g.gif "ch23g")  
  
## <a name="tracing-options"></a>Ablaufverfolgungsoptionen  
 Wenn der Benutzer im Dialogfeld **ODBC-Datenquellenadministrator** auf die Registerkarte **Ablaufverfolgung** klickt, werden **in SQLManageDataSources** Ablaufverfolgungsoptionen angezeigt, wie in der folgenden Abbildung dargestellt.  
  
 ![Registerkarte "Nachverfolgung des ODBC-Datenquellen-Administrators"](../../../odbc/reference/syntax/media/ch23h.gif "Ch23h")  
  
 Wenn der Benutzer auf **Jetzt** starten und dann auf **OK**klickt, aktiviert **SQLManageDataSources** die manuelle Ablaufverfolgung für alle Anwendungen, die derzeit auf dem Computer ausgeführt werden.  
  
 Wenn der Benutzer den Namen einer Ablaufverfolgungsdatei im Textfeld **Protokolldatei Pfad** angibt und dann auf **OK**klickt, legt **SQLManageDataSources** das **TraceFile-Schlüsselwort** im Abschnitt [ODBC] der Systeminformationen auf den angegebenen Namen fest.  
  
> [!IMPORTANT]  
>  Die Unterstützung für Visual Studio Analyzer wurde ab Windows 8 entfernt (Visual Studio Analyzer war nur in älteren Versionen von Visual Studio enthalten). Verwenden Sie für einen alternativen Fehlerbehebungsmechanismus die BID-Ablaufverfolgung.  
  
 Wenn der Benutzer auf **Visual Studio Analyzer starten** und dann auf **OK**klickt, ist Visual Studio Analyzer aktiviert. Sie bleibt aktiviert, bis auf **Visual Studio Analyzer** beenden geklickt wird.  
  
 Weitere Informationen zur Ablaufverfolgung finden Sie unter [Ablaufverfolgung](../../../odbc/reference/develop-app/tracing.md). Weitere Informationen zu den Schlüsselwörtern **Trace** und **TraceFile** finden Sie unter [ODBC Subkey](../../../odbc/reference/install/odbc-subkey.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Erstellen von Datenquellen|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|
