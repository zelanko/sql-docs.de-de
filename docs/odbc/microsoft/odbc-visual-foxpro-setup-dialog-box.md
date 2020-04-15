---
title: ODBC Visual FoxPro Setup Dialogfeld | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], installing
- FoxPro ODBC driver [ODBC], installing
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef7ac702a69342833c6dfffa0ffc9cdd0ac2857e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298080"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Einrichten von ODBC-Visual FoxPro (Dialogfeld)
Im Dialogfeld **ODBC Visual FoxPro Setup** können Sie eine Visual FoxPro-Datenquelle hinzufügen oder ändern.  
  
 Informationen zum Herunterladen des Treibers finden Sie [auf der Download-Site des Visual FoxPro ODBC-Treibers](https://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Dialogfeld „Optionen“  
 **Datenquellenname**  
 Geben Sie den Namen ein, den Sie für die Datenquelle verwenden möchten.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung für die Datenquelle ein.  
  
 **Datenbanktyp**  
 Hier können Sie den Datenbanktyp auswählen, mit dem die Datenquelle eine Verbindung herstellen soll.  
  
 **Visual FoxPro-Datenbank (. DBC)**  
 Gibt an, dass die Datenquelle eine [database](../../odbc/microsoft/visual-foxpro-terminology.md) Verbindung mit einer Visual FoxPro-Datenbank (.dbc-Datei) und allen Tabellen und lokalen Ansichten in der Datenbank herstellt.  
  
 **Verzeichnis "Freies Tabellenverzeichnis"**  
 Gibt an, dass die Datenquelle eine Verbindung mit einem Verzeichnis [freier Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)herstellt. Alle [Datenbanktabellen](../../odbc/microsoft/visual-foxpro-terminology.md) im gleichen Verzeichnis werden von ODBC-Katalogfunktionen wie [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) oder [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)ignoriert. Auf Datenbanktabellen kann mithilfe von SQL SELECT-Anweisungen zugegriffen werden, die über [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) und [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)gesendet werden.  
  
 **Pfad**  
 Zeigt den Pfad und den Namen für die Datenbank oder das Verzeichnis der freien Tabellen an, mit denen die Datenquelle eine Verbindung herstellt.  
  
 **Durchsuchen**  
 Ermöglicht es Ihnen, Ihr System und Netzwerk nach der Datenbank oder dem Verzeichnis zu durchsuchen, mit der Sie die Datenquelle verbinden möchten.  
  
 **Optionen**  
 Erweitert das Dialogfeld, sodass Sie Visual FoxPro ODBC-Treiberoptionen festlegen können.  
  
## <a name="driver"></a>Treiber  
 **Sortierreihenfolge**  
 Die Reihenfolge, in der Felder sortiert werden. Die Standardsequenzen spiegeln die Sequenzen wider, die von Ihrer Sprachversion des Betriebssystems unterstützt werden. Eine Liste der unterstützten Sortiersequenzen finden Sie unter [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Exklusiv**  
 Wenn dieses Kontrollkästchen aktiviert ist, öffnet der Treiber die Visual FoxPro-Datenbank ausschließlich, wenn Sie über die Datenquelle auf Daten zugreifen. Andere Benutzer können nicht auf die Datenbank oder die Tabellen in der Datenbank zugreifen, während die Datenbank exklusiv geöffnet wird. Tabellen in der exklusiv geöffneten Datenbank werden als SHARED geöffnet. Um eine Tabelle exklusiv zu öffnen, verwenden Sie den Befehl [SET EXCLUSIVE.](../../odbc/microsoft/set-exclusive-command.md) Dieses Kontrollkästchen ist deaktiviert, wenn **der Datenbanktyp** auf **Das Verzeichnis "Freie Tabelle"** festgelegt ist.  
  
 **Null**  
 Bestimmt, ob Spalten, die mit ALTER TABLE und CREATE TABLE erstellt wurden, NULL-Werte zulassen. Wenn Sie Null ON, INSERT - SQL festlegen, wird ein Nullwert in eine Spalte eingefügt, die nicht in einem INSERT - SQL... VALUE-Klausel. Ein Leerzeichen wird eingefügt, wenn Null AUS ist. Sie können diese Option auch über eine übergebene Verbindungszeichenfolge wie im folgenden Code steuern:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Deleted**  
 Legt fest, ob als gelöscht markierte Zeilen zurückgegeben werden. Sie können diese Option auch über eine übergebene Verbindungszeichenfolge wie im folgenden Code steuern:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Abrufen von Daten im Hintergrund**  
 Legt fest, ob Datensätze im Hintergrund abgerufen werden (progressives Abrufen) oder ob Ihre Anwendung wartet, bis alle Datensätze in der Ergebnismenge abgerufen werden.
