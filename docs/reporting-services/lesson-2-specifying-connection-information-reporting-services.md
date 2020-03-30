---
title: 'Lektion 2: Angeben von Verbindungsinformationen (Reporting Services) | Microsoft-Dokumentation'
description: In dieser Lerneinheit definieren Sie eine Datenquelle. Der Bericht verwendet diese Verbindungsinformationen, um auf Daten aus einer relationalen Datenbank oder anderen Quellen zuzugreifen.
ms.date: 12/09/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9d4e12a0322a35e96bd930c4fa6f1f852daf2bdd
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75258466"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Lektion 2: Angeben von Verbindungsinformationen (Reporting Services)

In Lektion 1 haben Sie gelernt, wie Sie Ihrem Tutorialprojekt einen paginierten [!INCLUDE[ssrsnoversion-md](../includes/ssrsnoversion-md.md)]-Bericht hinzufügen.
  
In dieser Lektion definieren Sie eine *Datenquelle*. Diese Verbindungsinformation wird von einem Bericht benötigt, um auf Daten aus einer relationalen Datenbank oder anderen Quellen zugreifen zu können.

Für diesen Bericht wird die Beispieldatenbank „AdventureWorks2016“ als Datenquelle hinzugefügt. In diesem Tutorial wird davon ausgegangen, dass die Datenbank in der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] auf Ihrem lokalen Computer installiert ist.  

## <a name="to-set-up-a-connection"></a>So richten Sie eine Verbindung ein  

1. Klicken Sie im Bereich **Berichtsdaten** auf **Neu** > **Datenquelle**. Wird der Bereich **Berichtsdaten** nicht angezeigt, klicken Sie im Menü **Ansicht** auf **Berichtsdaten**.

    ![ssrs-table-tutorial-2-new-data-source](media/ssrs-table-tutorial-2-new-data-source.png)

    Das Dialogfeld **Datenquelleneigenschaften** wird geöffnet mit dem Abschnitt **Allgemein**.

    ![Dialogfeld „Datenquelleneigenschaften“](media/lesson-2-specifying-connection-information-reporting-services/vs-datasource-connection-properties-dialog-box.png)

2. Geben Sie in das Textfeld **Name** den Begriff „AdventureWorks2016“ ein.

3. Aktivieren Sie das Optionsfeld **Eingebettete Verbindung**.

4. Wählen Sie im Dropdownfeld **Typ** die Option „Microsoft SQL Server“ aus.
  
5. Geben Sie in das Textfeld **Verbindungszeichenfolge** folgende Zeichenfolge ein:

    `Data source=localhost; initial catalog=AdventureWorks2016`

    > [!NOTE]
    > Bei dieser Verbindungszeichenfolge wird davon ausgegangen, dass der Berichtsserver [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und die Datenbank „AdventureWorks2016“ auf demselben lokalen Computer installiert sind.
    >
    >Ist dies nicht der Fall, ändern Sie die Verbindungszeichenfolge, und ersetzen Sie „localhost“ durch den Namen Ihres Datenbankservers/Ihrer Datenbankinstanz. Wenn Sie [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] oder eine benannte SQL Server-Instanz verwenden, müssen Sie die Verbindungszeichenfolge so ändern, dass sie Instanzinformationen enthält. Beispiel:
    >
    > `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2016`
    >
    > Weitere Informationen zu Verbindungszeichenfolgen finden Sie im Abschnitt `See also` weiter unten.

6. Klicken Sie auf die Registerkarte **Anmeldeinformationen**, und wählen Sie im Abschnitt **Anmeldeinformationen ändern, mit denen eine Verbindung mit der Datenquelle hergestellt wird** das Optionsfeld **Windows-Authentifizierung verwenden (integrierte Sicherheit)** aus.

7. Klicken Sie auf **OK**, um den Vorgang abzuschließen.

Im Berichts-Designer wird die Datenquelle „AdventureWorks2016“ dem Bereich **Berichtsdaten** hinzugefügt.

![ssrs-adventureworks-datasource](media/lesson-2-specifying-connection-information-reporting-services/ssrs-adventureworks-datasource2016.png)

## <a name="next-steps"></a>Nächste Schritte

In dieser Lektion haben Sie erfolgreich eine Verbindung mit der Beispieldatenbank „AdventureWorks2016“ definiert. Fahren Sie fort mit [Lektion 3: Definieren eines Datasets für den Tabellenbericht &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)
