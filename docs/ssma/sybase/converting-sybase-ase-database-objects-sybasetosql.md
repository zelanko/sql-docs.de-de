---
title: Konvertieren von Sybase ASE-Datenbankobjekten (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Converting Database Objects
ms.assetid: 509cb65d-2f54-427a-83d7-37919cc4e3e3
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0ab4bb272f83a16cf8f5be009424499bc4e054c4
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40392302"
---
# <a name="converting-sap-ase-database-objects-sybasetosql"></a>Konvertieren von SAP ASE-Datenbankobjekten (SybaseToSQL)
Nachdem Sie in SAP Adaptive Server Enterprise (ASE) eine Verbindung hergestellt haben, verbunden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL und Projekt festlegen und Optionen für die Zuordnung von Daten, können Sie Datenbankobjekte SAP Adaptive Server Enterprise (ASE) konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank -Objekte.  
  
## <a name="the-conversion-process"></a>Konvertierungsprozess  
Die Objektdefinitionen aus der ASE verwendet, konvertiert diese in ähnlichen konvertieren Datenbankobjekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte, und lädt dann diese Informationen in der SSMA-Metadaten. Er lädt nicht die Informationen in die Instanz der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL. Sie können dann die Objekte und deren Eigenschaften anzeigen, mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Metadaten-Explorer.
  
Bei der Konvertierung gibt SSMA monolog-Meldungen an die Ausgabe im Bereich und die Fehlermeldungen in der **Fehlerliste** Bereich. Verwenden Sie die Ausgabe- und Informationen, um festzustellen, ob Sie so ändern Sie Ihre ASE-Datenbanken oder den Konvertierungsprozess Ihrer, um die gewünschte Konvertierungsergebnisse erhalten haben.  
  
## <a name="setting-conversion-options"></a>Festlegen von Optionen  
Lesen Sie vor dem Konvertieren von Objekten, die die Projektoptionen für die Konvertierung in den **Projekteinstellungen** Dialogfeld. Verwenden Sie das Dialogfeld zu öffnen, können Sie festlegen, wie der SSMA-Funktionen und globale Variablen konvertiert. Weitere Informationen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
## <a name="converting-ase-database-objects"></a>Konvertieren die ASE-Datenbankobjekten  
Klicken Sie zum ASE-Datenbankobjekten zu konvertieren, wählen Sie zuerst die Objekte, die Sie konvertieren möchten, und lassen Sie dann die SSMA, die die Konvertierung nicht ausgeführt. Anzeigen von ausgehenden Nachrichten bei der Konvertierung auf den **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**So konvertieren Sie die ASE-Objekte in SQL Server oder SQL Azure-syntax**  
  
1.  In der Sybase-Metadaten-Explorer, erweitern Sie die ASE-Server, und dann **Datenbanken**.  
  
2.  Wählen Sie Objekte zu konvertieren:  
  
    -   Um alle Datenbanken zu konvertieren, wählen Sie das Kontrollkästchen neben **Datenbanken**.  
  
    -   Klicken Sie zum konvertieren, oder lassen Sie eine Datenbank, aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Klicken Sie zum konvertieren, oder lassen Sie die einzelnen Schemas aus, erweitern Sie die Datenbank, erweitern Sie **Schemas**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben dem Schema.  
  
    -   Konvertieren, oder lassen Sie eine Kategorie von Objekten, erweitern Sie das Schema, und aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben der Kategorie.  
  
    -   Konvertieren, oder lassen Sie einzelne Objekte, erweitern Sie die Kategorieordner, und aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt.  
  
3.  Um alle ausgewählten Objekte zu konvertieren, Maustaste **Datenbanken**, und wählen Sie dann **Schema konvertieren**.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten durch Rechtsklick auf das Objekt oder den enthaltenden Ordner aus, und wählen Sie dann konvertieren **Schema konvertieren**.  
  
> [!NOTE]  
> Einige der SAP ASE Systemfunktionen stimmen die entsprechenden SQL Server-System-Funktionen Verhalten nicht genau überein. Um das SAP ASE-Verhalten zu emulieren, generiert SSMA benutzerdefinierte Funktionen in der konvertierten SQL Server-Datenbank unter einem Schema namens "s2ss". Je nach den projekteinstellungen werden einige der Funktionen, SQL Server-System mit diesen emulierten Funktionen ersetzt. SSMA erstellt die folgenden benutzerdefinierten Funktionen:  
  
||||  
|-|-|-|  
|**char_length_nvarchar**|**index_colorder**|**ssma_datepart**|  
|**char_length_varchar**|**INTTOHEX**|**substring_nvarchar**|  
|**charindex_nvarchar**|**ssma_datediff**|**substring_varbinary**|  
|**charindex_varchar**|**hextoint**|**substring_varchar**|  
|**ulowsurr**|**to_unichar**|**ssma_current_time**|  
|**uhighsurr**|||  
  
## <a name="objects-not-supported-in-azure-sql"></a>In Azure SQL nicht unterstützte Objekte  
Die folgenden T-SQL-Schlüsselwörter werden von SSMA für SAP ASE verwendet, während der Konvertierung in einer lokalen SQL Server, aber diese Schlüsselwörter werden von SQL Azure T-SQL-Syntax nicht unterstützt:  
  
||||  
|-|-|-|  
|CHECKPOINT|CREATE/ALTER/DROP DEFAULT|CREATE/DROP RULE|  
|DBCC TRACEOFF|DBCC TRACEON|GRANT, REVOKE ODER DENY ALL|  
|KILL|READTEXT|SELECT INTO|  
|SET OFFSETS|SETUSER|SHUTDOWN|  
|WRITETEXT|||  
  
## <a name="viewing-conversion-problems"></a>Probleme bei der Konvertierung anzeigen  
Einige SAP ASE-Objekte können nicht konvertiert werden. Sie können die Abschlussraten für den Erfolg bestimmen, durch Anzeigen der Zusammenfassung Konvertierungsbericht.  
  
**Zum Anzeigen eines Übersichtsberichts**  
  
1.  Wählen Sie in der Sybase-Metadaten-Explorer, **Datenbanken**.  
  
2.  Wählen Sie im rechten Bereich die **Bericht** Registerkarte.  
  
    Dieser Bericht zeigt die Zusammenfassung Bewertungsbericht für alle Datenbankobjekte, die bewertet oder konvertiert wurden. Sie können auch einen Zusammenfassungsbericht für einzelne Objekte anzeigen:  
  
    -   Um den Bericht für eine einzelne Datenbank anzuzeigen, wählen Sie die Datenbank in einer Sybase-Metadaten-Explorer aus.  
  
    -   Um den Bericht für ein einzelnes Datenbankobjekt anzuzeigen, wählen Sie das Objekt in der Sybase-Metadaten-Explorer aus. Objekten, die Probleme bei der Konvertierung zu haben, ist ein rotes Fehlersymbol.  
  
Für Objekte, die Konvertierung fehlgeschlagen ist, können Sie die Syntax anzeigen, die die Konvertierungsfehler bewirkt, dass geführt haben.  
  
**Probleme beim Konvertieren der einzelnen anzeigen**  
  
1.  Erweitern Sie in der Sybase-Metadaten-Explorer, **Datenbanken**.  
  
2.  Erweitern Sie die Datenbank, die ein rotes Fehlersymbol zeigt.  
  
3.  Erweitern Sie die **Schemas** Ordner, und erweitern Sie dann das Schema, das ein rotes Fehlersymbol zeigt.  
  
4.  Erweitern Sie einen Ordner mit einem roten Fehlersymbol, unter dem Schema.  
  
5.  Wählen Sie das Objekt mit einem roten Fehlersymbol.  
  
6.  Wählen Sie im rechten Bereich die **Bericht** Registerkarte.  
  
7.  Am oberen Rand der **Bericht** Registerkarte wird eine Dropdown-Liste. Wenn die Liste zeigt **Statistiken**, ändern Sie die Auswahl auf **Quelle**.  
  
    SSMA wird der Quellcode und verschiedene Schaltflächen direkt über dem Code angezeigt.  
  
8.  Wählen Sie **nächsten Problem**, ein rotes Fehlersymbol mit einem Pfeil nach rechts zeigenden.  
  
    SSMA für SAP ASE werden den ersten problematisch Quellcode hervorgehoben, die in das aktuelle Objekt gefunden.  
  
Für jedes Element, das nicht konvertiert werden konnten, müssen Sie bestimmen, was Sie mit diesem Objekt tun möchten:  
  
-   Sie können den Quellcode für die Prozeduren und Trigger bearbeiten, auf die **SQL** Registerkarte.  
  
-   Sie können das SAP ASE-Objekt zum Entfernen oder Überarbeiten problematischen Code ändern. Um den aktualisierten Code in SSMA laden zu können, müssen Sie die Metadaten zu aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Sie können das Objekt von der Migration ausschließen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Metadaten-Explorer und Sybase-Metadaten-Explorer, deaktivieren Sie das Kontrollkästchen neben dem Element vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL und Migrieren von Daten von SAP ASE.  
  
## <a name="next-steps"></a>Nächste Schritte  
Im nächsten Schritt des Migrationsvorgangs [laden konvertiert-Datenbankobjekte in SQLServer / SQL Azure (SybaseToSQL)](http://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von SAP ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
