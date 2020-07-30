---
title: Umstellen von Sybase ASE-Datenbankobjekten (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Converting Database Objects
ms.assetid: 509cb65d-2f54-427a-83d7-37919cc4e3e3
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0785c3ecc6335494ed4c34f8919e3ad766236631
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394512"
---
# <a name="converting-sap-ase-database-objects-sybasetosql"></a>Umstellen von SAP ASE-Datenbankobjekten (sybaseto SQL)
Nachdem Sie eine Verbindung mit SAP Adaptive Server Enterprise (ASE) hergestellt, eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL hergestellt und Projekt-und Daten Zustellungs Optionen festgelegt haben, können Sie SAP Adaptive Server Enterprise-Datenbankobjekte (ASE) in- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankobjekte konvertieren  
  
## <a name="the-conversion-process"></a>Der Konvertierungsprozess  
Beim Konvertieren von Datenbankobjekten werden die Objekt Definitionen aus ASE konvertiert, in ähnliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Objekte konvertiert und diese Informationen dann in die SSMA-Metadaten geladen. Die Informationen werden nicht in die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL geladen. Anschließend können Sie die Objekte und deren Eigenschaften mithilfe von oder dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL-metadatenexplorer anzeigen.
  
Während der Konvertierung druckt SSMA Ausgabemeldungen im Ausgabebereich und Fehlermeldungen in den **Fehlerliste** Bereich. Bestimmen Sie anhand der Ausgabe-und Fehlerinformationen, ob Sie Ihre ASE-Datenbanken oder den Konvertierungsprozess ändern müssen, um die gewünschten Konvertierungs Ergebnisse zu erhalten.  
  
## <a name="setting-conversion-options"></a>Festlegen von Konvertierungsoptionen  
Überprüfen Sie vor dem Konvertieren von Objekten die Projekt Konvertierungsoptionen im Dialogfeld **Projekteinstellungen** . Mit diesem Dialogfeld können Sie festlegen, wie SSMA Funktionen und globale Variablen konvertiert. Weitere Informationen finden Sie unter [Project Settings &#40;Conversion&#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
## <a name="converting-ase-database-objects"></a>Umstellen von ASE-Datenbankobjekten  
Zum Konvertieren von ASE-Datenbankobjekten wählen Sie zunächst die Objekte aus, die Sie konvertieren möchten, und lassen Sie dann die Konvertierung von SSMA durchführen. Wenn Sie während der Konvertierung Ausgabemeldungen anzeigen möchten, wählen Sie im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So konvertieren Sie ASE-Objekte in SQL Server-oder SQL Azure-Syntax**  
  
1.  Erweitern Sie im Sybase-metadatenexplorer den ASE-Server, und erweitern Sie dann **Datenbanken**.  
  
2.  Zu konvertierende Objekte auswählen:  
  
    -   Aktivieren Sie das Kontrollkästchen neben **Datenbanken**, um alle Datenbanken zu konvertieren.  
  
    -   Aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um eine Datenbank zu konvertieren oder auszulassen.  
  
    -   Wenn Sie einzelne Schemas konvertieren oder weglassen möchten, erweitern Sie die Datenbank, erweitern Sie **Schemas**, und aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben dem Schema.  
  
    -   Wenn Sie eine Kategorie von Objekten konvertieren oder weglassen möchten, erweitern Sie das Schema, und aktivieren oder deaktivieren Sie dann das Kontrollkästchen neben der Kategorie.  
  
    -   Wenn Sie einzelne Objekte konvertieren oder weglassen möchten, erweitern Sie den Ordner Category, und aktivieren oder deaktivieren Sie das Kontrollkästchen neben dem Objekt.  
  
3.  Zum Konvertieren aller ausgewählten Objekte klicken Sie mit der rechten Maustaste auf **Datenbanken**, und wählen Sie dann **Schema konvertieren**aus.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten konvertieren, indem Sie mit der rechten Maustaste auf das Objekt oder den enthaltenden Ordner klicken und dann **Schema konvertieren**auswählen.  
  
> [!NOTE]  
> Einige der SAP ASE-Systemfunktionen entsprechen nicht exakt den entsprechenden SQL Server Systemfunktionen im Verhalten. Um das SAP ASE-Verhalten zu emulieren, generiert SSMA benutzerdefinierte Funktionen in der konvertierten SQL Server Datenbank unter einem Schema, das als 2SS "bezeichnet wird. Abhängig von den Projekteinstellungen werden einige der SQL Server Systemfunktionen durch diese emulierten Funktionen ersetzt. SSMA erstellt die folgenden benutzerdefinierten Funktionen:  

:::row:::
    :::column:::
        **char_length_nvarchar**  
        **char_length_varchar**  
        **charindex_nvarchar**  
        **charindex_varchar**  
        **hexentyp**  
        **index_colorder**  
    :::column-end:::
    :::column:::
        **intum Hex**  
        **ssma_current_time**  
        **ssma_datediff**  
        **ssma_datepart**  
        **substring_nvarchar**  
        **substring_varbinary**  
    :::column-end:::
    :::column:::
        **substring_varchar**  
        **to_unichar**  
        **uhighsurr**  
        **ulowsurr**  
    :::column-end:::
:::row-end:::

## <a name="objects-not-supported-in-azure-sql"></a>Nicht unterstützte Objekte in Azure SQL  
Die folgenden t-SQL-Schlüsselwörter werden von SSMA für SAP ASE während der Konvertierung in SQL Server lokal verwendet. diese Schlüsselwörter werden jedoch von SQL Azure T-SQL-Syntax nicht unterstützt:  

:::row:::
    :::column:::
        CHECKPOINT  
        CREATE/ALTER/DROP DEFAULT  
        CREATE/DROP RULE  
        DBCC TRACEOFF  
        DBCC TRACEON  
    :::column-end:::
    :::column:::
        GRANT/REVOKE/DENY ALL  
        KILL  
        READTEXT  
        SELECT INTO  
        SET OFFSETS  
    :::column-end:::
    :::column:::
        SETUSER  
        SHUTDOWN  
        WRITETEXT  
    :::column-end:::
:::row-end:::

## <a name="viewing-conversion-problems"></a>Anzeigen von Konvertierungs Problemen  
Einige SAP ASE-Objekte werden möglicherweise nicht konvertiert. Sie können die Erfolgsraten der Konvertierung ermitteln, indem Sie den Zusammenfassungs Bericht für die Zusammenfassung anzeigen  
  
**So zeigen Sie einen Zusammenfassungs Bericht an**  
  
1.  Wählen Sie im Sybase-metadatenexplorer **Datenbanken**aus.  
  
2.  Wählen Sie im rechten Bereich die Registerkarte **Bericht** aus.  
  
    Dieser Bericht zeigt den Zusammenfassungs Bewertungsbericht für alle Datenbankobjekte an, die bewertet oder konvertiert wurden. Sie können auch einen Zusammenfassungs Bericht für einzelne Objekte anzeigen:  
  
    -   Um den Bericht für eine einzelne Datenbank anzuzeigen, wählen Sie die Datenbank im Sybase-metadatenexplorer aus.  
  
    -   Um den Bericht für ein einzelnes Datenbankobjekt anzuzeigen, wählen Sie das Objekt im Sybase-metadatenexplorer aus. Bei Objekten, die Konvertierungsprobleme aufweisen, wird ein rotes Fehler Symbol angezeigt.  
  
Bei Objekten, die nicht erfolgreich konvertiert werden konnten, können Sie die Syntax anzeigen, die zu einem Konvertierungs Fehler geführt hat.  
  
**So zeigen Sie einzelne Konvertierungsprobleme an**  
  
1.  Erweitern Sie im Sybase-metadatenexplorer den Eintrag **Datenbanken**.  
  
2.  Erweitern Sie die Datenbank, in der ein rotes Fehler Symbol angezeigt wird.  
  
3.  Erweitern Sie den Ordner **Schemas** , und erweitern Sie dann das Schema, das ein rotes Fehler Symbol anzeigt.  
  
4.  Erweitern Sie unter dem Schema einen Ordner mit einem roten Fehler Symbol.  
  
5.  Wählen Sie das Objekt mit einem roten Fehler Symbol aus.  
  
6.  Wählen Sie im rechten Bereich die Registerkarte **Bericht** aus.  
  
7.  Am oberen Rand der Registerkarte **Bericht** befindet sich eine Dropdown Liste. Wenn in der Liste **Statistiken**angezeigt werden, ändern Sie die Auswahl in **Quelle**.  
  
    SSMA zeigt den Quellcode und mehrere Schaltflächen direkt oberhalb des Codes an.  
  
8.  Wählen Sie **nächstes Problem**aus, ein rotes Fehler Symbol, wenn ein Pfeil nach rechts zeigt.  
  
    SSMA für SAP ASE hebt den ersten problematischen Quell Code hervor, der im aktuellen-Objekt gefunden wird.  
  
Sie müssen für jedes Element, das nicht konvertiert werden konnte, bestimmen, was Sie mit diesem Objekt tun möchten:  
  
-   Sie können den Quellcode für Prozeduren und Trigger auf der Registerkarte " **SQL** " bearbeiten.  
  
-   Sie können das SAP ASE-Objekt ändern, um problematischen Code zu entfernen oder zu überarbeiten. Um den aktualisierten Code in SSMA zu laden, müssen Sie die Metadaten aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SAP ASE &#40;sybaseto SQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Sie können das Objekt von der Migration ausschließen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Deaktivieren Sie in oder im Azure SQL-metadatenexplorer und im Sybase-metadatenexplorer das Kontrollkästchen neben dem Element, bevor Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL laden und Daten aus SAP ASE migrieren.  
  
## <a name="next-steps"></a>Nächste Schritte  
Der nächste Schritt des Migrations Vorgangs besteht darin, [konvertierte Datenbankobjekte in SQL Server/SQL Azure (sybasedesql) zu laden](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von SAP ASE-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
