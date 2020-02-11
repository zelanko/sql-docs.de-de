---
title: Perspektivische Darstellung (tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 6d2636c4-dae4-448f-a1d4-dbee739e177c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4704fc56ae1eacfb8481533c9d743afff80e923
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62757751"
---
# <a name="perspective-representation-tabular"></a>Perspektivische Darstellung (tabellarisch)
  Eine Perspektive ist ein Mechanismus, um das Modell zu vereinfachen oder einen kleineren Teil davon für die Clientanwendung zu fokussieren.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der perspektivischen Darstellung finden Sie unter [perspektivische Darstellung (tabellarisch)](perspective-representation-tabular.md) .  
  
> [!WARNING]  
>  Perspektiven sind kein Sicherheitsmechanismus; auf Objekte außerhalb der Perspektive kann immer noch vom Benutzer über andere Schnittstellen zugegriffen werden.  
  
## <a name="perspective-representation"></a>Perspektivendarstellung  
 Im Hinblick auf AMO-Objekte verfügt eine Perspektivendarstellung über eine 1:1-Zuordnungsbeziehung zu <xref:Microsoft.AnalysisServices.Perspective>, und es sind keine weiteren AMO-Hauptobjekte erforderlich.  
  
### <a name="perspective-in-amo"></a>Perspektive in AMO  
 Der folgende Codeausschnitt veranschaulicht, wie eine Perspektive in einem tabellarischen Modell erstellt wird. Das wichtigste Element in diesem Codeausschnitt ist perspectiveElements. Dieses Objekt ist eine grafische Darstellung aller Objekte im tabellarischen Modell, die für den Benutzer verfügbar gemacht werden. *perspectiveelements* enthält vier Spalten. in diesem Szenario sind nur die Spalten 1, 2 und 3 relevant. Spalte 1 enthält den Typ des angezeigten Elements: -elementTypeValue-. Spalte 2 enthält den vollständigen Namen des Elements, der u. U. analysiert werden muss, um das Element in die Perspektive einzufügen. Spalte 3 enthält das Kontrollkästchenelement -checkedElement-, das angibt, ob das Element Teil der Perspektive ist oder nicht.  
  
```  
  
private void updatePerspective_Click(  
                     AMO.Cube modelCube  
                  ,  DataGridView perspectiveElements  
                  ,  string updatedPerspectiveID  
             )  
{  
    //Update is done by delete first, create new and insert after  
    //if perspective doesn't exist then create first and insert after  
    updatedPerspectiveID = updatedPerspectiveID.Trim();  
    if (modelCube.Perspectives.Contains(updatedPerspectiveID))  
    {  
        modelCube.Perspectives.Remove(updatedPerspectiveID, true);  
        newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    AMO.Perspective currentPerspective = modelCube.Perspectives.Add(updatedPerspectiveID, updatedPerspectiveID);  
  
    foreach (DataGridViewRow currentDGVRow in perspectiveElements.Rows)  
    {  
        bool checkedElement = (bool)currentDGVRow.Cells[3].Value;  
        if (checkedElement)  
        {  
            string elementTypeValue = currentDGVRow.Cells[1].Value.ToString();  
            string elementNameValue = currentDGVRow.Cells[2].Value.ToString();  
            switch (elementTypeValue)  
            {  
                case "Column: Attribute":  
                case "Column: Calculated Column":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionAttributeName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Attributes.Contains(perspectiveDimensionAttributeName))  
                        {  
                            currentPerspectiveDimension.Attributes.Add(perspectiveDimensionAttributeName);  
                        }  
                    }  
                    break;  
                case "Hierarchy":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionHierarchyName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Hierarchies.Contains(perspectiveDimensionHierarchyName))  
                        {  
                            currentPerspectiveDimension.Hierarchies.Add(perspectiveDimensionHierarchyName);  
                        }  
                    }  
                    break;  
                case "Measure":  
                    {  
                        string perspectiveMeasureGroupName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string measureName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        string perspectiveMeasureName = string.Format("[Measures].[{0}]", measureName);  
                        AMO.PerspectiveCalculation currentPerspectiveCalculation = new AMO.PerspectiveCalculation(perspectiveMeasureName, AMO.PerspectiveCalculationType.Member);  
                        if (!currentPerspective.Calculations.Contains(perspectiveMeasureName))  
                        {  
                            currentPerspective.Calculations.Add(currentPerspectiveCalculation);  
                        }  
                        if (modelCube.MdxScripts["MdxScript"].CalculationProperties.Contains(string.Format("KPIs.[{0}]", measureName)))  
                        {//Current Measure is also a KPI ==> will be added to the KPIs collection of the perspective  
                            AMO.PerspectiveKpi currentPerspectiveKpi = new AMO.PerspectiveKpi(perspectiveMeasureName);  
                            if (!currentPerspective.Kpis.Contains(perspectiveMeasureName))  
                            {  
                                currentPerspective.Kpis.Add(currentPerspectiveKpi);  
                            }  
                        }  
                    }  
                    break;  
                default:  
                    break;  
            }  
        }  
    }  
  
    newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
    MessageBox.Show(String.Format("Perpective successfully updated."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
}  
  
```  
  
## <a name="amo2tabular-sample"></a>AMO2Tabular-Beispiel  
 Um jedoch einen Einblick in die Verwendung von AMO zur Erstellung und Bearbeitung von Perspektivendarstellungen zu gewinnen, können Sie den Quellcode im AMO2Tabular-Beispiel einsehen. Das Beispiel ist auf Codeplex verfügbar. Ein wichtiger Hinweis zum Code: Der Code wird nur zur Verdeutlichung für die logischen Konzepte bereitgestellt, die hier erläutert werden, und sollte nicht in einer Produktionsumgebung verwendet oder zu anderen als Lehrzwecken eingesetzt werden.  
  
  
