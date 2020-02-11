---
title: Datenbankobjekte werden umgerechnet (accesstosql) | Microsoft-Dokumentation
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
ms.openlocfilehash: 56c55dbc5df61bfdb9013e505335af16fccbeecd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006627"
---
# <a name="converting-access-database-objects-accesstosql"></a>Datenbankobjekte werden umgerechnet (accesstosql)
Nachdem Sie Access-Datenbanken hinzugefügt und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Verbindung mit oder SQL Azure hergestellt haben, zeigt SSMA Metadaten für den Zugriff und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Datenbankobjekten an. Sie können jetzt auf Datenbankobjekte zugreifen auswählen und dann die Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Schemas konvertieren.  
  
## <a name="the-conversion-process"></a>Der Konvertierungsprozess  
Beim Konvertieren von Datenbankobjekten werden die Objekt Definitionen aus den Zugriffs Metadaten konvertiert, [!INCLUDE[tsql](../../includes/tsql-md.md)] in eine entsprechende Syntax konvertiert und dann in das Projekt geladen. Anschließend können Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -oder-SQL Azure Objekte und deren Eigenschaften mithilfe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von oder SQL Azure Metadaten-Explorer anzeigen.  
  
> [!IMPORTANT]  
> Beim wandeln von Objekten werden die Objekte nicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in oder SQL Azure erstellt. Die Objekt Definitionen werden nur konvertiert, und die Informationen werden im SSMA-Projekt gespeichert.  
  
Während der Konvertierung druckt SSMA den Status im Ausgabebereich und Fehler-, Warn-und Informationsmeldungen in den Fehlerliste Bereich. Verwenden Sie diese Informationen, um zu bestimmen, ob Sie die Zugriffs Datenbanken oder den Konvertierungsprozess ändern müssen, um die gewünschten Konvertierungs Ergebnisse zu erhalten. Sie können auch die Informationen im Thema [Vorbereiten von Access-Datenbanken für die Migration](preparing-access-databases-for-migration-accesstosql.md) verwenden, um zu bestimmen, was nicht konvertiert wird.  
  
## <a name="setting-conversion-options"></a>Festlegen von Konvertierungsoptionen  
Überprüfen Sie vor dem Konvertieren von Objekten die Projekt Konvertierungsoptionen im Dialogfeld **Projekteinstellungen** . Mit diesem Dialogfeld können Sie festlegen, wie SSMA indizierte Memo Spalten, Primärschlüssel, Fremdschlüssel Einschränkungen, Zeitstempel und Tabellen ohne Indizes konvertiert. Weitere Informationen finden Sie unter [Projekteinstellungen (Konvertierung)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
## <a name="conversion-results"></a>Konvertierungs Ergebnisse  
In der folgenden Tabelle wird gezeigt, welche Zugriffs Objekte konvertiert werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und die resultierenden Objekte oder SQL Azure-Objekte:  
  
|Access-Objekt|Resultierende SQL Server Objekt|  
|-----------------|-------------------------------|  
|table|table|  
|column|column|  
|Index|Index|  
|Fremdschlüssel|Fremdschlüssel|  
|query|Ansicht<br /><br />Die meisten SELECT-Abfragen werden in Sichten konvertiert. Andere Abfragen, z. b. Update Abfragen, werden nicht migriert.<br /><br />SELECT-Abfragen, die Parameter akzeptieren, werden nicht konvertiert, und es handelt sich nicht um Kreuz Registerkarten Abfragen.|  
|report|nicht konvertiert|  
|form|nicht konvertiert|  
|Makro|nicht konvertiert|  
|Mond|nicht konvertiert|  
|Standardwert|Standardwert|  
|Spalten Eigenschaft mit der Länge NULL zulassen|Check-Einschränkung|  
|Spalten Validierungs Regel|Check-Einschränkung|  
|Tabellen Validierungs Regel|Check-Einschränkung|  
|Primärschlüssel|Primärschlüssel|  
  
## <a name="converting-access-objects"></a>Umstellen von Zugriffs Objekten  
Zum Konvertieren von Access-Datenbankobjekten müssen Sie zuerst die Objekte auswählen, die Sie konvertieren möchten, und SSMA dann die Konvertierung durchführen. Wenn Sie während der Konvertierung Ausgabemeldungen anzeigen möchten, wählen Sie im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So können Sie Access-Datenbankobjekte auswählen und in SQL Server-oder SQL Azure-Syntax konvertieren**  
  
1.  Erweitern Sie in Access Metadata Explorer den Eintrag **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
2.  Führen Sie einen oder mehrere der folgenden Schritte aus:  
  
    -   Aktivieren Sie das Kontrollkästchen neben **Datenbanken**, um alle Datenbanken zu konvertieren.  
  
    -   Aktivieren oder deaktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um einzelne Datenbanken zu konvertieren oder auszulassen.  
  
    -   Wenn Sie Abfragen konvertieren oder weglassen möchten, erweitern Sie die Datenbank, und aktivieren oder deaktivieren Sie das Kontrollkästchen **Abfragen** .  
  
    -   Zum Konvertieren oder weglassen einzelner Tabellen erweitern Sie die Datenbank, erweitern Sie **Tabellen**, und aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
3.  Führen Sie eines der folgenden Verfahren aus:  
  
    -   Zum Konvertieren von Schemas klicken Sie mit der rechten Maustaste auf **Datenbanken** , und wählen Sie **Schema konvertieren**  
  
        Sie können auch einzelne Objekte konvertieren. Klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie **Schema konvertieren**aus, um ein Objekt zu konvertieren, unabhängig von den ausgewählten Objekten.  
  
        Wenn ein Objekt konvertiert wurde, wird es Fett in Access Metadata Explorer angezeigt.  
  
    -   Wenn Sie Schemas und Daten in einem Schritt konvertieren, laden und migrieren möchten, klicken Sie mit der rechten Maustaste auf Datenbanken, und wählen Sie **konvertieren, laden und Migrieren**aus.  
  
4.  Überprüfen Sie die Meldungen im **Ausgabe** Bereich und alle Fehler und Warnungen im **Fehlerliste** Bereich.  
  
## <a name="altering-tables-and-indexes"></a>Ändern von Tabellen und Indizes  
Nachdem Sie die Zugriffs Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Metadaten konvertiert haben und bevor Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure laden, können Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen und Indizes ändern oder SQL Azure.  
  
**So ändern Sie Tabellen-oder Index Eigenschaften**  
  
1.  Wählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie in oder SQL Azure metadatenexplorer die Tabelle oder den Index aus, die Sie ändern möchten.  
  
2.  Klicken Sie auf der Registerkarte **Tabelle** auf die Eigenschaft, die Sie ändern möchten, und geben Sie dann die neue Einstellung ein. Sie können z. b. nvarchar (15) in nvarchar (20) ändern oder ein Kontrollkästchen aktivieren, um eine Tabellenspalte auf NULL zu setzen.  
  
    Bewegen Sie den Cursor aus der geänderten Eigenschaften Zelle. Klicken Sie hierzu auf eine andere Zeile, oder drücken Sie die Tab-Taste.  
  
3.  Klicken Sie auf **Anwenden**.  
  
Nun können Sie die Änderungen im Code auf der Registerkarte " **SQL** " anzeigen.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs ist das [Laden von konvertierten Datenbankobjekten in SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
