---
title: Geben Sie für die Verwendung mit Zeitintelligenz (SSAS – tabellarisch) markieren als Datumstabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af799e8e806696022635a04d808213ffb5c0e779
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794301"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular"></a>Angeben von "Als Datumstabelle markieren" zur Verwendung mit Zeitintelligenz (SSAS – tabellarisch)
  Um die Zeitintelligenzfunktionen in DAX-Formeln zu verwenden, müssen Sie eine Datumstabelle und eine eindeutige Bezeichnerspalte (datetime) des Date-Datentyps angeben. Sobald eine Spalte in der Datumstabelle als eindeutiger Bezeichner angegeben wird, können Sie Beziehungen zwischen Spalten in der Datumstabelle und beliebigen Faktentabellen erstellen.  
  
 Bei Verwendung der Zeitintelligenzfunktionen gelten die folgenden Regeln:  
  
-   Bei Verwendung von DAX-Zeitintelligenzfunktionen sollte niemals eine datetime-Spalte aus einer Faktentabelle angegeben werden. Erstellen Sie im Modell immer eine separate Datumstabelle, die mindestens eine datetime-Spalte des Date-Datentyps mit eindeutigen Werten enthält.  
  
-   Stellen Sie sicher, dass die Datumstabelle über einen fortlaufenden Datumsbereich verfügt.  
  
-   Die datetime-Spalte in der Datumstabelle sollte Tagesgranularität (ohne Unterteilung der Tage) aufweisen.  
  
-   Sie müssen eine Datumstabelle und eine eindeutige Bezeichnerspalte im Dialogfeld **Als Datumstabelle markieren** angeben.  
  
-   Erstellen Sie Beziehungen zwischen Faktentabellen und Spalten des Date-Datentyps in der Datumstabelle.  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a>So geben Sie eine Datumstabelle und einen eindeutigen Bezeichner an  
  
1.  Klicken Sie im Modell-Designer auf die Datumstabelle.  
  
2.  Klicken Sie im Menü **Tabelle** auf **Datum**, und klicken Sie dann auf **Als Datumstabelle markieren**  
  
3.  Wählen Sie im Dialogfeld **Als Datumstabelle markieren** im Listenfeld **Datum** eine Spalte aus, die als eindeutiger Bezeichner verwendet wird. Diese Spalte muss eindeutige Werte enthalten und sollte den Date-Datentyp aufweisen. Zum Beispiel:  
  
    |date|  
    |----------|  
    |7/1/2010 12:00:00 AM|  
    |7/2/2010 12:00:00 AM|  
    |7/3/2010 12:00:00 AM|  
    |7/4/2010 12:00:00 AM|  
    |7/5/2010 12:00:00 AM|  
  
4.  Erstellen Sie ggf. Beziehungen zwischen Faktentabellen und der Datumstabelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Berechnungen &#40;SSAS – tabellarisch&#41;](calculations-ssas-tabular.md)   
 [Zeitintelligenzfunktionen &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634763.aspx)  
  
  
