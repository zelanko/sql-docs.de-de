---
title: Bearbeiten von Eigenschaften (Dialogfeld) (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.edittablepropdb.f1
ms.assetid: 8d913e83-7246-44cc-8fc7-31729023c0d8
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 36cabf1186738420e3dbd35504a81ea0318b966b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148244"
---
# <a name="edit-table-properties-dialog-box-ssas"></a>Tabelleneigenschaften bearbeiten (Dialogfeld) (SSAS)
  Im Dialogfeld **Tabelleneigenschaften bearbeiten** können Sie die Eigenschaften von Tabellen anzeigen und ändern, die mit dem Tabellenimport-Assistenten in den Modell-Designer importiert werden. Um das Dialogfeld zu öffnen, wählen Sie im Modell-Designer eine Tabelle aus, und klicken Sie auf das Menü **Tabelle** und anschließend auf **Tabelleneigenschaften**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 Die Optionen dieses Dialogfelds variieren, je nachdem, ob Daten ursprünglich durch Auswahl von Tabellen aus einer Liste oder mithilfe einer SQL-Abfrage importiert wurden.  
  
## <a name="table-preview-mode"></a>Tabellenvorschaumodus  
 **Tabellenname**  
 Zeigt den Namen der Datentabelle im Modell an.  
  
> [!NOTE]  
>  Der Name kann hier nicht bearbeitet werden. Sie können den Namen der Tabelle jedoch ändern, indem Sie im unteren Bereich des Modell-Designers mit der rechten Maustaste auf die Tabellenregisterkarte klicken.  
  
 **Verbindungsname**  
 Zeigt den Namen der aktuell verwendeten Verbindung an.  
  
 **Quellname**  
 Mit dieser Option können Sie die Tabelle anzeigen oder ändern, aus der die Daten abgerufen werden.  
  
 Wenn Sie die Quelle in eine Tabelle ändern, die andere Spalten als die aktuelle Tabelle enthält, wird eine entsprechende Warnmeldung angezeigt. Sie müssen dann die Spalten auswählen, die Sie in die aktuelle Tabelle einfügen möchten, und auf **Speichern**klicken. Sie können die gesamte Tabelle ersetzen, indem Sie das Kontrollkästchen links von der Tabelle aktivieren.  
  
> [!NOTE]  
>  Wenn Sie die Datenquelle einer Tabelle ändern, ersetzen Sie praktisch den Inhalt der aktuellen Tabelle durch den Inhalt der neuen Quelltabelle.  
  
 **Spaltennamen aus**  
 |||  
|-|-|  
|**Quelle**|Aktivieren Sie diese Option, um die aktuellen Spaltennamen durch die Spaltennamen aus der ausgewählten Quelltabelle zu ersetzen.|  
|**Model**|Aktivieren Sie diese Option, um die aktuellen Spaltennamen zu verwenden, wie sie im Modell vorhanden sind.|  
  
 **Vorschau aktualisieren**  
 Klicken Sie auf diese Option, um die Spalten der Daten in der momentan ausgewählten Quelltabelle anzuzeigen.  
  
 **Wechseln Sie zu**  
 |||  
|-|-|  
|**Tabellenvorschau**|Wählen Sie diese Option aus, um die ausgewählte Tabelle und eine beschränkte Anzahl von Datenzeilen in der Vorschau anzuzeigen.|  
|**Abfrage-editor**|Wählen Sie diese Option aus, um die Abfrage für die ausgewählte Datenquelle anzuzeigen. Diese Option ist nicht für alle Datenquellen verfügbar.|  
  
 **Kontrollkästchen im Spaltenheader**  
 Aktivieren Sie das Kontrollkästchen, um die Spalte in den Datenimport einzuschließen. Deaktivieren Sie das Kontrollkästchen, um die Spalte aus dem Datenimport zu entfernen.  
  
 **Nach-unten Schaltfläche in der Kopfzeile der Spalte**  
 Filtern Sie Daten in der Spalte.  
  
 **Zeilenfilter löschen**  
 Klicken Sie auf diese Option, um alle angewendeten Filter zu entfernen.  
  
 **OK**  
 Klicken Sie auf diese Option, um alle vorgenommenen Änderungen zu übernehmen, auch das Ersetzen der Spalten.  
  
## <a name="query-design-mode"></a>Abfrageentwurfsmodus  
 **Tabellenname**  
 Zeigt den Namen der Datentabelle im Modell an.  
  
> [!NOTE]  
>  Sie können den Namen hier nicht bearbeiten. Sie können den Namen der Tabelle jedoch ändern, indem Sie im unteren Bereich des Designers mit der rechten Maustaste auf die Tabellenregisterkarte klicken.  
  
 **Verbindungsname**  
 Zeigt den Namen der aktuell verwendeten Verbindung an.  
  
 **Wechseln Sie zu**  
 |||  
|-|-|  
|**Tabellenvorschau**|Wählen Sie diese Option Liste aus, um die ausgewählte Tabelle und einige Zeilen der Daten in der Vorschau anzuzeigen.|  
|**Abfrage-editor**|Aktivieren Sie diese Option, um die Abfrage anzuzeigen, die für die ausgewählte Datenquelle ausgegeben wird.|  
  
 **SQL-Anweisung**  
 Zeigt die SQL-Anweisung an, die für die aktuelle Datenquelle ausgegeben wird, um Zeilen abzurufen. Standardmäßig werden alle Zeilen abgerufen. Sie können jedoch auch eine Teilmenge der Zeilen abrufen, indem Sie entweder einen Filter entwerfen oder die SQL-Anweisung manuell bearbeiten.  
  
 **Überprüfen**  
 Klicken Sie auf diese Option, um sicherzustellen, dass die Anweisung für die ausgewählte Datenquelle und den Anbieter syntaktisch korrekt ist.  
  
 **Entwerfen**  
 Klicken Sie auf diese Option, um einen visuellen Abfrage-Designer zu öffnen und eine Abfrageanweisung zu erstellen. Drücken Sie im Designer die F1-TASTE, um Informationen zum Verwenden des Designers zu erhalten.  
  
 **OK**  
 Klicken Sie auf diese Option, um alle vorgenommenen Änderungen zu übernehmen, auch das Ersetzen der Spalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Spalten &#40;SSAS – tabellarisch&#41;](tabular-models/tables-and-columns-ssas-tabular.md)  
  
  