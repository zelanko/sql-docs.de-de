---
title: Erstellen Sie-Enannte Berechnung (Dialogfeld) (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 31c0444930e15d933d75dd72554c3232871cd59e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225190"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>Erstellen Sie-Enannte Berechnung (Dialogfeld) (Analysis Services)
  Mithilfe des Dialogfelds **Benannte Berechnung erstellen/bearbeiten** können Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] eine benannte Berechnung für eine Tabelle in einer Datenquellensicht definieren oder ändern. Führen Sie zum Anzeigen des Dialogfelds **Benannte Berechnung erstellen/bearbeiten** einen der folgenden Schritte aus:  
  
-   Klicken Sie im Bereich **Symbolleiste** von **Datenquellensicht-Designer** auf **Neue benannte Berechnung**.  
  
-   Klicken Sie im Bereich **Tabellen** oder **Diagramm** des **Datenquellensicht-Designers** mit der rechten Maustaste auf eine Tabelle, und wählen Sie **Neue benannte Berechnung** aus.  
  
-   Klicken Sie im Bereich **Diagramm** des **Datenquellensicht-Designers** mit der rechten Maustaste auf den Namen einer benannten Berechnung, und wählen Sie **Benannte Berechnung bearbeiten** aus.  
  
## <a name="options"></a>Tastatur  
 **Spaltenname**  
 Geben Sie den Namen der benannten Berechnung ein.  
  
 **Beschreibung**  
 Geben Sie die optionale Beschreibung der benannten Berechnung ein.  
  
 **Ausdruck**  
 Geben Sie einen gültigen SQL-Ausdruck ein, der einen skalaren Wert zurückgibt. Der Ausdruck wird an den Anbieter gesendet und im folgenden Ausdruck überprüft:  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 Der Ausdruck kann Verweise auf andere Tabellen in Form einer untergeordneten SELECT-Anweisung enthalten. If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Datenquellensicht-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
