---
title: 'Schritt 7: Hinzufügen und Konfigurieren des OLE DB-Ziels | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 620314ec11154737dc6d35bcf1d3e2587aaab2a1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65722995"
---
# <a name="lesson-1-7-add-and-configure-the-ole-db-destination"></a>Lektion 1.7: Hinzufügen und Konfigurieren des OLE DB-Ziels

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Von Ihrem Paket können jetzt Daten aus der Flatfilequelle extrahiert und in ein Format transformiert werden, das mit dem Ziel kompatibel ist. Die nächste Aufgabe besteht darin, die transformierten Daten in das Ziel zu laden. Fügen Sie ein OLE DB-Ziel zum Datenfluss hinzu, um die Daten zu laden. Das OLE DB-Ziel kann eine Datenbanktabelle, eine Ansicht oder einen SQL-Befehl verwenden, um Daten in verschiedene OLE DB-kompatible Datenbanken zu laden.  
  
In dieser Aufgabe fügen Sie ein OLE DB-Ziel hinzu und konfigurieren es, sodass die zuvor von Ihnen erstellte OLE DB-Verbindungs-Manager-Instanz verwendet werden kann.  
  
## <a name="add-and-configure-the-sample-ole-db-destination"></a>Hinzufügen und Konfigurieren eines OLE DB-Beispielziels  
  
1.  Erweitern Sie **Andere Ziele**in der **SSIS-Toolbox**, und ziehen Sie **OLE DB-Ziel** auf die Entwurfsoberfläche der Registerkarte **Datenfluss** . Fügen Sie das **OLE DB-Ziel** direkt unterhalb der Transformation **Lookup Date Key** ein.  
  
2.  Klicken Sie auf die Transformation **Lookup Date Key**, und ziehen Sie den blauen Pfeil zum neuen **OLE DB-Ziel**, um die zwei Komponenten miteinander zu verbinden.  
  
3.  Klicken Sie im Dialogfeld **Eingabe-/Ausgabe-Auswahl** im Listenfeld **Ausgabe** erst auf **Ausgabe der Suchübereinstimmungen**, und klicken anschließend auf **OK**.  
  
4.  Klicken Sie auf der Entwurfsoberfläche **Datenfluss** in der neuen **OLE DB-Ziel** -Komponente auf **OLE DB-Ziel**, und ändern Sie den Namen in **Sample OLE DB Destination** (OLE DB-Beispielziel).  
  
5.  Doppelklicken Sie auf **Sample OLE DB Destination**.  
  
6.  Stellen Sie im Dialogfeld **Ziel-Editor für OLE DB** sicher, dass **localhost.AdventureWorksDW2012** im Feld **OLE DB-Verbindungs-Manager** ausgewählt ist.  
  
7.  Geben Sie in das Feld **Name of the table or the view** (Name der Tabelle oder Sicht) **[dbo].[FactCurrencyRate]** ein, oder wählen Sie diese Zeichenfolge aus.  
  
8.  Klicken Sie auf die Schaltfläche **Neu**, um eine neue Tabelle zu erstellen.  Ändern Sie den Namen der Tabelle im Skript von **Sample OLE DB Destination** (OLE DB-Beispielziel) in **NewFactCurrencyRate**.  Wählen Sie **OK**.  
  
9. Wenn Sie auf **OK** klicken, wird das Dialogfeld geschlossen, und das Feld **Name of the table or the view** (Name der Tabelle oder Ansicht) wird automatisch in **NewFactCurrencyRate** geändert.  
  
10. Klicken Sie auf **Zuordnungen**.  
  
11. Überprüfen Sie, ob die Eingabespalten **AverageRate**, **CurrencyKey**, **EndOfDayRate**und **DateKey** den Zielspalten ordnungsgemäß zugeordnet sind. Wenn gleichnamige Spalten einander zugeordnet sind, ist die Zuordnung richtig.  
  
12. Wählen Sie **OK**.  
  
13. Klicken Sie erst mit der rechten Maustaste auf das Ziel **Sample OLE DB Destination** (OLE DB-Beispielziel) und anschließend mit der linken auf **Eigenschaften**.  
  
14. Überprüfen Sie im Fenster **Eigenschaften**, ob die Eigenschaft **LocaleID** auf **Englisch (USA)** und die Eigenschaft **DefaultCodePage** auf **1252** festgelegt ist.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Step 8: Vereinfachen des Layouts des Pakets aus Lektion 1](../integration-services/lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a>Siehe auch  
[OLE DB-Ziel](../integration-services/data-flow/ole-db-destination.md)  
  
  
  
