---
title: DDL ausführen (Analysis Services-Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.f1
helpviewer_keywords:
- Analysis Services Execute DDL task
- DDL
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 115ee695d8e5ae509499850113851f7bc565f562
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190670"
---
# <a name="analysis-services-execute-ddl-task"></a>DDL ausführen (Analysis Services-Task)
  Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Task DDL ausführen führt DLL-Anweisungen (Data Definition Language, Datendefinitionssprache) aus, mit denen Miningmodelle und mehrdimensionale Objekte, wie z. B. Cubes und Dimensionen, erstellt, gelöscht oder geändert werden können. Beispielsweise kann mit einer DDL-Anweisung eine Partition im **Adventure Works** -Cube erstellt oder eine Dimension in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], der im Lieferumfang von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthaltenen Beispieldatenbank von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], gelöscht werden.  
  
 Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Task DDL ausführen stellt mithilfe eines Verbindungs-Managers von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder mit einem Projekt von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] her. Weitere Informationen finden Sie unter [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] schließt eine Reihe von Tasks ein, die Business Intelligence-Vorgänge ausführen, wie z. B. das Verarbeiten analytischer Objekte und das Ausführen von Data Mining-Vorhersageabfragen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu verwandten Business Intelligence-Tasks zu erhalten:  
  
-   [Analysis Services-Verarbeitungstask](analysis-services-processing-task.md)  
  
-   [Data Mining-Abfragetask](data-mining-query-task.md)  
  
## <a name="ddl-statements"></a>DDL-Anweisungen  
 Die DDL-Anweisungen werden als [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) dargestellt und in einen XMLA-Befehl (XML for Analysis) eingebunden.  
  
-   Mit ASSL werden eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und die darin enthaltenen Datenbanken und Datenbankobjekte definiert und beschrieben. Weitere Informationen finden Sie unter [Analysis Services Scripting Language &#40;ASSL&#41; Verweis](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
-   Bei XMLA handelt es sich um eine Befehlssprache, mit der Aktionsbefehle, wie z. B. Create, Alter oder Process, an eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]gesendet werden. Weitere Informationen finden Sie in der [XML for Analysis-Referenz &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md).  
  
 Wenn der DDL-Code in einer separaten Datei gespeichert ist, gibt der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Task DDL ausführen mithilfe eines Dateiverbindungs-Manager den Dateipfad an. Weitere Informationen finden Sie unter [File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 DDL-Anweisungen können Kennwörter und sonstige vertrauliche Informationen enthalten. Deshalb sollte für ein Paket, das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Tasks DDL ausführen enthält, die Paketschutzebene `EncryptAllWithUserKey` oder `EncryptAllWithPassword` verwendet werden. Weitere Informationen finden Sie unter [Integration Services-Pakete &#40;SSIS&#41;](../integration-services-ssis-packages.md).  
  
### <a name="ddl-examples"></a>DDL-Beispiele  
 Die folgenden drei DDL-Anweisungen wurden von Skripterstellungsobjekten in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], der im Lieferumfang von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthaltenen Beispieldatenbank von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], generiert.  
  
 Mit der folgenden DDL-Anweisung wird die **Höherstufungs** -Dimension gelöscht.  
  
```  
<Delete xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 Mit der folgenden DDL-Anweisung wird der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] -Cube verarbeitet.  
  
```  
<Batch xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 Mit der folgenden DDL-Anweisung wird das **Forecasting** -Miningmodell erstellt.  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
 Die folgenden drei DDL-Anweisungen wurden von Skripterstellungsobjekten in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], der im Lieferumfang von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthaltenen Beispieldatenbank von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], generiert.  
  
 Mit der folgenden DDL-Anweisung wird die **Höherstufungs** -Dimension gelöscht.  
  
```  
<Delete xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 Mit der folgenden DDL-Anweisung wird der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] -Cube verarbeitet.  
  
```  
<Batch xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 Mit der folgenden DDL-Anweisung wird das **Forecasting** -Miningmodell erstellt.  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
## <a name="configuration-of-the-analysis-services-execute-ddl-task"></a>Konfiguration des Analysis Services-Tasks "DDL ausführen"  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Analysis Services-Task DDL-Task-Editor &#40;Seite "Allgemein"&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Analysis Services-Task DDL-Task-Editor &#40;Seite "DDL"&#41;](../analysis-services-execute-ddl-task-editor-ddl-page.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-execute-ddl-task"></a>Programmgesteuerte Konfiguration des Analysis Services-Tasks "DDL ausführen"  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften anzuzeigen:  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
  
