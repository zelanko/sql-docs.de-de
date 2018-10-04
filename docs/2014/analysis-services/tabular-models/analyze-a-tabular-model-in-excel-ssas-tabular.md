---
title: Analysieren eines Tabellenmodells in Excel (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b918cca81ba7e2ba0964012b7efcf40ad0a09fde
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224500"
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a>Analysieren eines Tabellenmodells in Excel (SSAS – tabellarisch)
  Über die Funktion In Excel analysieren in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] wird Microsoft Excel geöffnet, eine Datenquellenverbindung mit der Arbeitsbereichsdatenbank des Modells hergestellt und eine PivotTable in das Arbeitsblatt eingefügt. Modellobjekte (Tabellen, Spalten, Measures, Hierarchien und KPIs) sind als Felder in der PivotTable-Feldliste enthalten.  
  
> [!NOTE]  
>  Um die Funktion In Excel analysieren zu verwenden, muss Microsoft Office 2003 oder höher auf demselben Computer wie [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]installiert sein. Wenn Office nicht auf demselben Computer installiert ist, können Sie Excel auf einem anderen Computer verwenden und eine Datenquellenverbindung mit der Arbeitsbereichsdatenbank des Modells herstellen. Sie können dem Arbeitsblatt dann manuell eine PivotTable hinzufügen. Modellobjekte (Tabellen, Spalten, Measures und KPIs) sind als Felder in der PivotTable-Feldliste enthalten.  
  
## <a name="tasks"></a>Aufgaben  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>So analysieren Sie ein tabellarisches Modellprojekt mithilfe der Funktion "In Excel analysieren"  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **In Excel analysieren**.  
  
2.  Wählen Sie im Dialogfeld **Anmeldeinformationen und Perspektive auswählen** eine der folgenden Optionen für Anmeldeinformationen aus, um eine Verbindung mit der Arbeitsbereichsdatenquelle des Modells herzustellen:  
  
    -   Um das aktuelle Benutzerkonto zu verwenden, wählen Sie **Aktueller Windows-Benutzer**aus.  
  
    -   Um ein anderes Benutzerkonto zu verwenden, wählen Sie **Anderer Windows-Benutzer**aus.  
  
         In der Regel ist dieser Benutzer Mitglied einer Rolle. Es ist kein Kennwort erforderlich. Das Konto kann nur im Kontext einer Excel-Verbindung mit der Arbeitsbereichsdatenbank verwendet werden.  
  
    -   Um eine Sicherheitsrolle zu verwenden, wählen Sie **Rolle**und anschließend mindestens eine Rolle im Listenfeld aus.  
  
         Sicherheitsrollen müssen mit dem Rollen-Manager definiert werden. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Rollen &#40;SSAS – tabellarisch&#41;](roles-ssas-tabular.md).  
  
3.  Um eine Perspektive aus dem Listenfeld **Perspektive** zu verwenden, wählen Sie die Perspektive aus.  
  
     Perspektiven (mit Ausnahme der Standardeinstellung) müssen im Dialogfeld Perspektiven definiert werden. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Perspektiven &#40;SSAS – tabellarisch&#41;](perspectives-ssas-tabular.md).  
  
> [!NOTE]  
>  Die PivotTable-Feldliste in Excel wird nicht automatisch aktualisiert, wenn Sie im Modell-Designer Änderungen am Modellprojekt vornehmen. Um die PivotTable-Feldliste zu aktualisieren, klicken Sie in Excel im Menüband **Optionen** auf **Aktualisieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [In Excel analysieren &#40;SSAS – tabellarisch&#41;](analyze-in-excel-ssas-tabular.md)  
  
  
