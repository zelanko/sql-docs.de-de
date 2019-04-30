---
title: Verwalten von Datenquellen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a1f8893351ceb68ebd7c42e3ac82c876c01c10b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198757"
---
# <a name="managing-data-sources"></a>Verwalten von Datenquellen
Nachdem Sie einen ODBC-Treiber vom Setupprogramm vom Treiber installiert haben, können Sie eine oder mehrere Datenquellen dafür definieren. Der Datenquellenname (DSN) sollte eine eindeutige Beschreibung des ausgewählten angeben; z. B. *Gehaltsabrechnungen* oder *Accounts Payable*. Die Benutzer und System-Datenquellen, die für alle Treiber installierten definiert sind, finden Sie in der **Benutzer-DSN** oder **System-DSN** Registerkarten der **ODBC-Datenquellenadministrator**Dialogfeld. In einem Verzeichnis die Datei-Datenquellen finden Sie in der **Datei-DSN** Registerkarte Verzeichnis angezeigt werden wird eingegeben in die **Suchen in** im Feld der **Datei-DSN** Registerkarte.  
  
> [!NOTE]  
>  Verwenden Sie zum Verwalten von einer Datenquelle, die mit einer 32-Bit-Treiber unter 64-Bit-Plattform verbindet c:\windows\sysWOW64\odbcad32.exe. Verwenden Sie zum Verwalten von einer Datenquelle, die Verbindung mit einer 64-Bit-Treiber c:\windows\system32\odbcad32.exe. In **Verwaltung** auf einem 64-Bit-Windows 8-Betriebssystem befinden sich die Symbole für die 32-Bit- und 64-Bit- **ODBC-Datenquellenadministrator** Dialogfeld.  
  
 Wenn Sie der 64-Bit-odbcad32.exe mithilfe konfigurieren oder entfernen einen DSN ein, die Verbindung mit einer 32-Bit-Treiber, z. B. **Treiber werden von Microsoft Access (\*.mdb)**, Sie erhalten die folgende Fehlermeldung angezeigt:  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 Um diesen Fehler zu beheben, verwenden Sie die 32-Bit-odbcad32.exe konfigurieren oder entfernen den DSN.  
  
 Eine Datenquelle ordnet einen bestimmten ODBC-Treiber die Daten, die Sie über diesen Treiber zugreifen möchten. Beispielsweise können Sie eine Datenquelle den ODBC-dBASE-Treiber zu verwenden, um Zugriff auf eine oder mehrere dBASE-Dateien finden Sie in einem bestimmten Verzeichnis auf Ihrer Festplatte oder einem Netzlaufwerk erstellen. Verwenden den ODBC-Datenquellen-Administrator, können Sie hinzufügen, ändern und Löschen von Datenquellen, wie in der folgenden Tabelle beschrieben.  
  
|Aktion|Description|  
|------------|-----------------|  
|Hinzufügen von Datenquellen|Es ist möglich, mehrere Datenquellen hinzufügen jeweils einen Treiber zuordnen, mit einigen Daten, die Sie mit diesen Treiber zugreifen möchten. Benennen Sie jede Datenquelle, die diese Datenquelle eindeutig identifiziert. Z. B. Wenn Sie eine Datenquelle für einen Satz von dBASE-Dateien, die Kundeninformationen enthalten erstellen, können Sie die Datenquelle "Customers". nennen Anwendungen anzeigen in der Regel Datenquellennamen für Benutzer eine Auswahl treffen.<br /><br /> Das Hinzufügen einer Datei als Datenquelle ist geringfügig von dem Benutzer oder System-Datenquellen hinzufügen. Weitere Informationen finden Sie unter den ODBC-Datenquellenadministrator Hilfedatei.|  
|Ändern von Datenquellen|Je nach Ihren Anforderungen finden Sie es möglicherweise erforderlich, um Datenquellen neu zu konfigurieren. Sie können die Optionen zurücksetzen, indem Sie auf **konfigurieren** in einem beliebigen Dialogfeld des Treiber-Setup.|  
|Löschen von Datenquellen|Klicken Sie auf **entfernen** nach dem Auswählen einer Datenquelle.|  
  
 Weitere Informationen zu Datei-Datenquellen, finden Sie unter [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../odbc/reference/develop-app/connecting-using-file-data-sources.md) oder [SQLDriverConnect-Funktion](../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-Datenquellen-Administrator](../../odbc/admin/odbc-data-source-administrator.md)
