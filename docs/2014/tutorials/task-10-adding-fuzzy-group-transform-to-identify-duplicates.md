---
title: 'Aufgabe 10: Hinzufügen der Transformation für Fuzzygruppierung zum Erkennen von Duplikaten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e7091c4dbb8244476357afba18e973535def8baa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064805"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a>Aufgabe 10: Hinzufügen der Transformation für Fuzzygruppierung zur Identifizierung von Duplikaten
  In dieser Aufgabe fügen Sie eine Transformation für Fuzzygruppierung zum Datenfluss hinzu. Mit der Transformation für Fuzzygruppierung können Duplikate in den Quelldaten identifiziert werden. Weitere Informationen finden Sie unter [Transformation für Fuzzygruppierung](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) .  
  
1.  Ziehen Sie die Transformation für **Fuzzygruppierung** in **andere Transformationen** der **SSIS-Toolbox** auf die Registerkarte **Datenfluss** unter **richtige und korrigierte Datensätze kombinieren**.  
  
2.  Klicken Sie in der Registerkarte Datenfluss mit der rechten Maustaste auf Transformation für **Fuzzygruppierung** , **und klicken Sie** **Data Flow** Geben Sie **Group Suppliers with Matching IDs** ein, und drücken **Sie die Eingabe**Taste  
  
3.  Verbinden Sie **korrekte und korrigierte Datensätze** **mit Gruppen Lieferanten mit übereinstimmenden IDs** , die den blauen Connector verwenden.  
  
     ![Verbinden mit Gruppenlieferanten mit übereinstimmenden IDs](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "Verbinden mit Gruppenlieferanten mit übereinstimmenden IDs")  
  
4.  Doppelklicken Sie auf **Gruppen Lieferanten mit übereinstimmenden IDs**.  
  
5.  Klicken Sie im **Transformations-Editor für fuzzygruppen**neben **OLE DB Dropdown Liste Verbindungs-Manager** auf **neu** , um das Dialogfeld **OLE DB Verbindungs** -Manager konfigurieren zu starten.  
  
6.  Klicken Sie im Dialogfeld auf **neu** , um das Dialogfeld **Verbindungs-Manager** zu starten.  
  
7.  Geben Sie **(local)** oder **Period** (.) als Server Namen ein.  
  
8.  Wählen Sie **MDS** aus, **oder geben Sie ein Feld Datenbankname ein** . Die MDS-Datenbank wird als temporärer Speicher für die **Transformation für fuzzygruppen**verwendet. Die Transformation für **Fuzzygruppierung** erfordert eine Verbindung mit einer Instanz von SQL Server um die temporären SQL Server Tabellen zu erstellen, die der Transformations Algorithmus für seine Arbeit benötigt. Sie können eine Datenbank erstellen oder eine andere vorhandene Datenbank zu diesem Zweck verwenden.  
  
9. Klicken Sie auf **Verbindung testen** , um die Verbindung zu testen, und klicken Sie im Meldungs Feld auf **OK** .  
  
10. Klicken Sie im Dialogfeld **Verbindungs-Manager** auf **OK**.  
  
11. Wählen Sie **(lokal) aus. MDS** (oder **localhost. MDS**) aus der **Liste der Datenverbindungen** , und klicken Sie auf **OK**.  
  
12. Bestätigen Sie im **Transformations-Editor für Fuzzygruppierung**, dass **(local) lautet. MDS** oder **localhost. MDS** ist für den **OLE DB-Verbindungs-Manager**ausgewählt.  
  
13. Wechseln Sie zur Registerkarte **Spalten** .  
  
14. Aktivieren Sie das Kontrollkästchen (Kontrollkästchen) **SupplierID_Output** aus der Liste der **verfügbaren Eingabe Spalten**. Um die Transformation zu konfigurieren, wählen Sie die Eingabespalten für die Identifizierung von Duplikaten aus. Verwenden Sie in diesem Schritt zur Vereinfachung nur die SupplierID.  
  
     ![Transformations-Editor für Fuzzygruppierung](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "Transformations-Editor für Fuzzygruppierung")  
  
15. Klicken Sie auf **OK** , um den **Transformations-Editor für fuzzygruppen**  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 11: Hinzufügen der Transformation „Bedingtes Teilen“ zur Filterung von Duplikaten](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
