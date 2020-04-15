---
title: SQLCreateDataSource-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94dc0d6d6f3b5bc96ae41aecda5b46f119cff85c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301200"
---
# <a name="sqlcreatedatasource-function"></a>SQLCreateDataSource-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLCreateDataSource** zeigt ein Dialogfeld an, mit dem der Benutzer eine Datenquelle hinzufügen kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLCreateDataSource(  
     HWND    hwnd,  
     LPSTR   lpszDS);  
```  
  
## <a name="arguments"></a>Argumente  
 *Hwnd*  
 [Eingabe] Übergeordnetes Fensterhandle.  
  
 *lpszDS*  
 [Eingabe] Datenquellenname. *lpszDS* kann ein Nullzeiger oder eine leere Zeichenfolge sein.  
  
## <a name="returns"></a>Rückgabe  
 **SQLCreateDataSource** gibt TRUE zurück, wenn die Datenquelle erstellt wird. Andernfalls wird FALSE zurückgegeben.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCreateDataSource** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallerError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fensterhandle|Das *hwnd-Argument* war ungültig oder NULL.|  
|ODBC_ERROR_INVALID_DSN|Ungültiger DSN|Das *argument lpszDS* enthielt eine Zeichenfolge, die für einen DSN ungültig war.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Der Aufruf von **ConfigDSN** mit der Option ODBC_ADD_DSN ist fehlgeschlagen.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber- oder Übersetzereinrichtungsbibliothek konnte nicht geladen werden.|Die Treibereinrichtungsbibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_USER_CANCELED|Benutzer abgebrochener Vorgang|Der Benutzer hat die Erstellung einer neuen Datenquelle abgebrochen.|  
|ODBC_ERROR_CREATE_DSN_FAILED|Der angeforderte DSN konnte nicht erstellt werden.|Es konnte keine Verbindung mit der Datenbank hergestellt werden. Der Aufruf von **SQLDriverConnect** für eine Datei-DSN hat keine erfolgreiche Verbindung zurückgegeben.<br /><br /> In die Datei konnte nicht geschrieben werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 Wenn *hwnd* null ist, gibt **SQLCreateDataSource** FALSE zurück. Andernfalls wird das Dialogfeld **Neue Datenquelle erstellen** mit einer Assistentenseite angezeigt, um den Typ der einzurichtenden Datenquelle auszuwählen, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "Neue Datenquelle erstellen": Typ auswählen](../../../odbc/reference/syntax/media/ch23a.gif "CH23A")  
  
 Die Standardoption ist **File Data Source**. Wenn eine Datenquelle ausgewählt und auf **Weiter** geklickt wurde, wird die folgende Seite des Assistenten angezeigt, die eine Liste der installierten Treiber enthält.  
  
 ![Dialogfeld "Neue Datenquelle erstellen": Treiber auswählen](../../../odbc/reference/syntax/media/ch23b.gif "CH23B")  
  
 Wenn auf **Abbrechen** geklickt wird, verschwindet das Dialogfeld und **SQLCreateDataSource** gibt FALSE mit dem Fehlercode ODBC_ERROR_USER_CANCELED zurück. Wenn die Option **Benutzerdatenquelle** oder **Systemdatenquelle** ausgewählt wurde, ist die Schaltfläche **Erweitert** nicht verfügbar.  
  
 Wenn auf die Schaltfläche **Weiter** geklickt wird, tritt eine der folgenden Optionen auf, je nachdem, welcher Datenquellentyp ausgewählt wurde:  
  
-   Wenn **Dateidatenquelle** ausgewählt wurde, wird eine Assistentenseite angezeigt, auf der der Benutzer einen Dateinamen eingeben kann.  
  
-   Wenn entweder **Benutzerdatenquelle** oder **Systemdatenquelle** ausgewählt wurde, wird eine Assistentenseite mit dem Typ der Datenquelle und des Treibers zur Überprüfung angezeigt, und wenn auf **Fertig** stellen geklickt wird, wird die Datenquelle eingerichtet.  
  
 Wenn auf der Seite Neuer Datenquellen-Assistent auf **Erweitert** geklickt wird, wird eine Assistentenseite angezeigt, auf der der Benutzer treiberspezifische Informationen eingeben kann. Geben Sie im Textfeld dieses Dialogfelds den Treiber und die Schlüsselwörter getrennt durch Rückgaben ein, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "Erweiterte Einstellungen für die Datei-DSN-Erstellung"](../../../odbc/reference/syntax/media/ch23c.gif "CH23C")  
  
 Weitere treiberspezifische Schlüsselwörter finden Sie unter der Beschreibung von **SQLDriverConnect**. Alle außer **DSN** sind zulässig.  
  
 Die Standardeinstellung für die Option **Verify This Connection** ist TRUE. Diese Standardeinstellung gilt unabhängig davon, ob diese Assistentenseite aktiviert ist oder nicht. Wenn auf **OK** geklickt wird, werden die im Textfeld angegebene Zeichenfolge und der Optionswert **"Diese Verbindung überprüfen"** zwischengespeichert. (Wenn auf die Schaltfläche **Schließen** oder **Abbrechen** geklickt wird, gehen alle neu eingegebenen treiberspezifischen Informationen verloren, da die im Textfeld angegebene Zeichenfolge und der Optionswert **"Diese Verbindung überprüfen"** nicht zwischengespeichert werden.)  
  
 Wenn **Dateidatenquelle** auf der ersten Assistentenseite ausgewählt wurde, wird der Benutzer aufgefordert, einen Dateinamen einzugeben, nachdem ein Treiber ausgewählt und die Schlüsselwortwerte auf der Seite Erweiterter Assistent eingegeben wurden. Klicken Sie auf **Durchsuchen,** um nach einem Dateinamen zu suchen. In diesem Fall wird das Standardverzeichnis im Feld **Durchsuchen** durch eine Kombination des von CommonFileDir in HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Windows-CurrentVersion und "ODBC-DataSources" angegebenen Pfads angegeben. (Wenn CommonFileDir "C:-Programmdateien, allgemeine Dateien" war, wäre das Standardverzeichnis "C:-Programmdateien, "Gemeinsame Dateien", "ODBC-Datenquellen".)  
  
 Wenn ein Dateiname eingegeben wurde und **auf Weiter** geklickt wird, wird der eingegebene Dateiname auf Gültigkeit mit den Standardregeln für die Dateibenennung des Betriebssystems überprüft. Wenn der Dateiname ungültig ist, benachrichtigt ein Fehlermeldungsfeld den Benutzer, dass ein ungültiger Dateiname eingegeben wurde. Nachdem der Benutzer das Meldungsfeld bestätigt hat, wird der Fokus auf die Assistentenseite zurückgesendet, auf der der Dateiname eingegeben wird. Wenn der Dateiname gültig ist, wird eine Assistentenseite, auf der die ausgewählten Keyword-Wert-Paare angezeigt werden, zur Überprüfung angezeigt, wie in der folgenden Abbildung dargestellt.  
  
 ![Dialogfeld "Neue Datenquelle erstellen": Überprüfen](../../../odbc/reference/syntax/media/ch23d.gif "CH23D")  
  
 Wenn auf **Fertig** stellen geklickt wird und **Dateidatenquelle** als Datenquellentyp ausgewählt wurde und wenn die **Option Diese Verbindung true überprüfen** ist, wird **SQLDriverConnect** mit den Schlüsselwörtern **SAVEFILE** und **DRIVER** aufgerufen. Das *Argument DriverCompletion* ist auf SQL_DRIVER_COMPLETE festgelegt. Der Dateiname für das **Schlüsselwort SAVEFILE** ist der Name, der eingegeben oder ausgewählt wurde, und der Treibername für das **Schlüsselwort DRIVER** ist der gewählte Name. Wenn auf der Seite Erweiterter Assistent eine treiberspezifische Verbindungszeichenfolge angegeben wurde, wird diese Zeichenfolge nach dem **SCHLÜSSELwort DRIVER** angehängt.  
  
 Wenn **SQLDriverConnect** SQL_SUCCESS zurückgibt, hat der Treiber-Manager die Datei-DSN erstellt. **SQLCreateDataSource** gibt TRUE zurück. Wenn **SQLDriverConnect** SQL_SUCCESS nicht zurückgibt, weist ein Warnmeldungsfeld darauf hin, dass keine Verbindung mit der Datenquelle hergestellt werden konnte. Ein DSN mit minimalen Verbindungsinformationen kann weiterhin erstellt werden. Mit diesem Meldungsfeld kann der Benutzer die Datei-DSN-Erstellung entweder abbrechen oder fortsetzen.  
  
 Wenn der Benutzer die Erstellung des DSN fortsetzt, wird dieser Prozess so fortgesetzt, als ob die Option **Überprüfen dieser Verbindung** auf FALSE festgelegt wäre. Wenn der Benutzer den Vorgang abbricht, wird FALSE für **SQLCreateDataSource** mit dem Fehlercode ODBC_ERROR_CREATE_DSN_FAILED zurückgegeben.  
  
 Wenn **Dateidatenquelle** als Datenquellentyp ausgewählt wurde und die Option **Überprüfen dieser Verbindung** FALSE ist, wird ein Datei-DSN mit dem **SCHLÜSSELwort DRIVER** und der benutzerdefinierten Verbindungszeichenfolge (falls vorhanden) auf der Seite Erweiterter Assistent erstellt. Wenn die Dateierstellung erfolgreich war, wird TRUE für **SQLCreateDataSource**zurückgegeben. Wenn die Dateierstellung nicht erfolgreich war, benachrichtigt ein Fehlermeldungsfeld den Benutzer über den Fehler, der vom Betriebssystem zurückgegeben wurde. FALSE wird für **SQLCreateDataSource** mit dem Fehlercode ODBC_ERROR_CREATE_DSN_FAILED zurückgegeben. Weitere Informationen zu Dateidatenquellen finden Sie unter [Verbinden mit Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)oder [sqlDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Wenn **Benutzer-** oder **Systemdatenquelle** als Datenquellentyp ausgewählt wurde, wird **ConfigDSN** in der Treiberinstallationsbibliothek mit dem ODBC_ADD_DSN *fRequest*aufgerufen. Weitere Informationen finden Sie unter [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Verwalten von Datenquellen|[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|
