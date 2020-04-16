---
title: 'Schritt 7: Hinzufügen und Konfigurieren des OLE DB-Ziels | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 97b155852a0d6941cff4da0bdd4565e08dc63e79
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "62767559"
---
# <a name="step-7-adding-and-configuring-the-ole-db-destination"></a>Schritt 7: Hinzufügen und Konfigurieren des OLE DB-Ziels
  Von Ihrem Paket können jetzt Daten aus der Flatfilequelle extrahiert und in ein Format transformiert werden, das mit dem Ziel kompatibel ist. Die nächste Aufgabe besteht darin, die transformierten Daten tatsächlich in das Ziel zu laden. Um die Daten zu laden, müssen Sie ein OLE DB-Ziel zum Datenfluss hinzufügen. Vom OLE DB-Ziel kann eine Datenbanktabelle, eine Ansicht oder ein SQL-Befehl verwendet werden, um Daten in verschiedene OLE DB-kompatible Datenbanken zu laden.  
  
 In diesem Vorgang fügen Sie ein OLE DB-Ziel hinzu und konfigurieren es, sodass der OLE DB-Verbindungs-Manager verwendet werden kann, den Sie vorher erstellt haben.  
  
### <a name="to-add-and-configure-the-sample-ole-db-destination"></a>So fügen Sie das Beispiel-OLE DB-Ziel hinzu und konfigurieren es  
  
1.  Erweitern Sie in der **SSIS Toolbox** **andere Ziele**, und ziehen Sie OLE **DB Destination** auf die Entwurfsoberfläche der Registerkarte **Datenfluss.** Platzieren Sie das OLE DB-Ziel direkt unter der **Transformation "Lookup Date Key".**  
  
2.  Klicken Sie auf die Transformation **Lookup Date Key** , und ziehen Sie den grünen Pfeil zum neu hinzugefügten **OLE DB-Ziel** , um die zwei Komponenten miteinander zu verbinden.  
  
3.  Klicken Sie im Dialogfeld **Eingabe-/Ausgabe-Auswahl** im Listenfeld **Ausgabe** auf **Ausgabe der Suchübereinstimmungen**, und klicken Sie anschließend auf **OK**.  
  
4.  Klicken Sie auf der Entwurfsoberfläche **Datenfluss** in der neu hinzugefügten **OLE DB-Ziel** -Komponente auf **OLE DB-Ziel** , und ändern Sie den Namen zu **Sample OLE DB Destination**(OLE DB-Beispielziel).  
  
5.  Doppelklicken Sie auf **Sample OLE DB Destination**.  
  
6.  Stellen Sie im Dialogfeld **Ziel-Editor für OLE DB** sicher, dass **localhost.AdventureWorksDW2012** im Feld **OLE DB-Verbindungs-Manager** ausgewählt ist.  
  
7.  Geben Sie im Feld **Name der Tabelle oder Sicht****[dbo].[FactCurrencyRate]** ein, oder wählen Sie diese Zeichenfolge aus.  
  
8.  Klicken Sie auf die Schaltfläche **Neu** , um eine neue Tabelle zu erstellen.  Ändern Sie den Namen der Tabelle im Skript in **NewFactCurrencyRate**.  Klicken Sie auf **OK**.  
  
9. Nach dem Klicken auf **OK**wird das Dialogfeld geschlossen, und der **Name der Tabelle oder Sicht** wird automatisch in **NewFactCurrencyRate**geändert.  
  
10. Klicken Sie auf **Zuordnungen**.  
  
11. Überprüfen Sie, ob die Eingabespalten **AverageRate**, **CurrencyKey**, **EndOfDayRate**und **DateKey** den Zielspalten ordnungsgemäß zugeordnet sind. Wenn gleichnamige Spalten einander zugeordnet sind, ist die Zuordnung richtig.  
  
12. Klicken Sie auf **OK**.  
  
13. Klicken Sie mit der rechten Maustaste auf das Ziel **Sample OLE DB Destination** und anschließend auf **Eigenschaften**.  
  
14. Stellen Sie im Fenster `LocaleID` Eigenschaften sicher, dass die Eigenschaft`DefaultCodePage` auf **Englisch (USA)** und die Eigenschaft auf **1252**festgelegt ist.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Schritt 8: Vereinfachen des Layouts des Pakets aus Lektion 1](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Ziel](data-flow/ole-db-destination.md)  
  
  
