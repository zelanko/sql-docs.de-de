---
title: Verwalten von Datenquellen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- deleting data sources [ODBC], ODBC data source administrator
- data sources [ODBC], ODBC data source administrator
- adding data sources [ODBC], ODBC data source administrator
- removing data sources [ODBC], ODBC data source administrator
- ODBC data source administrator [ODBC], data source management
ms.assetid: 67cc4945-4850-4eb4-8da6-b835ddaeca4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5069ac9a5babc3071c52d73d5b56b21729a5d8a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307211"
---
# <a name="managing-data-sources"></a>Verwalten von Datenquellen
Nachdem Sie einen ODBC-Treiber aus dem Setupprogramm des Treibers installiert haben, können Sie eine oder mehrere Datenquellen dafür definieren. Der Datenquellenname (Data Source Name, DSN) sollte eine eindeutige Beschreibung der Daten enthalten. z. *B. Lohn-* oder *Kontenpflicht .* Die Benutzer- und Systemdatenquellen, die für alle aktuell installierten Treiber definiert sind, werden auf den Registerkarten **Benutzer-DSN** oder **System-DSN** im Dialogfeld **ODBC-Datenquellenadministrator** aufgeführt. Die Dateidatenquellen in einem bestimmten Verzeichnis werden auf der Registerkarte **Datei-DSN** aufgeführt. das anzuzeigende Verzeichnis wird in das Feld **"In suchen"** auf der Registerkarte **Datei-DSN** eingegeben.  
  
> [!NOTE]  
>  Um eine Datenquelle zu verwalten, die eine Verbindung zu einem 32-Bit-Treiber unter der 64-Bit-Plattform herstellt, verwenden Sie c:-Windows-System-sysWOW64-odbcad32.exe. Um eine Datenquelle zu verwalten, die eine Verbindung zu einem 64-Bit-Treiber herstellt, verwenden Sie c:-Windows-System32-odbcad32.exe. In **Administrative Tools** auf einem 64-Bit-Betriebssystem für Windows 8 gibt es Symbole für das Dialogfeld 32-Bit und 64-Bit **ODBC Data Source Administrator.**  
  
 Wenn Sie die 64-Bit-Datei odbcad32.exe verwenden, um einen DSN zu konfigurieren oder zu entfernen, der eine Verbindung zu einem 32-Bit-Treiber herstellt, z. B. **Driver do Microsoft Access (\*.mdb),** wird die folgende Fehlermeldung angezeigt:  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 Um diesen Fehler zu beheben, verwenden Sie die 32-Bit-Datei odbcad32.exe, um den DSN zu konfigurieren oder zu entfernen.  
  
 Eine Datenquelle ordnet einen bestimmten ODBC-Treiber den Daten zu, auf die Sie über diesen Treiber zugreifen möchten. Sie können z. B. eine Datenquelle erstellen, um den ODBC dBASE-Treiber für den Zugriff auf eine oder mehrere dBASE-Dateien in einem bestimmten Verzeichnis auf Ihrer Festplatte oder einem Netzwerklaufwerk zu verwenden. Mit dem ODBC-Datenquellenadministrator können Sie Datenquellen hinzufügen, ändern und löschen, wie in der folgenden Tabelle beschrieben.  
  
|Aktion|BESCHREIBUNG|  
|------------|-----------------|  
|Hinzufügen von Datenquellen|Es ist möglich, mehrere Datenquellen hinzuzufügen, wobei jeder einen Treiber mit einigen Daten, auf die Sie zugreifen möchten, mit diesem Treiber assoziiert. Geben Sie jeder Datenquelle einen Namen, der diese Datenquelle eindeutig identifiziert. Wenn Sie beispielsweise eine Datenquelle für einen Satz von dBASE-Dateien erstellen, die Kundeninformationen enthalten, können Sie die Datenquelle als "Kunden" bezeichnen. Anwendungen zeigen in der Regel Datenquellennamen für Benutzer an, aus denen Sie auswählen können.<br /><br /> Das Hinzufügen einer Dateidatenquelle unterscheidet sich geringfügig vom Hinzufügen von Benutzer- oder Systemdatenquellen. Weitere Informationen finden Sie in der Hilfedatei des ODBC-Datenquellenadministrators.|  
|Ändern von Datenquellen|Je nach Ihren Anforderungen ist es möglicherweise erforderlich, Datenquellen neu zu konfigurieren. Sie können die Optionen zurücksetzen, indem Sie in einem beliebigen Dialogfeld für das Treiber-Setup auf **Konfigurieren** klicken.|  
|Löschen von Datenquellen|Klicken Sie auf **Entfernen,** nachdem Sie eine Datenquelle ausgewählt haben.|  
  
 Weitere Informationen zu Dateidatenquellen finden Sie unter [Verbinden mit Dateidatenquellen](../../odbc/reference/develop-app/connecting-using-file-data-sources.md) oder die [SQLDriverConnect-Funktion](../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-Datenquellen-Administrator](../../odbc/admin/odbc-data-source-administrator.md)
