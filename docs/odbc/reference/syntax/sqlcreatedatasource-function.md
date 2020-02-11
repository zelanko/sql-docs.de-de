---
title: Sqlkreatedatasource-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCreateDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCreateDataSource
helpviewer_keywords:
- SQLCreateDataSource function [ODBC]
ms.assetid: 76ee851a-dca9-40cc-8e9e-eb3f74e560ee
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0b3a6fced096c779b5ab91bf4e5b6a3f0a66e5f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68121386"
---
# <a name="sqlcreatedatasource-function"></a>SQLCreateDataSource-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,0  
  
 **Zusammenfassung**  
 **Sqlkreatedatasource** zeigt ein Dialogfeld an, mit dem der Benutzer eine Datenquelle hinzufügen kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLCreateDataSource(  
     HWND    hwnd,  
     LPSTR   lpszDS);  
```  
  
## <a name="arguments"></a>Argumente  
 *HWND*  
 Der Handle des übergeordneten Fensters.  
  
 *lpszds*  
 Der Der Name der Datenquelle. *lpszds* können ein NULL-Zeiger oder eine leere Zeichenfolge sein.  
  
## <a name="returns"></a>Rückgabe  
 **Sqlkreatedatasource** gibt true zurück, wenn die Datenquelle erstellt wird. Andernfalls wird false zurückgegeben.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCreateDataSource** "false" zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster handle.|Das *HWND* -Argument war ungültig oder NULL.|  
|ODBC_ERROR_INVALID_DSN|Ungültiger DSN|Das *lpszds* -Argument enthielt eine Zeichenfolge, die für einen DSN ungültig war.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Fehler beim **ConfigDSN** -Rückruf mit der ODBC_ADD_DSN-Option.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber-oder Konvertierungs-Setup Bibliothek konnte nicht geladen werden.|Die Treiber Setup Bibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_USER_CANCELED|Benutzer Abbruch Vorgang|Die Erstellung einer neuen Datenquelle wurde vom Benutzer abgebrochen.|  
|ODBC_ERROR_CREATE_DSN_FAILED|Der angeforderte DSN konnte nicht erstellt werden.|Es konnte keine Verbindung mit der Datenbank hergestellt werden. der **SQLDriverConnect** -Befehl für einen Datei-DSN hat keine erfolgreiche Verbindung zurückgegeben.<br /><br /> In die Datei konnte nicht geschrieben werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 Wenn *HWND* NULL ist, gibt **sqlkreatedatasource** den Wert false zurück. Andernfalls wird das Dialogfeld **neue Datenquelle erstellen** mit einer Assistenten Seite angezeigt, mit der Sie den Typ der zu erstellenden Datenquelle auswählen können. Dies ist in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "Neue Datenquelle erstellen": Typ auswählen](../../../odbc/reference/syntax/media/ch23a.gif "CH23A")  
  
 Die Standardoption ist **File Data Source**. Wenn eine Datenquelle ausgewählt und als **nächstes** darauf geklickt wurde, wird die folgende Seite des Assistenten angezeigt, die eine Liste der installierten Treiber enthält.  
  
 ![Dialogfeld "Neue Datenquelle erstellen": Treiber auswählen](../../../odbc/reference/syntax/media/ch23b.gif "CH23B")  
  
 Wenn Sie auf **Abbrechen** klicken, wird das Dialogfeld ausgeblendet, und **sqlkreatedatasource** gibt mit dem Fehlercode ODBC_ERROR_USER_CANCELED false zurück. Wenn entweder die Option **Benutzerdaten Quelle** oder **System Datenquelle** ausgewählt wurde, ist die Schaltfläche **erweitert** nicht verfügbar.  
  
 Wenn Sie auf die Schaltfläche " **weiter** " klicken, wird je nach ausgewähltem Daten Quellentyp eine der folgenden Aktionen ausgeführt:  
  
-   Wenn die **Datei Datenquelle** ausgewählt wurde, wird eine Assistenten Seite angezeigt, auf der der Benutzer einen Dateinamen eingeben kann.  
  
-   Wenn entweder **Benutzerdaten Quelle** oder **System Datenquelle** ausgewählt wurde, wird eine Assistenten Seite angezeigt, auf der der Typ der Datenquelle und des Treibers angezeigt wird, um die Überprüfung zu überprüfen. Wenn Sie auf **Fertig** stellen klicken, wird die Datenquelle eingerichtet.  
  
 Wenn Sie auf der Seite neue Datenquelle erstellen auf **erweitert** klicken, wird eine Assistenten Seite angezeigt, auf der der Benutzer Treiber spezifische Informationen eingeben kann. Geben Sie im Textfeld dieses Dialog Felds den durch Returns getrennten Treiber und die Schlüsselwörter ein, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "Erweiterte Einstellungen für die Datei-DSN-Erstellung"](../../../odbc/reference/syntax/media/ch23c.gif "CH23C")  
  
 Weitere Treiber spezifische Schlüsselwörter finden Sie unter der Beschreibung von **SQLDriverConnect**. Alle außer **DSN** sind zulässig.  
  
 Der Standardwert für die Option **diese Verbindung überprüfen** ist true. Diese Standardeinstellung gilt unabhängig davon, ob diese Assistenten Seite aktiviert ist. Wenn auf **OK** geklickt wird, werden die im Textfeld angegebene Zeichenfolge und der Wert **dieser Verbindungs Option überprüfen** zwischengespeichert. (Wenn auf die Schaltfläche **Schließen** oder **Abbrechen** geklickt wird, gehen alle neu eingegebenen treiberspezifischen Informationen verloren, da die im Textfeld angegebene Zeichenfolge und der Wert **dieser Verbindungs Option überprüfen** nicht zwischengespeichert werden.)  
  
 Wenn auf der ersten Seite des Assistenten die Option **Datei Datenquelle** ausgewählt wurde, dann wird der Benutzer aufgefordert, einen Dateinamen einzugeben, nachdem ein Treiber ausgewählt und die Schlüsselwort Werte auf der Seite erweiterter Assistent eingegeben wurden. Klicken Sie auf **Durchsuchen** , um einen Dateinamen zu suchen. in diesem Fall wird das Standardverzeichnis im Feld durch **Suchen** durch eine Kombination aus dem Pfad angegeben, der von commonfiledir in HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion und "odbc\datasources" angegeben wird. (Wenn commonfiledir "c:\Programme\Gemeinsame Dateien" war, lautet das Standardverzeichnis "c:\Programme\Gemeinsame Dateien\ODBC\Data Sources".)  
  
 Wenn ein Dateiname eingegeben und **dann auf weiter** geklickt wird, wird der eingegebene Dateiname auf Gültigkeit der Standardregeln für die Datei Benennung des Betriebssystems überprüft. Wenn der Dateiname ungültig ist, wird der Benutzer im Feld Fehlermeldung darüber informiert, dass ein ungültiger Dateiname eingegeben wurde. Nachdem der Benutzer das Meldungs Feld bestätigt hat, wird der Fokus auf die Seite des Assistenten zurückgegeben, in der der Dateiname eingegeben wurde. Wenn der Dateiname gültig ist, wird eine Assistenten Seite mit den ausgewählten Schlüsselwort-Wert-Paaren zur Überprüfung angezeigt, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "Neue Datenquelle erstellen": Überprüfen](../../../odbc/reference/syntax/media/ch23d.gif "CH23D")  
  
 Wenn auf **Fertig** stellen geklickt wird und die **Datei Datenquelle** als Daten Quellentyp ausgewählt wurde, und wenn die Option **diese Verbindung überprüfen** auf true festgelegt ist, wird **SQLDriverConnect** mit den Schlüsselwörtern **SaveFile** und **Driver** aufgerufen. Das Argument *DriverCompletion* ist auf SQL_DRIVER_COMPLETE festgelegt. Der Dateiname für das Schlüsselwort " **SaveFile** " ist der Name, der eingegeben oder ausgewählt wurde, und der Treiber Name für das **Treiber** Schlüsselwort ist der Name, der ausgewählt wurde. Wenn eine Treiber spezifische Verbindungs Zeichenfolge auf der Seite des erweiterten Assistenten angegeben wurde, wird diese Zeichenfolge nach dem **Treiber** Schlüsselwort angefügt.  
  
 Wenn **SQLDriverConnect** SQL_SUCCESS zurückgibt, hat der Treiber-Manager die Datei-DSN erstellt. **Sqlkreatedatasource** gibt true zurück. Wenn **SQLDriverConnect** SQL_SUCCESS nicht zurückgibt, gibt ein Warn Meldungs Feld an, dass keine Verbindung mit der Datenquelle hergestellt werden konnte. Ein DSN mit minimalen Verbindungsinformationen kann weiterhin erstellt werden. Mit diesem Meldungs Feld kann der Benutzer die Datei-DSN-Erstellung entweder abbrechen oder fortsetzen.  
  
 Wenn der Benutzer die Erstellung des DSN fortsetzt, wird dieser Vorgang fortgesetzt, als ob die Option **diese Verbindung überprüfen** auf false festgelegt ist. Wenn der Benutzer das Abbrechen auswählt, wird false für **sqlkreatedatasource** mit dem Fehlercode ODBC_ERROR_CREATE_DSN_FAILED zurückgegeben.  
  
 Wenn die **Datei Datenquelle** als Daten Quellentyp ausgewählt wurde und die Option **diese Verbindung überprüfen** auf false festgelegt ist, wird ein Datei-DSN mit dem **Treiber** Schlüsselwort und der benutzerdefinierten Verbindungs Zeichenfolge (sofern vorhanden) von der erweiterten Assistenten Seite erstellt. Wenn die Dateierstellung erfolgreich war, wird für **sqlkreatedatasource**der Wert true zurückgegeben. Wenn die Dateierstellung nicht erfolgreich war, wird der Benutzer im Fehlermeldungs Feld mit dem Fehler benachrichtigt, der vom Betriebssystem zurückgegeben wurde. "False" wird für " **sqlkreatedatasource** " mit dem Fehlercode "ODBC_ERROR_CREATE_DSN_FAILED" zurückgegeben. Weitere Informationen zu Datei Datenquellen finden Sie unter [Herstellen einer Verbindung mithilfe von Datei Datenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)oder unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Wenn eine **Benutzer** -oder **System Datenquelle** als Daten Quellentyp ausgewählt wurde, wird **ConfigDSN** in der Treiber Setup Bibliothek mit dem ODBC_ADD_DSN *fRequest*aufgerufen. Weitere Informationen finden Sie unter [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Verwalten von Datenquellen|[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|
