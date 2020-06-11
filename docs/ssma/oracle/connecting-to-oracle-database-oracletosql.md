---
title: Herstellen einer Verbindung mit Oracle Database (oracleto SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit der Oracle-Datenbank herstellen, um die Oracle-Datenbank zu SQL Server migrieren SSMA Ruft Metadaten zu allen Oracle-Schemas ab und zeigt diese an.
author: nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 06/04/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Refreshing Oracle Metadata
ms.assetid: e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6
ms.author: alexiva
ms.openlocfilehash: d6fc63d62e9761f167eb70165c6f9324f56253a8
ms.sourcegitcommit: 38639b67a135ca1a50a8e38fa61a089efe90e3f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84454533"
---
# <a name="connecting-to-oracle-database-oracletosql"></a>Herstellen einer Verbindung mit Oracle Database (OracleToSQL)

Zum Migrieren von Oracle-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] müssen Sie eine Verbindung mit der Oracle-Datenbank herstellen, die Sie migrieren möchten. Wenn Sie eine Verbindung herstellen, werden von SSMA Metadaten zu allen Oracle-Schemas abgerufen und anschließend im Bereich Oracle-metadatenexplorer angezeigt. SSMA speichert Informationen über den Datenbankserver, speichert aber keine Kenn Wörter.

Die Verbindung mit der Datenbank bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung herstellen, wenn Sie eine aktive Verbindung mit der Datenbank herstellen möchten.

Metadaten über die Oracle-Datenbank werden nicht automatisch aktualisiert. Wenn Sie die Metadaten im Oracle-metadatenexplorer aktualisieren möchten, müssen Sie Sie stattdessen manuell aktualisieren. Weitere Informationen finden Sie im Abschnitt "Aktualisieren von Oracle-Metadaten" weiter unten in diesem Thema.

## <a name="required-oracle-permissions"></a>Erforderliche Oracle-Berechtigungen

Das Konto, das zum Herstellen einer Verbindung mit der Oracle-Datenbank verwendet wird, muss mindestens über die folgenden Berechtigungen verfügen:

- `CONNECT`  
  Erforderlich, um eine Verbindung mit der Datenbank herzustellen (eine Sitzung erstellen).

- `SELECT ANY DICTIONARY`  
  Erforderlich, um System Wörterbuch Tabellen abzufragen (z `SYS.MLOG$` . b.), um alle Objekte zu ermitteln.

Dadurch kann SSMA alle Objekte in dem Schema laden, das sich im Besitz des Benutzers befindet, der eine Verbindung herstellt. In den meisten realen Szenarios gibt es Schema übergreifende Verweise zwischengespeicherten Prozeduren, und SSMA muss alle referenzierten Objekte für eine erfolgreiche Konvertierung ermitteln können. Zum Abrufen von Metadaten für Objekte, die in anderen Schemas definiert sind, muss das Konto über die folgenden zusätzlichen Berechtigungen verfügen:

- `SELECT ANY TABLE`  
  Erforderlich, um Tabellen, Sichten, materialisierte Sichten und Synonyme in anderen Schemas zu ermitteln.

- `SELECT ANY SEQUENCE`  
  Erforderlich, um Sequenzen in anderen Schemas zu ermitteln.

- `CREATE ANY PROCEDURE`  
  Erforderlich zum Ermitteln von PL/SQL für Prozeduren, Funktionen und Pakete in anderen Schemas.

- `CREATE ANY TRIGGER`  
  Erforderlich, um die auslöserdefinitionen in anderen Schemas zu ermitteln.

- `CREATE ANY TYPE`  
  Erforderlich, um Typen zu ermitteln, die in anderen Schemas definiert sind.

Für einige der SSMA-Features sind zusätzliche Berechtigungen erforderlich. Wenn Sie beispielsweise die Funktion " [Tester](testing-migrated-database-objects-oracletosql.md) " und " [Backup Management](managing-backups-oracletosql.md) " verwenden möchten, müssen Sie dem Benutzer, der die Verbindung herstellt, Folgendes erteilen:

- `EXECUTE ANY PROCEDURE`  
  Erforderlich zum Ausführen von Prozeduren und Funktionen, die Sie in allen Schemas testen möchten.

- `CREATE ANY TABLE` und `ALTER ANY TABLE`  
  Ist erforderlich, um temporäre Tabellen für die Änderungs Nachverfolgung und Sicherungen zu erstellen und zu ändern.

- `INSERT ANY TABLE` und `UPDATE ANY TABLE`  
  Erforderlich zum Einfügen von Änderungs nach Verfolgungs-und Sicherungsdaten in temporäre Tabellen.

- `DROP ANY TABLE`  
  Erforderlich zum Löschen von temporären Tabellen, die für die Änderungs Nachverfolgung und Sicherungen verwendet werden.

- `CREATE ANY INDEX` und `ALTER ANY INDEX`  
  Erforderlich zum Erstellen und Ändern von Indizes für temporäre Tabellen, die für die Änderungs Nachverfolgung und Sicherungen verwendet werden.

- `DROP ANY INDEX`  
  Erforderlich zum Löschen von Indizes für temporäre Tabellen, die für die Änderungs Nachverfolgung und Sicherungen verwendet werden.

- `CREATE ANY TRIGGER` und `ALTER ANY TRIGGER`  
  Erforderlich zum Erstellen und ändern temporärer Trigger, die für die Änderungs Nachverfolgung verwendet werden.

- `DROP ANY TRIGGER`  
  Zum Löschen temporärer Trigger, die für die Änderungs Nachverfolgung verwendet werden.

> [!NOTE]
> Dies ist ein allgemeiner Satz von Berechtigungen, die für die ordnungsgemäße Ausführung von SSMA erforderlich sind. Wenn Sie den Umfang der Migration auf eine Teilmenge von Schemas eingrenzen möchten, können Sie dies tun, indem Sie dem begrenzten Satz von Objekten anstelle von die Berechtigungen für die begrenzte Anzahl von Objekten erteilen `ALL` . Es kann sehr schwierig sein, alle Abhängigkeiten ordnungsgemäß zu identifizieren, sodass SSMA nicht ordnungsgemäß funktioniert. Es wird dringend empfohlen, sich wie oben definiert an die generische Menge zu halten, um mögliche Berechtigungsprobleme während des Migrations Vorgangs auszuschließen.

## <a name="establishing-a-connection-to-oracle"></a>Herstellen einer Verbindung mit Oracle

Wenn Sie eine Verbindung mit einer Datenbank herstellen, liest SSMA die Metadaten der Datenbank und fügt diese Metadaten dann der Projektdatei hinzu. Diese Metadaten werden von SSMA verwendet, wenn Objekte in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Syntax konvertiert werden und Daten zu migriert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie können diese Metadaten im Bereich Oracle-metadatenexplorer durchsuchen und die Eigenschaften einzelner Datenbankobjekte überprüfen.

> [!IMPORTANT]
> Bevor Sie versuchen, eine Verbindung herzustellen, stellen Sie sicher, dass der Datenbankserver ausgeführt wird und Verbindungen akzeptieren kann.

**Zum Herstellen einer Verbindung mit Oracle**

1. Wählen Sie im Menü **Datei** die Option **mit Oracle verbinden**aus.  
   Wenn Sie zuvor eine Verbindung mit Oracle hergestellt haben, wird der Befehls Name **erneut mit Oracle**verbunden.
  
2. Wählen Sie im Feld **Anbieter** die Option **Oracle-Client Anbieter** oder **OLE DB Anbieter**aus, je nachdem, welcher Anbieter installiert ist. Der Standardwert ist Oracle Client.

3. Wählen Sie im Feld **Modus** entweder den **Standard Modus**, den **TNSNAME-Modus**oder den **Verbindungs Zeichen folgen Modus**aus.  
   Verwenden Sie den Standardmodus, um den Servernamen und den Port anzugeben. Verwenden Sie den Dienstnamen Modus, um den Oracle-Dienstnamen manuell anzugeben. Verwenden Sie den Verbindungs Zeichen folgen Modus, um eine vollständige Verbindungs Zeichenfolge

4. Wenn Sie den **Standard Modus**auswählen, geben Sie die folgenden Werte an:
   1. Geben Sie im Feld **Server Name** den Namen oder die IP-Adresse des Datenbankservers ein, oder wählen Sie ihn aus.
   2. Wenn der Datenbankserver nicht für die Annahme von Verbindungen über den Standardport (1521) konfiguriert ist, geben Sie im Feld **Serverport** die Portnummer ein, die für Oracle-Verbindungen verwendet wird.
   3. Geben Sie im Feld **Oracle sid** den System Bezeichner ein.
   4. Geben Sie im Feld **Benutzername** ein Oracle-Konto ein, das über die erforderlichen Berechtigungen verfügt.
   5. Geben Sie im Feld **Kennwort** das Kennwort für den angegebenen Benutzernamen ein.

5. Wenn Sie den **TNSNAME-Modus**auswählen, geben Sie die folgenden Werte an:
   1. Geben Sie im Feld **Verbindungs Bezeichner** den Verbindungs Bezeichner (TNS-Alias) der Datenbank ein.
   2. Geben Sie im Feld **Benutzername** ein Oracle-Konto ein, das über die erforderlichen Berechtigungen verfügt.
   3. Geben Sie im Feld **Kennwort** das Kennwort für den angegebenen Benutzernamen ein.
  
6. Wenn Sie den **Verbindungs Zeichen folgen Modus**auswählen, geben Sie im Feld **Verbindungs Zeichenfolge** eine Verbindungs Zeichenfolge an.  
   Das folgende Beispiel zeigt eine OLE DB Verbindungs Zeichenfolge:

   `Provider=OraOLEDB.Oracle;Data Source=MyOracleDB;User Id=myUsername;Password=myPassword;`

   Das folgende Beispiel zeigt eine Oracle-Client Verbindungs Zeichenfolge, die die integrierte Sicherheit verwendet:

   `Data Source=MyOracleDB;Integrated Security=yes;`

   Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Oracle &#40;oracleto SQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md).

## <a name="reconnecting-to-oracle"></a>Erneutes Herstellen einer Verbindung mit Oracle

Die Verbindung mit dem Datenbankserver bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung herstellen, wenn Sie eine aktive Verbindung mit der Datenbank herstellen möchten. Sie können offline arbeiten, bis Sie Metadaten aktualisieren, Datenbankobjekte in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten migrieren möchten.

## <a name="refreshing-oracle-metadata"></a>Aktualisieren von Oracle-Metadaten

Metadaten über die Oracle-Datenbank werden nicht automatisch aktualisiert. Bei den Metadaten im Oracle-metadatenexplorer handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung hergestellt haben, oder wenn Sie das letzte Mal manuell Sie können Metadaten für alle Schemas, ein einzelnes Schema oder einzelne Datenbankobjekte manuell aktualisieren.

**So aktualisieren Sie Metadaten**

1. Stellen Sie sicher, dass Sie mit der Datenbank verbunden sind.

2. Aktivieren Sie im Oracle-metadatenexplorer das Kontrollkästchen neben jedem Schema oder Datenbankobjekt, das Sie aktualisieren möchten.

3. Klicken Sie mit der rechten Maustaste auf **Schemas**oder das einzelne Schema oder Datenbankobjekt, und wählen Sie dann **aus Datenbank aktualisieren aus**.  
   Wenn Sie nicht über eine aktive Verbindung verfügen, zeigt SSMA das Dialogfeld **Verbindung mit Oracle herstellen an** , sodass Sie eine Verbindung herstellen können.

4. Geben Sie im Dialogfeld aus Datenbank aktualisieren an, welche Objekte aktualisiert werden sollen.

   - Um ein Objekt zu aktualisieren, klicken Sie auf das **aktive** Feld neben dem Objekt, bis ein Pfeil angezeigt wird.
   - Um zu verhindern, dass ein Objekt aktualisiert wird, klicken Sie auf das **aktive** Feld neben dem Objekt, bis ein **X** angezeigt wird.
   - Um eine Kategorie von Objekten zu aktualisieren oder abzulehnen, klicken Sie auf das **aktive** Feld neben dem Kategorieordner.

   Um die Definitionen der Farbcodierung anzuzeigen, klicken Sie auf die Schaltfläche **Legende** .

5. [!INCLUDE[clickOK](../../includes/clickok-md.md)]

## <a name="next-steps"></a>Nächste Schritte

Der nächste Schritt des Migrations Vorgangs besteht darin, [eine Verbindung mit einer Instanz von SQL Server herzustellen](connecting-to-sql-server-oracletosql.md).

## <a name="see-also"></a>Weitere Informationen

[Migrieren von Oracle-Datenbanken zu SQL Server &#40;oracleto SQL-&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)
