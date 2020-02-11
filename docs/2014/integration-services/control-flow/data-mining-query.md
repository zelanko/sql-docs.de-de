---
title: Datamining-Abfrage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquery.f1
ms.assetid: 948e358a-6245-429f-82c7-4cedc5e048fd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 07373f17838fa387fe6ee22e31312a3933307fa3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68890331"
---
# <a name="data-mining-query"></a>Data Mining-Abfrage
  Im Entwurfsbereich befindet sich der Data Mining-Generator für Vorhersageabfragen, mit dem Sie Data Mining-Vorhersageabfragen erstellen können. Vorhersageabfragen können entweder auf der Grundlage von Eingabetabellen oder von SINGLETON-Vorhersageabfragen erstellt werden. Wechseln Sie zur Ergebnissicht, um die Abfrage auszuführen und die Ergebnisse anzuzeigen. Die Abfragesicht zeigt die vom Generator für Vorhersageabfragen erstellte DMX-Abfrage (Data Mining Extensions).  
  
## <a name="options"></a>Tastatur  
 Schaltfläche Ansicht wechseln  
 Klicken Sie auf ein Symbol, um zwischen dem Entwurfs- und Abfragebereich zu wechseln. Standardmäßig ist der Entwurfsbereich geöffnet.  
  
 Um zum Entwurfs Bereich zu wechseln, klicken Sie auf das Symbol für den ![Entwurfs Symbol](../media/ssis-designicon.gif "Entwurf (Symbol)") .  
  
 Um zum Abfrage Bereich zu wechseln, klicken Sie auf das Symbol ![SQL-Symbol](../media/ssis-queryicon.gif "SQL (Symbol)") .  
  
 **Mining Modell**  
 Zeigt das Miningmodell an, auf dem Sie die Vorhersagen aufbauen wollen.  
  
 **Modell auswählen**  
 Öffnet das Dialogfeld **Miningmodell auswählen** .  
  
 **Eingabe Spalten**  
 Zeigt die zum Generieren der Vorhersagen ausgewählten Eingabespalten an.  
  
 **`Source`**  
 Wählen Sie in der Dropdownliste die Quelle aus, die das Feld enthält, das Sie für die Spalte verwenden wollen. Sie können entweder das in der **Miningmodell** -Tabelle ausgewählte Miningmodell, die in der **Eingabetabelle(n) auswählen** -Tabelle ausgewählten Eingabetabellen, eine Vorhersagefunktion oder einen benutzerdefinierten Ausdruck verwenden.  
  
 Spalten können aus den das Miningmodell enthaltenden Tabellen und den Eingabespalten auf die Zelle gezogen werden.  
  
 **Feld**  
 Wählen Sie eine Spalte aus der Liste der aus der Quelltabelle abgeleiteten Spalten aus. Wenn Sie unter **Quelle** die **Vorhersagefunktion**ausgewählt haben, enthält diese Zelle eine Dropdownliste der für das ausgewählte Miningmodell verfügbaren Vorhersagefunktionen.  
  
 **Alias**  
 Der Name der vom Server zurückgegebenen Spalte.  
  
 **Anzeigen**  
 Wählen Sie aus, ob die Spalte zurückgegeben oder nur in der WHERE-Klausel verwendet werden soll.  
  
 **Gruppe**  
 Wird mit der **Und/Oder** -Spalte verwendet, um Ausdrücke zu gruppieren. Beispielsweise (expr1 OR expr2) AND expr3.  
  
 **Und/oder**  
 Wird zum Erstellen einer logischen Abfrage verwendet. Beispielsweise (expr1 OR expr2) AND expr3.  
  
 **Kriterium/Argument**  
 Geben Sie eine Bedingung oder einen benutzerdefinierten Ausdruck an, der auf die Spalte angewendet wird. Spalten können aus den das Miningmodell enthaltenden Tabellen und den Eingabespalten auf die Zelle gezogen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen für Data Mining-Abfragen](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
