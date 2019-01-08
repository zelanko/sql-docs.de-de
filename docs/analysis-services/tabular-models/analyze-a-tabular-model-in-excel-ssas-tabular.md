---
title: Eine Analysis Services-Tabellenmodells in Excel analysieren | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a3cd28375a60dc2cbf7447068fde8c5a1c7dba07
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072227"
---
# <a name="analyze-a-tabular-model-in-excel"></a>Analysieren eines tabellarischen Modells in Excel  
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Über die Funktion In Excel analysieren in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] wird Microsoft Excel geöffnet, eine Datenquellenverbindung mit der Arbeitsbereichsdatenbank des Modells hergestellt und eine PivotTable in das Arbeitsblatt eingefügt. Modellobjekte (Tabellen, Spalten, Measures, Hierarchien und KPIs) sind als Felder in der PivotTable-Feldliste enthalten.  
  
> [!NOTE]  
>  Um die Funktion In Excel analysieren zu verwenden, muss Microsoft Office 2003 oder höher auf demselben Computer wie [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]installiert sein. Wenn Office nicht auf demselben Computer installiert ist, können Sie Excel auf einem anderen Computer verwenden und eine Datenquellenverbindung mit der Arbeitsbereichsdatenbank des Modells herstellen. Sie können dem Arbeitsblatt dann manuell eine PivotTable hinzufügen. Modellobjekte (Tabellen, Spalten, Measures und KPIs) sind als Felder in der PivotTable-Feldliste enthalten.  
  
## <a name="tasks"></a>Richtlinienübersicht  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>So analysieren Sie ein tabellarisches Modellprojekt mithilfe der Funktion "In Excel analysieren"  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **In Excel analysieren**.  
  
2.  Wählen Sie im Dialogfeld **Anmeldeinformationen und Perspektive auswählen** eine der folgenden Optionen für Anmeldeinformationen aus, um eine Verbindung mit der Arbeitsbereichsdatenquelle des Modells herzustellen:  
  
    -   Um das aktuelle Benutzerkonto zu verwenden, wählen Sie **Aktueller Windows-Benutzer**aus.  
  
    -   Um ein anderes Benutzerkonto zu verwenden, wählen Sie **Anderer Windows-Benutzer**aus.  
  
         In der Regel ist dieser Benutzer Mitglied einer Rolle. Es ist kein Kennwort erforderlich. Das Konto kann nur im Kontext einer Excel-Verbindung mit der Arbeitsbereichsdatenbank verwendet werden.  
  
    -   Um eine Sicherheitsrolle zu verwenden, wählen Sie **Rolle**und anschließend mindestens eine Rolle im Listenfeld aus.  
  
         Sicherheitsrollen müssen mit dem Rollen-Manager definiert werden. Weitere Informationen finden Sie unter [erstellen und Verwalten von Rollen](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
3.  Um eine Perspektive aus dem Listenfeld **Perspektive** zu verwenden, wählen Sie die Perspektive aus.  
  
     Perspektiven (mit Ausnahme der Standardeinstellung) müssen im Dialogfeld Perspektiven definiert werden. Weitere Informationen finden Sie unter [erstellen und Verwalten von Perspektiven](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md).  
  
> [!NOTE]  
>  Die PivotTable-Feldliste in Excel wird nicht automatisch aktualisiert, wenn Sie im Modell-Designer Änderungen am Modellprojekt vornehmen. Um die PivotTable-Feldliste zu aktualisieren, klicken Sie in Excel im Menüband **Optionen** auf **Aktualisieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [In Excel analysieren](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)  
  
  
