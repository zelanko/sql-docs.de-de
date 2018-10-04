---
title: Hinzufügen einer Tabelle (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 065cec0c70d0b98131dc4cdc5b477b11115091f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146510"
---
# <a name="add-a-table-ssas-tabular"></a>Hinzufügen einer Tabelle (SSAS – tabellarisch)
  In diesem Thema wird beschrieben, wie Sie eine Tabelle aus einer Datenquelle hinzufügen, aus der Sie zuvor Daten in das Modell importiert haben. Um eine Tabelle aus derselben Datenquelle hinzuzufügen, können Sie die vorhandene Datenquellenverbindung verwenden. Es wird empfohlen, immer eine einzelne Verbindung zu verwenden, wenn Sie eine beliebige Anzahl von Tabellen aus einer einzelnen Datenquelle importieren.  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a>So fügen Sie eine Tabelle aus einer vorhandenen Datenquelle hinzu  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Menü **Modell** auf **Vorhandene Verbindungen**.  
  
2.  Wählen Sie auf der Seite **Vorhandene Verbindungen** die Verbindung mit der Datenquelle aus, die über die hinzuzufügende Tabelle verfügt, und klicken Sie dann auf **Öffnen**.  
  
3.  Wählen Sie auf der Seite **Tabellen und Sichten auswählen** die Tabelle aus der Datenquelle aus, die Sie dem Modell hinzufügen möchten.  
  
    > [!NOTE]  
    >  Die Seite **Tabellen und Sichten auswählen** enthält keine Tabellen, die zuvor als überprüft importiert wurden.  Wenn Sie eine Tabelle auswählen, die zuvor mithilfe dieser Verbindung importiert wurde, und Sie der Tabelle keinen anderen Anzeigenamen gegeben haben, wird eine 1 an den Anzeigenamen angefügt. Tabellen, die zuvor mithilfe dieser Verbindung importiert wurden, müssen nicht erneut ausgewählt werden.  
  
4.  Verwenden Sie ggf. **Vorschau und Filter**, um nur bestimmte Spalten auszuwählen bzw. Filter auf die zu importierenden Daten anzuwenden.  
  
5.  Klicken Sie auf **Fertig stellen** , um die neue Tabelle zu importieren.  
  
> [!NOTE]  
>  Wenn Sie mehrere Tabellen gleichzeitig aus einer einzelnen Datenquelle importieren, werden im Modell automatisch die Tabellenbeziehungen erstellt, die in der Datenquelle vorhanden waren. Wenn Sie später eine Tabelle hinzufügen, kann es jedoch erforderlich sein, manuell Beziehungen zwischen den neu hinzugefügten und den zuvor importierten Tabellen im Modell zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Importieren von Daten &#40;SSAS – tabellarisch&#41;](../import-data-ssas-tabular.md)   
 [Löschen einer Tabelle &#40;SSAS – tabellarisch&#41;](delete-a-table-ssas-tabular.md)  
  
  
