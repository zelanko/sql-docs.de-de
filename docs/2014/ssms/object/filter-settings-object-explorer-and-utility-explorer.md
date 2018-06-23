---
title: Filtereinstellungen (Objekt-Explorer und Hilfsprogramm-Explorer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.job.filtersettings.f1
- sql12.swb.common.filtersettings.f1
ms.assetid: 4aab04bc-e1ab-4d4b-ab74-b287fc805bc2
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 33fb385ecfaac18b3c38a426361f381b301d63cc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151711"
---
# <a name="filter-settings-object-explorer-and-utility-explorer"></a>Filtereinstellungen (Objekt-Explorer und Hilfsprogramm-Explorer)
  Mithilfe dieses Dialogfelds können Sie einen Filter angeben. Mit einem Filter können Sie Objekt-Explorer und Hilfsprogramm-Explorer so konfigurieren, dass nur Elemente angezeigt werden, die bestimmte Kriterien erfüllen. So können Sie mit einem Filter beispielsweise nur Aufträge mit Namen anzeigen lassen, die das Wort "Wartung" enthalten. Die Kopfzeile für das Dialogfeld **Filtereinstellungen** enthält den Namen des Servers und kann den Namen der Datenbank enthalten.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Eigenschaft**  
 Zeigt die Eigenschaft an, nach der gefiltert werden soll.  
  
 **Ist gleich**  
 Wählen Sie die Art aus, in der der Filter den Wert auf die Eigenschaft anwendet. Folgende Optionen stehen zur Verfügung:  
  
-   **Ist gleich**  
  
     Der Filter zeigt Elemente an, bei denen die Eigenschaft und der Wert genau übereinstimmen.  
  
-   **Enthält**  
  
     Der Filter zeigt die Elemente an, bei denen die Eigenschaft den Wert enthält. Die Eigenschaft kann noch weiteren Text enthalten.  
  
-   **Enthält nicht**  
  
     Der Filter zeigt die Elemente an, bei denen die Eigenschaft den Wert nicht enthält.  
  
-   **Kleiner als**  
  
     Verfügbar für Datumsangaben. Dieser Filter zeigt Elemente an, deren Datum vor dem eingegebenen Wert liegt.  
  
-   **Kleiner oder gleich**  
  
     Verfügbar für Datumsangaben. Dieser Filter zeigt Elemente an, deren Datum vor dem eingegebenen Wert liegt bzw. genau dem Wert entspricht.  
  
-   **Größer als**  
  
     Verfügbar für Datumsangaben. Dieser Filter zeigt Elemente an, deren Datum nach dem eingegebenen Wert liegt.  
  
-   **Größer oder gleich**  
  
     Verfügbar für Datumsangaben. Dieser Filter zeigt Elemente an, deren Datum nach dem eingegebenen Wert liegt bzw. genau dem Wert entspricht.  
  
-   **Zwischen**  
  
     Verfügbar für Datumsangaben. Dieser Filter zeigt Elemente an, deren Datum zwischen den eingegebenen Datumsangaben liegt. Wählen Sie **Zwischen** aus, und drücken Sie TAB, um eine weitere Zeile für die Eingabe des zweiten Datums hinzuzufügen.  
  
-   **Nicht zwischen**  
  
     Verfügbar für Datumsangaben. Dieser Filter zeigt Elemente an, deren Datum vor oder nach den beiden eingegebenen Datumsangaben liegt. Wählen Sie **Nicht zwischen** aus, und fügen Sie der **Operator** -Spalte mit TAB eine neue Zeile für die Eingabe des zweiten Datums hinzu.  
  
 **ReplTest1**  
 Geben Sie den Wert ein, mit dem die Eigenschaft verglichen werden soll. Bei Datumsangaben klicken Sie auf den nach unten zeigenden Pfeil, um einen Kalender für die Auswahl des Datums anzuzeigen.  
  
 **Filter löschen**  
 Entfernt alle aktuellen Filtereinstellungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SQL Server Management Studio](../sql-server-management-studio-ssms.md)   
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  