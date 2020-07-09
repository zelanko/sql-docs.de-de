---
title: SQL-Datenermittlung und -klassifizierung | Microsoft-Dokumentation
description: SQL-Datenermittlung und -klassifizierung
documentationcenter: ''
ms.reviewer: vanto
ms.assetid: 89c2a155-c2fb-4b67-bc19-9b4e03c6d3bc
ms.service: sql-database
ms.prod_service: sql-database,sql
ms.custom: security
ms.topic: conceptual
ms.date: 06/10/2020
ms.author: datrigan
author: DavidTrigano
ms.openlocfilehash: 7c23b7faa93281ab34ed4b500d10dfd50e9c8c76
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737041"
---
# <a name="sql-data-discovery-and-classification"></a>SQL-Datenermittlung und -klassifizierung
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Die Datenermittlung und -klassifizierung führt ein neues Tool in [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) für das **Ermitteln**, **Klassifizieren**, **Bezeichnen**  &  **Melden** von vertraulichen Daten in Ihren Datenbanken ein.
Die Ermittlung und Klassifizierung Ihrer sensibelsten Daten (geschäftliche, finanzielle, gesundheitliche usw.) kann im Informationsschutzformat Ihres Unternehmens eine entscheidende Rolle spielen. Sie kann für Folgendes als Infrastruktur gelten:
* Maßnahmen zum Einhalten von Datenschutzstandards.
* Steuern des Zugriffs auf und Verstärken der Sicherheit von Datenbanken oder Spalten, die hochsensible Daten enthalten.

> [!NOTE]
> Die Datenermittlung und -klassifizierung wird **in SQL Server 2012 und höher unterstützt und kann mit [SSMS 17.5](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder höher verwendet werden**. Weitere Informationen zur Datenermittlung und -klassifizierung in Azure SQL-Datenbanken finden Sie unter [Azure SQL-Datenbank – Datenermittlung und -klassifizierung](/azure/sql-database/sql-database-data-discovery-and-classification/).

## <a name="overview"></a><a id="subheading-1"></a>Übersicht
Die Datenermittlung und -klassifizierung führen eine Reihe von erweiterten Diensten ein, und sie bilden ein neues SQL Information Protection-Paradigma für den Schutz von Daten, nicht nur von der Datenbank:

* **Ermittlung und Empfehlungen:** Die Klassifizierungsengine überprüft Ihre Datenbank und identifiziert Spalten, die möglicherweise sensible Daten enthalten. Dann besteht die einfache Möglichkeit zum Überprüfen und Anwenden der geeigneten Empfehlungen zur Klassifizierung und zum manuellen Klassifizieren von Spalten.
* **Bezeichnung:** Sensible Daten können dauerhaft mit Klassifizierungsbezeichnungen gekennzeichnet werden.
* **Sichtbarkeit**: Der Klassifizierungsstatus der Datenbank kann in einem detaillierten Bericht im Portal angezeigt werden, der zwecks Konformität und Überwachung sowie anderer Gründe ausgedruckt oder exportiert werden kann.

## <a name="discovering-classifying--labeling-sensitive-columns"></a><a id="subheading-2"></a>Ermitteln, Klassifizieren und Bezeichnen von sensiblen Spalten
Im folgenden Abschnitt werden die Schritte zum Ermitteln, Klassifizieren und Bezeichnen von Spalten mit sensiblen Daten in Ihrer Datenbank sowie das Anzeigen des aktuellen Klassifizierungsstatus Ihrer Datenbank und das Exportieren von Berichten beschrieben.

Die Klassifizierung umfasst zwei Metadatenattribute:
* Bezeichnungen: Die wichtigsten Klassifizierungsattribute zum Definieren der Vertraulichkeitsstufe der in der Spalte gespeicherten Daten.  
* Informationstypen: Sie bieten zusätzliche Granularität für den Typ der in der Spalte gespeicherten Daten.

**Klassifizieren Ihrer SQL Server-Datenbank:**

1. Stellen Sie in SSMS (SQL Server Management Studio) eine Verbindung zu SQL Server her.

2. Klicken Sie im Objekt-Explorer von SSMS mit der rechten Maustaste auf die Datenbank, die Sie klassifizieren möchten, und wählen Sie dann **Aufgaben** > **Datenermittlung und -klassifizierung** > **Daten klassifizieren…** aus.

   ![Navigationsbereich][0]

3. Die Klassifizierungsengine prüft Ihre Datenbank auf Spalten, die potenziell sensible Daten enthalten, und erstellt eine Liste der **empfohlenen Spaltenklassifizierungen**:

    * Klicken Sie auf das Benachrichtigungsfeld für die Empfehlungen im oberen Rand des Fensters, oder klicken Sie auf den Bereich für Empfehlungen im unteren Rand des Fensters, um eine Liste der empfohlenen Spaltenklassifizierungen anzuzeigen:

        ![Navigationsbereich][2]

        ![Navigationsbereich][3]

    * Überprüfen Sie die Liste der Empfehlungen:
        * Zum Akzeptieren einer Empfehlung für eine bestimmte Spalte aktivieren Sie das Kontrollkästchen in der linken Spalte der entsprechenden Zeile. Sie können auch *alle Empfehlungen* als akzeptiert markieren, indem Sie das Kontrollkästchen im Tabellenkopf der Empfehlungen aktivieren.

        * Sie können auch den empfohlenen Informationstyp und die Vertraulichkeitsbezeichnung mithilfe der Dropdownfelder ändern.        

        ![Navigationsbereich][4]

    * Klicken Sie zum Anwenden Ihrer ausgewählten Empfehlungen auf die blaue Schaltfläche **Accept selected recommendations** (Ausgewählte Änderungen akzeptieren).

        ![Navigationsbereich][5]

4. Alternativ oder zusätzlich zur empfehlungsbasierten Klassifizierung können Sie Spalten auch **manuell klassifizieren**:

    * Klicken Sie im oberen Menü des Fensters auf **Klassifizierung hinzufügen**.

        ![Navigationsbereich][6]

    * Wählen Sie im daraufhin geöffneten Kontextfenster das Schema, die Tabelle und dann die Spalte, die Sie klassifizieren möchten, sowie den Informationstyp und die Vertraulichkeitsbezeichnung aus. Klicken Sie dann auf die Schaltfläche **Klassifizierung hinzufügen** am unteren Rand des Kontextfensters.

        ![Navigationsbereich][7]

5. Klicken Sie im oberen Menü des Fensters auf **Speichern**, um Ihre Klassifizierung zu vervollständigen und die Datenbankspalten dauerhaft mit den neuen Klassifizierungsmetadaten zu bezeichnen (Tag).

    ![Navigationsbereich][8]


6. Klicken Sie im oberen Menü des Fensters auf **Bericht anzeigen**, um einen Bericht mit einer vollständigen Zusammenfassung des Klassifizierungsstatus der Datenbank zu generieren. Sie können auch über SSMS einen Bericht erstellen. Klicken Sie mit der rechten Maustaste auf die Datenbank, in der der Bericht erstellt werden soll, und wählen Sie **Aufgaben** > **Datenermittlung und -klassifizierung** > **Bericht generieren…** aus.

    ![Navigationsbereich][9]

    ![Navigationsbereich][10]

## <a name="manage-information-protection-policy-with-ssms"></a><a id="subheading-3"></a>Verwalten der Information Protection-Richtlinie mit SSMS

Sie können die Information Protection-Richtlinie mit [SSMS 18.4](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder höher verwalten:

1. Stellen Sie in SSMS (SQL Server Management Studio) eine Verbindung zu SQL Server her.

2. Klicken Sie im Objekt-Explorer in SSMS mit der rechten Maustaste auf eine Ihrer Datenbanken, und wählen Sie **Aufgaben** > **Datenermittlung- und -klassifizierung** aus.

   Mithilfe der folgenden Menüoptionen können Sie die Information Protection-Richtlinie verwalten:

* **Information Protection-Richtliniendatei festlegen:** Hier wird die Information Protection-Richtlinie wie in der ausgewählten JSON-Datei definiert verwendet.

* **Information Protection-Richtlinie exportieren:** Hier wird die Information Protection-Richtlinie in eine JSON-Datei exportiert.

* **Information Protection-Richtlinie zurücksetzen:** Hier wird die Information Protection-Richtlinie auf die Information Protection-Standardrichtlinie zurückgesetzt.

> [!IMPORTANT]
> Die Information Protection-Richtliniendatei wird nicht in SQL Server gespeichert.
> Für SSMS wird eine Information Protection-Standardrichtlinie verwendet. Wenn eine benutzerdefinierte Information Protection-Richtlinie nicht angewendet werden kann, kann in SSMS nicht die Standardrichtlinie verwendet werden. Die Datenklassifizierung schlägt fehl. Klicken Sie auf **Information Protection-Richtlinie zurücksetzen**, damit die Standardrichtlinie verwendet, das Problem behoben und die Datenklassifizierung ausgeführt wird.

## <a name="accessing-the-classification-metadata"></a><a id="subheading-4"></a>Zugriff auf Klassifizierungsmetadaten

In SQL Server 2019 wird die Systemkatalogsicht [`sys.sensitivity_classifications`](../system-catalog-views/sys-sensitivity-classifications-transact-sql.md) eingeführt. Diese Sicht gibt Informationstypen und Vertraulichkeitsbezeichnungen zurück. 

> [!NOTE]
> Für diese Sicht ist die Berechtigung **BELIEBIGE VERTRAULICHKEITSKLASSIFIZIERUNG ANZEIGEN** erforderlich. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](https://docs.microsoft.com/sql/relational-databases/security/metadata-visibility-configuration?view=sql-server-ver15).

Fragen Sie für SQL Server 2019-Instanzen `sys.sensitivity_classifications` ab, um alle klassifizierten Spalten mit dazugehörigen Klassifizierungen zu überprüfen. Beispiel: 

```sql
SELECT 
    schema_name(O.schema_id) AS schema_name,
    O.NAME AS table_name,
    C.NAME AS column_name,
    information_type,
    label,
    rank,
    rank_desc
FROM sys.sensitivity_classifications sc
    JOIN sys.objects O
    ON  sc.major_id = O.object_id
    JOIN sys.columns C 
    ON  sc.major_id = C.object_id  AND sc.minor_id = C.column_id
```

In Versionen vor SQL Server 2019 werden die Klassifizierungsmetadaten für Informationstypen und Vertraulichkeitsbezeichnungen in den folgenden erweiterten Eigenschaften gespeichert: 

* `sys_information_type_name`
* `sys_sensitivity_label_name`

Mithilfe der Katalogsicht für erweiterte Eigenschaften ([`sys.extended_properties`](../system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)) können Sie auf die Metadaten zugreifen.

Bei Instanzen von SQL Server 2017 und älteren Versionen gibt das folgende Codebeispiel alle klassifizierten Spalten mit der jeweiligen Klassifizierung zurück:

```sql
SELECT
    schema_name(O.schema_id) AS schema_name,
    O.NAME AS table_name,
    C.NAME AS column_name,
    information_type,
    sensitivity_label 
FROM
    (
        SELECT
            IT.major_id,
            IT.minor_id,
            IT.information_type,
            L.sensitivity_label 
        FROM
        (
            SELECT
                major_id,
                minor_id,
                value AS information_type 
            FROM sys.extended_properties 
            WHERE NAME = 'sys_information_type_name'
        ) IT 
        FULL OUTER JOIN
        (
            SELECT
                major_id,
                minor_id,
                value AS sensitivity_label 
            FROM sys.extended_properties 
            WHERE NAME = 'sys_sensitivity_label_name'
        ) L 
        ON IT.major_id = L.major_id AND IT.minor_id = L.minor_id
    ) EP
    JOIN sys.objects O
    ON  EP.major_id = O.object_id 
    JOIN sys.columns C 
    ON  EP.major_id = C.object_id AND EP.minor_id = C.column_id
```

## <a name="manage-classifications"></a><a id="subheading-5"></a>Verwalten von Klassifizierungen

# <a name="t-sql"></a>[T-SQL](#tab/t-sql)
Mit T-SQL können Sie Spaltenklassifizierungen hinzufügen/entfernen sowie alle Klassifizierungen für die gesamte Datenbank abrufen.

- Hinzufügen/Aktualisieren der Klassifizierung einer oder mehrerer Spalten: [VERTRAULICHKEITSKLASSIFIZIERUNG HINZUFÜGEN](https://docs.microsoft.com/sql/t-sql/statements/add-sensitivity-classification-transact-sql)
- Entfernen der Klassifizierung einer oder mehrerer Spalten: [VERTRAULICHKEITSKLASSIFIZIERUNG VERWERFEN](https://docs.microsoft.com/sql/t-sql/statements/drop-sensitivity-classification-transact-sql)

# <a name="powershell-cmdlet"></a>[PowerShell-Cmdlet](#tab/sql-powelshell)
Sie können das Power Shell-Cmdlet verwenden, um Spaltenklassifizierungen hinzuzufügen/zu entfernen sowie alle Klassifizierungen abzurufen und Empfehlungen für die gesamte Datenbank zu erhalten.

- [Get-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlSensitivityClassification?view=sqlserver-ps)
- [Get-SqlSensitivityRecommendations](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlSensitivityRecommendations?view=sqlserver-ps)
- [Set-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Set-SqlSensitivityClassification?view=sqlserver-ps)
- [Remove-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Remove-SqlSensitivityClassification?view=sqlserver-ps)

---

## <a name="next-steps"></a><a id="subheading-6"></a>Nächste Schritte

Weitere Informationen zur Datenermittlung und -klassifizierung in Azure SQL-Datenbanken finden Sie unter [Azure SQL-Datenbank – Datenermittlung und -klassifizierung](https://go.microsoft.com/fwlink/?linkid=866265).

Ziehen Sie in Betracht, Ihre sensiblen Spalten durch Anwenden von Sicherheitsmechanismen auf der Spaltenebene zu schützen:

* [Dynamische Datenmaskierung](https://docs.microsoft.com/sql/relational-databases/security/dynamic-data-masking) zum Verbergen der verwendeten sensiblen Spalten.
* [Immer verschlüsselt](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) zum Verschlüsseln der sensiblen Spalten im Ruhezustand.

<!--Anchors-->
[SQL Data Discovery & Classification overview]: #subheading-1
[Discovering, classifying & labeling sensitive columns]: #subheading-2
[Manage information protection policy with SSMS]: #subheading-3
[Accessing the classification metadata]: #subheading-4
[Manage classifications]: #subheading-5
[Next Steps]: #subheading-6

<!--Image references-->

[0]: ./media/sql-data-discovery-and-classification/0-data-classification-explorer.png
[2]: ./media/sql-data-discovery-and-classification/2-recommendations-notification-box.png
[3]: ./media/sql-data-discovery-and-classification/3-recommendations-panel.png
[4]: ./media/sql-data-discovery-and-classification/4-recommendations.png
[5]: ./media/sql-data-discovery-and-classification/5-accept-recommendations-button.png
[6]: ./media/sql-data-discovery-and-classification/6-add-classification-button.png
[7]: ./media/sql-data-discovery-and-classification/7-manual-classification.png
[8]: ./media/sql-data-discovery-and-classification/8-save.png
[9]: ./media/sql-data-discovery-and-classification/9-view-report.png
[10]: ./media/sql-data-discovery-and-classification/10-report.png
