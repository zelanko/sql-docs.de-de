---
title: Übergeben von Parametern an Updategramms (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- nullvalue attribute
- passing parameters [SQLXML]
- parameters [SQLXML]
- updategrams [SQLXML], passing parameters
- null values [SQLXML]
ms.assetid: 2354e6e7-1860-471f-8711-4e374c5a4ed2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9097ed23a228a48500d9f40ca8f8e3b3f12b1ba0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113740"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a>Übergeben von Parametern an Updategrams (SQLXML 4.0)
  Updategrams sind Vorlagen. Daher können Sie ihnen Parameter übergeben. Weitere Informationen zum Übergeben von Parametern an Vorlagen finden Sie unter [Sicherheitsüberlegungen zu Updategramms &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md).  
  
 Mit Updategrams können Sie NULL als Parameterwert übergeben. Um den NULL-Parameterwert zu übergeben, geben Sie das `nullvalue`-Attribut an. Der Wert, der dem `nullvalue`-Attribut zugewiesen wird, wird dann als Parameterwert zur Verfügung gestellt. Updategrams behandeln diesen Wert als NULL.  
  
> [!NOTE]  
>  In `<sql:header>` und `<updg:header>` geben Sie den `nullvalue`-Wert als nicht qualifiziert an, während Sie den `<updg:sync>`-Wert in `nullvalue` als qualifiziert angeben (z. B. `updg:nullvalue`).  
  
## <a name="examples"></a>Beispiele  
 Um funktionierende Beispiele, die mit den folgenden Beispielen erstellen, müssen Sie die Anforderungen, die im angegebenen erfüllen [Anforderungen für die Ausführung von SQLXML-Beispielen](../../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
 Beachten Sie bevor Sie die updategrambeispiele verwenden Folgendes ein:  
  
-   Die Beispiele verwenden die Standardzuordnung (d. h. es ist kein Zuordnungsschema im Updategram angegeben). Weitere Beispiele für Updategrams, die Zuordnungsschemas verwenden, finden Sie unter [ein Mapping-Schema mit Anmerkungen angeben, in einem Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
### <a name="a-passing-parameters-to-an-updategram"></a>A. Übergeben von Parametern an ein Updategram  
 In diesem Beispiel ändert das Updategram den Nachnamen eines Angestellten in der HumanResources.Shift-Tabelle. An das Updategram werden zwei Parameter übergeben: ShiftID zur eindeutigen Identifizierung der Schicht und Name.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header>  
  <updg:param name="ShiftID"/>  
  <updg:param name="Name" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="$ShiftID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="$Name" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie das oben angegebene Updategram in Editor, und speichern Sie es als Datei unter UpdategramWithParameters.xml.  
  
2.  Bereiten Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs) in [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) das Updategram ausgeführt wird, indem Sie die folgenden Zeilen nach dem Hinzufügen der `cmd.Properties("Output Stream").Value = outStream`:  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value  
    cmd.Parameters.Append cmd.CreateParameter("@ShiftID",  2, 1,  0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@Name",   200, 1, 50, "New Name")  
    ```  
  
### <a name="b-passing-null-as-a-parameter-value-to-an-updategram"></a>B. Übergeben von NULL als Parameterwert an ein Updategram  
 Durch Ausführen eines Updategrams wird der Wert "isnull" dem Parameter zugewiesen, der auf NULL gesetzt werden soll. Das Updategram konvertiert den "isnulll"-Parameterwert in NULL und verarbeitet ihn entsprechend.  
  
 Das folgende Updategram legt einen Mitarbeitertitel auf NULL fest:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header nullvalue="isnull" >  
  <updg:param name="EmployeeID"/>  
  <updg:param name="ManagerID" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Employee EmployeeID="$EmployeeID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Employee ManagerID="$ManagerID" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie das oben angegebene Updategram in Editor, und speichern Sie es als Datei unter UpdategramPassingNullvalues.xml.  
  
2.  Bereiten Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs) in [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) das Updategram ausgeführt wird, indem Sie die folgenden Zeilen nach dem Hinzufügen der `cmd.Properties("Output Stream").Value = outStream`:  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberlegungen zu Updategramms &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
