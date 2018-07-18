---
title: Datamining-Abfrage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquery.f1
ms.assetid: 948e358a-6245-429f-82c7-4cedc5e048fd
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a40552887a63e9c07acf695a40dc3f7fecf02d29
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197920"
---
# <a name="data-mining-query"></a>Data Mining-Abfrage
  Im Entwurfsbereich befindet sich der Data Mining-Generator für Vorhersageabfragen, mit dem Sie Data Mining-Vorhersageabfragen erstellen können. Vorhersageabfragen können entweder auf der Grundlage von Eingabetabellen oder von SINGLETON-Vorhersageabfragen erstellt werden. Wechseln Sie zur Ergebnissicht, um die Abfrage auszuführen und die Ergebnisse anzuzeigen. Die Abfragesicht zeigt die vom Generator für Vorhersageabfragen erstellte DMX-Abfrage (Data Mining Extensions).  
  
## <a name="options"></a>Tastatur  
 Schaltfläche Ansicht wechseln  
 Klicken Sie auf ein Symbol, um zwischen dem Entwurfs- und Abfragebereich zu wechseln. Standardmäßig ist der Entwurfsbereich geöffnet.  
  
 Klicken Sie auf das ![Design-Symbol](../media/ssis-designicon.gif "Design-Symbol"), um in den Entwurfsbereich zu wechseln.  
  
 Klicken Sie auf das ![SQL-Symbol](../media/ssis-queryicon.gif "SQL-Symbol"), um in den Abfragebereich zu wechseln.  
  
 **Miningmodell**  
 Zeigt das Miningmodell an, auf dem Sie die Vorhersagen aufbauen wollen.  
  
 **Modell auswählen**  
 Öffnet das Dialogfeld **Miningmodell auswählen** .  
  
 **Eingabespalten**  
 Zeigt die zum Generieren der Vorhersagen ausgewählten Eingabespalten an.  
  
 **Quelle**  
 Wählen Sie in der Dropdownliste die Quelle aus, die das Feld enthält, das Sie für die Spalte verwenden wollen. Sie können entweder das in der **Miningmodell** -Tabelle ausgewählte Miningmodell, die in der **Eingabetabelle(n) auswählen** -Tabelle ausgewählten Eingabetabellen, eine Vorhersagefunktion oder einen benutzerdefinierten Ausdruck verwenden.  
  
 Spalten können aus den das Miningmodell enthaltenden Tabellen und den Eingabespalten auf die Zelle gezogen werden.  
  
 **Feld**  
 Wählen Sie eine Spalte aus der Liste der aus der Quelltabelle abgeleiteten Spalten aus. Wenn Sie unter **Quelle** die **Vorhersagefunktion**ausgewählt haben, enthält diese Zelle eine Dropdownliste der für das ausgewählte Miningmodell verfügbaren Vorhersagefunktionen.  
  
 **Alias**  
 Der Name der vom Server zurückgegebenen Spalte.  
  
 **Anzeigen**  
 Wählen Sie aus, ob die Spalte zurückgegeben oder nur in der WHERE-Klausel verwendet werden soll.  
  
 **Gruppieren**  
 Wird mit der **Und/Oder** -Spalte verwendet, um Ausdrücke zu gruppieren. Beispielsweise (expr1 OR expr2) AND expr3.  
  
 **Und/Oder**  
 Wird zum Erstellen einer logischen Abfrage verwendet. Beispielsweise (expr1 OR expr2) AND expr3.  
  
 **Kriterium/Argument**  
 Geben Sie eine Bedingung oder einen benutzerdefinierten Ausdruck an, der auf die Spalte angewendet wird. Spalten können aus den das Miningmodell enthaltenden Tabellen und den Eingabespalten auf die Zelle gezogen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Abfrageschnittstellen](../../analysis-services/data-mining/data-mining-query-tools.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
