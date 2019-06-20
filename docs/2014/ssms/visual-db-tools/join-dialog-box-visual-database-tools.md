---
title: Verknüpfen (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e266d398debd65a8a03f73d7f8726899c97b7e13
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62711135"
---
# <a name="join-dialog-box-visual-database-tools"></a>Verknüpfen (Dialogfeld) (Visual Database Tools)
  In diesem Dialogfeld können Sie Optionen zum Verknüpfen von Tabellen angeben. Um das Dialogfeld aufzurufen, wählen Sie im Bereich **Entwurf** eine Joinlinie aus. Klicken Sie anschließend im Fenster **Eigenschaften** auf **Joinbedingung und -typ**, und klicken Sie auf die Auslassungspunkte **(...)** , die rechts neben der Eigenschaft angezeigt werden.  
  
 In der Standardeinstellung sind verknüpfte Tabellen über eine innere Verknüpfung miteinander verbunden. Mithilfe dieser Verknüpfung wird ein Resultset auf der Grundlage von Zeilen erstellt, deren Inhalte mit den Informationen in den verknüpften Spalten übereinstimmen. Wenn Sie die Optionen im Dialogfeld **Verbinden** festlegen, können Sie einen Join angeben, die auf einem anderen Operator basiert. Außerdem können Sie einen äußeren Join festlegen.  
  
 Weitere Informationen zum Verbinden von Tabellen finden Sie unter [Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
## <a name="options"></a>Optionen  
  
|**Begriff**|**Definition**|  
|--------------|--------------------|  
|**Table**|Die Namen der verknüpften Tabellen bzw. Tabellenwertobjekte. Die Tabellennamen können an dieser Stelle nicht geändert werden. Sie werden lediglich zu Informationszwecken angezeigt.|  
|**Spalte**|Die Namen der Spalten, mit denen die Tabellen verknüpft werden. Mit dem Operator in der Operatorliste wird die Beziehung zwischen den Daten in den Spalten angegeben. Die Spaltennamen können an dieser Stelle nicht geändert werden. Sie werden lediglich zu Informationszwecken angezeigt.|  
|**Operator**|Geben Sie den Operator an, der die Beziehung zwischen den verknüpften Spalten bestimmt. Wenn nicht der Gleichheitsoperator (=) festgelegt werden soll, wählen Sie den gewünschten Operator aus der Liste aus. Wenn Sie die Eigenschaftenseite schließen, wird der von Ihnen ausgewählte Operator im Rautensymbol der Joinlinie wie folgt angezeigt:<br /><br /> ![Symbol für Visual Database Tools](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")|  
|**Alle Zeilen aus \<table1 >**|Geben Sie an, dass alle Zeilen der linken Tabelle auch dann in der Ausgabe aufgeführt werden, wenn die rechte Tabelle keine entsprechenden Zeilen enthält. Für Spalten ohne übereinstimmende Daten in der rechten Tabelle werden keine Werte angezeigt. Das Auswählen dieser Option ist gleichbedeutend mit der Angabe von LEFT OUTER JOIN in der SQL-Anweisung.|  
|**Alle Zeilen aus \<table2 >**|Geben Sie an, dass alle Zeilen der rechten Tabelle auch dann in der Ausgabe aufgeführt werden, wenn die linke Tabelle keine entsprechenden Zeilen enthält. Für Spalten ohne übereinstimmende Daten in der linken Tabelle werden keine Werte angezeigt. Das Auswählen dieser Option ist gleichbedeutend mit der Angabe von RIGHT OUTER JOIN in der SQL-Anweisung.|  
  
 Wählen sowohl alle **Zeilen aus \<table1 >** und **alle Zeilen aus \<table2 >** entspricht der Angabe von FULL OUTER JOIN in der SQL-Anweisung.  
  
 Wenn eine Option zum Erstellen eines äußeren Joins angegeben wird, ändert sich das Rautensymbol in der Joinlinie, um anzuzeigen, dass es sich beim Join um einen linken äußeren, rechten äußeren oder vollständigen äußeren Join handelt.  
  
> [!NOTE]  
>  Die Wörter "links" und "rechts" müssen nicht unbedingt der Position der Tabellen im Diagrammbereich entsprechen. "Links" bezieht sich auf die Tabelle, die in der SQL-Anweisung links vom Schlüsselwort JOIN genannt wird, und "rechts" bezieht sich dementsprechend auf die Tabelle zur Rechten des Schlüsselworts JOIN. Ein Verschieben der Tabellen im Bereich **Diagramm** hat keinen Einfluss darauf, welche Tabelle als links oder rechts behandelt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Abfragen mit Joins &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
