---
title: Konvertieren den Zugriff auf Datenbankobjekte (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases
- Access databases, converting schemas
- conversion
- conversion, converting schemas
- indexes, altering
- metadata
- metadata, altering
- metadata, converting
- migrating databases, one-click
- one-click migration
- schemas
- schemas, converting
- SQL
- SQL, converting
- syntax
- syntax, converting
- tables, altering
- translating Access to SQL Azure
- translating Access to SQL Server
ms.assetid: e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c4bb3d1b6fdc57e1251e9c8ca39f0c7437ffb126
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63139020"
---
# <a name="converting-access-database-objects-accesstosql"></a>Konvertieren den Zugriff auf Datenbankobjekte (AccessToSQL)
Nachdem Sie den Zugriff auf Datenbanken hinzugefügt und verbunden haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, SSMA zeigt die Metadaten für den Zugriff und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbankobjekte. Sie können jetzt den Zugriff auf Datenbankobjekte auswählen und anschließend konvertiert der Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Schemas.  
  
## <a name="the-conversion-process"></a>Konvertierungsprozess  
Konvertieren von Datenbankobjekten verwendet die Objektdefinitionen aus den Metadaten für den Zugriff, wandelt sie in der entsprechenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, und klicken Sie dann diese Informationen in das Projekt lädt. Klicken Sie dann sehen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte und deren Eigenschaften mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer.  
  
> [!IMPORTANT]  
> Konvertieren von Objekten erstellt keine Objekte im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Nur die Objektdefinitionen konvertiert, und speichert die Informationen in der SSMA-Projekt.  
  
Bei der Konvertierung gibt SSMA Status, um den Ausgabebereich und Fehler-, Warn- und informationsmeldungen in den Bereich Fehlerliste angezeigt. Verwenden Sie diese Informationen, um festzustellen, ob Sie Ihre Access-Datenbanken oder Ihre Konvertierungsprozess zum Abrufen der Ergebnisse für die gewünschte Konvertierung ändern möchten. Sie können auch die Informationen in der [Access-Datenbanken für die Migration vorbereiten](preparing-access-databases-for-migration-accesstosql.md) Thema, um zu bestimmen, welche werden und wird nicht konvertiert werden.  
  
## <a name="setting-conversion-options"></a>Festlegen von Optionen  
Lesen Sie vor dem Konvertieren von Objekten, die die Projektoptionen für die Konvertierung in den **Projekteinstellungen** Dialogfeld. Verwenden Sie das Dialogfeld zu öffnen, können Sie festlegen, wie SSMA indizierte Memospalten, Primärschlüssel, fremdschlüsseleinschränkungen, Zeitstempel und Tabellen ohne Indizes konvertiert. Weitere Informationen finden Sie unter [Project Settings (Conversion)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
## <a name="conversion-results"></a>Konvertierungsergebnisse  
Die folgende Tabelle zeigt, welche Zugriff Objekte konvertiert werden, und das resultierende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte:  
  
|Access-Objekt|Resultierende SQL Server-Objekt|  
|-----------------|-------------------------------|  
|-Tabelle|-Tabelle|  
|column|column|  
|Index|Index|  
|Fremdschlüssel|Fremdschlüssel|  
|Abfrage|Ansicht<br /><br />Die SELECT-Abfragen werden in Ansichten konvertiert. Andere Abfragen, z. B. UPDATE-Abfragen werden nicht migriert.<br /><br />SELECT-Abfragen, die Parameter annehmen, werden nicht konvertiert, ebenso wie Kreuztabellenberichten Abfragen.|  
|Bericht|nicht konvertiert|  
|Formular|nicht konvertiert|  
|Makro|nicht konvertiert|  
|Modul|nicht konvertiert|  
|Standardwert|Standardwert|  
|Zulassen von NULL Length-Eigenschaft für Spalte|CHECK-Einschränkung|  
|Validierungsregel für die Spalte|CHECK-Einschränkung|  
|Validierungsregel für die Tabelle|CHECK-Einschränkung|  
|Primärschlüssel|Primärschlüssel|  
  
## <a name="converting-access-objects"></a>Konvertieren den Zugriff auf Objekte  
Um den Zugriff auf Datenbankobjekte zu konvertieren, müssen Sie zuerst die Objekte auswählen, die Sie verwenden möchten, konvertieren, und lassen dann die SSMA, die die Konvertierung erforderlich sind. Anzeigen von ausgehenden Nachrichten bei der Konvertierung auf den **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**Um auszuwählen, und konvertieren den Zugriff auf Datenbankobjekte in SQL Server oder SQL Azure-syntax**  
  
1.  Erweitern Sie im Metadaten-Explorer für den Zugriff, **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
2.  Führen Sie eine oder mehrere der folgenden:  
  
    -   Um alle Datenbanken zu konvertieren, wählen Sie das Kontrollkästchen neben **Datenbanken**.  
  
    -   Klicken Sie zum konvertieren, oder lassen Sie die einzelne Datenbanken, aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Zum konvertieren, oder lassen Sie Abfragen aus, erweitern Sie die Datenbank, und aktivieren bzw. Deaktivieren der **Abfragen** Kontrollkästchen.  
  
    -   Klicken Sie zum konvertieren, oder lassen Sie einzelne Tabellen, erweitern Sie die Datenbank, erweitern Sie **Tabellen**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
3.  Führen Sie eines der folgenden Verfahren aus:  
  
    -   Um Schemas zu konvertieren, Maustaste **Datenbanken** , und wählen Sie **Schema konvertieren**.  
  
        Sie können auch einzelne Objekte konvertieren. Um ein Objekt zu konvertieren, unabhängig davon, welche Objekte ausgewählt sind, mit der rechten Maustaste in des Objekts, und wählen Sie **Schema konvertieren**.  
  
        Wenn ein Objekt konvertiert wurde, wird es in der Access-Metadaten-Explorer fett formatiert angezeigt.  
  
    -   Zum konvertieren, laden und Migrieren von Schemas und Daten in einem Schritt, Maustaste, Datenbanken, und wählen **konvertieren, laden und migrieren**.  
  
4.  Überprüfen Sie die Meldungen in die **Ausgabe** Bereich und Fehlern und Warnungen in der **Fehlerliste** Bereich.  
  
## <a name="altering-tables-and-indexes"></a>Ändern von Tabellen und Indizes  
Nach der Konvertierung auf Metadaten zugreifen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten und vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, Sie können ändern, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellen und Indizes.  
  
**Zum Ändern von Tabellen- oder Eigenschaften**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer, wählen Sie die Tabelle oder einen Index, die Sie ändern möchten.  
  
2.  Auf der **Tabelle** Registerkarte, klicken Sie auf die Eigenschaft, die Sie verwenden möchten, ändern und dann geben Sie ein oder wählen Sie die neue Einstellung. Sie können z. B. nvarchar(15) in nvarchar(20) ändern, oder wählen Sie ein Kontrollkästchen, um eine Spalte NULL-Werte zulässt.  
  
    Bewegen des Cursors aus der Zelle der geänderten Eigenschaft. Dies ist möglich, durch Klicken auf eine neue Zeile ein, oder Drücken der Tab-Taste.  
  
3.  Klicken Sie auf **Anwenden**.  
  
Sie können jetzt die Änderungen im Code anzeigen, auf die **SQL** Registerkarte.  
  
## <a name="next-step"></a>Nächster Schritt  
Im nächsten Schritt des Migrationsvorgangs [laden konvertierter Datenbankobjekte in SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
