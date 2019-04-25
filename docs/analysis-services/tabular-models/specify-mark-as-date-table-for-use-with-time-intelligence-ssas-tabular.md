---
title: Geben Sie als Datumstabelle markieren in tabellarischen Modellen von Analysis Services | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df4afbecebd3c076f80064dbd3d13f35ba2cbcf0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472080"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence"></a>Geben Sie für die Verwendung mit Zeitintelligenz markieren als Datumstabelle
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Um die Verwendung von zeitintelligenzfunktionen in DAX-Formeln zu verwenden, müssen Sie eine Datumstabelle und eine eindeutige Bezeichnerspalte (Datetime) des Date-Datentyps angeben. Sobald eine Spalte in der Datumstabelle als eindeutiger Bezeichner angegeben wird, können Sie Beziehungen zwischen Spalten in der Datumstabelle und beliebigen Faktentabellen erstellen.  
  
 Wenn Sie zeitintelligenzfunktionen verwenden, gelten die folgenden Regeln:  
  
-   Wenn Sie DAX-zeitintelligenzfunktionen verwenden, geben Sie niemals eine Datetime-Spalte aus einer Faktentabelle aus. Erstellen Sie im Modell immer eine separate Datumstabelle, die mindestens eine datetime-Spalte des Date-Datentyps mit eindeutigen Werten enthält.  
  
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
 [Berechnungen](../../analysis-services/tabular-models/calculations-ssas-tabular.md)   
 [Zeitintelligenzfunktionen (DAX)](http://msdn.microsoft.com/91df278d-4b28-40c1-a572-cdb91f081517)  
  
  
