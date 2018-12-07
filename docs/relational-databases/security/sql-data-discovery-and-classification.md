---
title: SQL-Datenermittlung und -klassifizierung | Microsoft-Dokumentation
description: SQL-Datenermittlung und -klassifizierung
documentationcenter: ''
ms.reviewer: carlrab
ms.assetid: 89c2a155-c2fb-4b67-bc19-9b4e03c6d3bc
ms.service: sql-database
ms.prod_service: sql-database,sql
ms.custom: security
ms.topic: conceptual
ms.date: 02/13/2018
ms.author: giladm
author: giladm
manager: shaik
ms.openlocfilehash: 18495f81289981d4ce5a72ac943150bfea4c4f3d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539120"
---
# <a name="sql-data-discovery-and-classification"></a>SQL-Datenermittlung und -klassifizierung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die Datenermittlung und -klassifizierung führt ein neues Tool in SSMS (SQL Server Management Studio) für das **Ermitteln**, **Klassifizieren**, **Bezeichnen** & **Melden** von sensiblen Daten in Ihren Datenbanken ein.
Die Ermittlung und Klassifizierung Ihrer sensibelsten Daten (geschäftliche, finanzielle, gesundheitliche usw.) kann im Informationsschutzformat Ihres Unternehmens eine entscheidende Rolle spielen. Sie kann für Folgendes als Infrastruktur gelten:
* Maßnahmen zum Einhalten von Datenschutzstandards.
* Steuern des Zugriffs auf und Verstärken der Sicherheit von Datenbanken oder Spalten, die hochsensible Daten enthalten.

> [!NOTE]
> Die Datenermittlung und -klassifizierung werden **in SQL Server 2008 und höher unterstützt**. Weitere Informationen zur Datenermittlung und -klassifizierung in Azure SQL-Datenbanken finden Sie unter [Azure SQL-Datenbank – Datenermittlung und -klassifizierung](https://go.microsoft.com/fwlink/?linkid=866265).

## <a id="subheading-1"></a>Übersicht
Die Datenermittlung und -klassifizierung führen eine Reihe von erweiterten Diensten ein, und sie bilden ein neues SQL Information Protection-Paradigma für den Schutz von Daten, nicht nur von der Datenbank:
* **Ermittlung und Empfehlungen:** Die Klassifizierungsengine überprüft Ihre Datenbank und identifiziert Spalten, die möglicherweise sensible Daten enthalten. Dann besteht die einfache Möglichkeit zum Überprüfen und Anwenden der geeigneten Empfehlungen zur Klassifizierung und zum manuellen Klassifizieren von Spalten.
* **Bezeichnung:** Sensible Daten können dauerhaft mit Klassifizierungsbezeichnungen gekennzeichnet werden.
* **Sichtbarkeit**: Der Klassifizierungsstatus der Datenbank kann in einem detaillierten Bericht im Portal angezeigt werden, der zwecks Konformität und Überwachung sowie anderer Gründe ausgedruckt oder exportiert werden kann.

## <a id="subheading-2"></a>Ermitteln, Klassifizieren und Bezeichnen von sensiblen Spalten
Im folgenden Abschnitt werden die Schritte zum Ermitteln, Klassifizieren und Bezeichnen von Spalten mit sensiblen Daten in Ihrer Datenbank sowie das Anzeigen des aktuellen Klassifizierungsstatus Ihrer Datenbank und das Exportieren von Berichten beschrieben.

Die Klassifizierung umfasst zwei Metadatenattribute:
* Bezeichnungen: Die wichtigsten Klassifizierungsattribute zum Definieren der Vertraulichkeitsstufe der in der Spalte gespeicherten Daten.  
* Informationstypen: Sie bieten zusätzliche Granularität für den Typ der in der Spalte gespeicherten Daten.

<br>
**Klassifizieren Ihrer SQL Server-Datenbank:**

1. Stellen Sie in SSMS (SQL Server Management Studio) eine Verbindung zu SQL Server her.

2. Führen Sie im Objekt-Explorer von SSMS einen Rechtsklick auf die Datenbank aus, die Sie klassifizieren möchten, und wählen Sie dann **Tasks** > **Classify Data...** (Aufgaben > Daten klassifizieren...) aus.

    ![Navigationsbereich][1]

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


6. Klicken Sie im oberen Menü des Fensters auf **Bericht anzeigen**, um einen Bericht mit einer vollständigen Zusammenfassung des Klassifizierungsstatus der Datenbank zu generieren.

    ![Navigationsbereich][9]

    ![Navigationsbereich][10]


## <a id="subheading-3"></a>Zugriff auf Klassifizierungsmetadaten

Die Klassifizierungsmetadaten für *Informationstypen* und *Vertraulichkeitsstufen* werden in den folgenden erweiterten Eigenschaften gespeichert: 
* sys_information_type_name
* sys_sensitivity_label_name

Sie können mit der Ansicht des Katalogs der erweiterten Eigenschaften [sys.extended_properties](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties) auf die Metadaten zugreifen.

Das folgenden Codebeispiel gibt alle klassifizierten Spalten mit der jeweiligen Klassifizierung zurück:

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

## <a id="subheading-4"></a>Nächste Schritte

Weitere Informationen zur Datenermittlung und -klassifizierung in Azure SQL-Datenbanken finden Sie unter [Azure SQL-Datenbank – Datenermittlung und -klassifizierung](https://go.microsoft.com/fwlink/?linkid=866265).

Ziehen Sie in Betracht, Ihre sensiblen Spalten durch Anwenden von Sicherheitsmechanismen auf der Spaltenebene zu schützen:

* [Dynamische Datenmaskierung](https://docs.microsoft.com/sql/relational-databases/security/dynamic-data-masking) zum Verbergen der verwendeten sensiblen Spalten.
* [Immer verschlüsselt](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) zum Verschlüsseln der sensiblen Spalten im Ruhezustand.

<!--Anchors-->
[SQL Data Discovery & Classification overview]: #subheading-1
[Discovering, classifying & labeling sensitive columns]: #subheading-2
[Accessing the classification metadata]: #subheading-3
[Next Steps]: #subheading-4

<!--Image references-->
[1]: ./media/sql-data-discovery-and-classification/1_data_classification_explorer_menu.png
[2]: ./media/sql-data-discovery-and-classification/2_recommendations_notification_box.png
[3]: ./media/sql-data-discovery-and-classification/3_recommendations_panel.png
[4]: ./media/sql-data-discovery-and-classification/4_recommendations.png
[5]: ./media/sql-data-discovery-and-classification/5_accept_recommendations_button.png
[6]: ./media/sql-data-discovery-and-classification/6_add_classification_button.png
[7]: ./media/sql-data-discovery-and-classification/7_manual_classification.png
[8]: ./media/sql-data-discovery-and-classification/8_save.png
[9]: ./media/sql-data-discovery-and-classification/9_view_report.png
[10]: ./media/sql-data-discovery-and-classification/10_report.png
