---
title: ODBC Visual FoxPro-Setup (Dialog Feld) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298080"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Einrichten von ODBC-Visual FoxPro (Dialogfeld)
Im Dialogfeld **Visual FoxPro-Setup für ODBC** können Sie eine Visual FoxPro-Datenquelle hinzufügen oder ändern.  
  
 Informationen zum Herunterladen des Treibers finden Sie auf [der Visual FoxPro-ODBC-Treiber-Download Website](https://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Dialogfeld „Optionen“  
 **Datenquellen Name**  
 Geben Sie den Namen ein, den Sie für die Datenquelle verwenden möchten.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung für die Datenquelle ein.  
  
 **Datenbanktyp**  
 Hiermit können Sie den Typ der Datenbank auswählen, mit der die Datenquelle eine Verbindung herstellen soll.  
  
 **Visual FoxPro-Datenbank (. DBC (Double**  
 Gibt an, dass die Datenquelle eine Verbindung mit einer Visual FoxPro- [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md) (DBC-Datei) und mit allen Tabellen und lokalen Sichten in der Datenbank herstellt.  
  
 **Kostenloses Tabellen Verzeichnis**  
 Gibt an, dass die Datenquelle eine Verbindung mit einem Verzeichnis mit [freien Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)herstellt. Alle [Daten Bank](../../odbc/microsoft/visual-foxpro-terminology.md) Tabellen im gleichen Verzeichnis werden von ODBC-Katalog Funktionen wie [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) oder [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)ignoriert. Auf Datenbanktabellen kann mithilfe von SQL SELECT-Anweisungen zugegriffen werden, die über [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) und [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)gesendet werden.  
  
 **Pfad**  
 Zeigt den Pfad und den Namen für die Datenbank oder das Verzeichnis der freien Tabellen an, mit denen die Datenquelle eine Verbindung herstellt.  
  
 **Durchsuchen**  
 Ermöglicht es Ihnen, das System und das Netzwerk nach der Datenbank oder dem Verzeichnis zu durchsuchen, mit der Sie eine Verbindung mit der Datenquelle herstellen möchten.  
  
 **Optionen**  
 Erweitert das Dialogfeld, sodass Sie die Visual FoxPro-ODBC-Treiberoptionen festlegen können.  
  
## <a name="driver"></a>Treiber  
 **Sortierreihenfolge**  
 Die Reihenfolge, in der Felder sortiert werden. Die Standardsequenzen entsprechen den Sequenzen, die von Ihrer Sprachversion des Betriebssystems unterstützt werden. Eine Liste der unterstützten Sortierungs Sequenzen finden Sie unter [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Exklusiv**  
 Wenn dieses Kontrollkästchen aktiviert ist, öffnet der Treiber die Visual FoxPro-Datenbank ausschließlich, wenn Sie mithilfe der Datenquelle auf Daten zugreifen. Andere Benutzer können nicht auf die Datenbank oder die Tabellen in der Datenbank zugreifen, während die Datenbank exklusiv geöffnet wird. Tabellen in der exklusiv geöffneten Datenbank werden als freigegeben geöffnet. Verwenden Sie den Befehl [exklusiven festlegen](../../odbc/microsoft/set-exclusive-command.md) , um exklusiv eine Tabelle zu öffnen. Dieses Kontrollkästchen ist deaktiviert, wenn der **Datenbanktyp** auf das **freie Tabellen Verzeichnis**festgelegt ist.  
  
 **Normal**  
 Bestimmt, ob mit ALTER TABLE und CREATE TABLE erstellte Spalten NULL-Werte zulassen. Wenn Sie für NULL festlegen, fügt INSERT-SQL einen NULL-Wert in eine Spalte ein, die nicht in einem INSERT-SQL... VALUE-Klausel. Wenn NULL deaktiviert ist, wird ein leeres-Zeichen eingefügt. Sie können diese Option auch über eine bestandene Verbindungs Zeichenfolge steuern, wie im folgenden Code:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Deleted**  
 Bestimmt, ob Zeilen zurückgegeben werden, die als gelöscht markiert sind. Sie können diese Option auch über eine bestandene Verbindungs Zeichenfolge steuern, wie im folgenden Code:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Abrufen von Daten im Hintergrund**  
 Bestimmt, ob Datensätze im Hintergrund abgerufen werden (progressives abrufen), oder die Anwendung wartet, bis alle Datensätze im Resultset abgerufen werden.
