---
title: Übergeben von Parametern an Updategrams (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nullvalue attribute
- passing parameters [SQLXML]
- parameters [SQLXML]
- updategrams [SQLXML], passing parameters
- null values [SQLXML]
ms.assetid: 2354e6e7-1860-471f-8711-4e374c5a4ed2
author: rothja
ms.author: jroth
ms.openlocfilehash: d9e699ea80253934ecc6f3ce744feaed6fd6a392
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047469"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a>Übergeben von Parametern an Updategrams (SQLXML 4.0)
  Updategrams sind Vorlagen. Daher können Sie ihnen Parameter übergeben. Weitere Informationen zum Übergeben von Parametern an Vorlagen finden Sie unter [Updategram Security Überlegungen &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md).  
  
 Mit Updategrams können Sie NULL als Parameterwert übergeben. Um den NULL-Parameterwert zu übergeben, geben Sie das `nullvalue`-Attribut an. Der Wert, der dem `nullvalue`-Attribut zugewiesen wird, wird dann als Parameterwert zur Verfügung gestellt. Updategrams behandeln diesen Wert als NULL.  
  
> [!NOTE]  
>  In `<sql:header>` und `<updg:header>` geben Sie den `nullvalue`-Wert als nicht qualifiziert an, während Sie den `<updg:sync>`-Wert in `nullvalue` als qualifiziert angeben (z. B. `updg:nullvalue`).  
  
## <a name="examples"></a>Beispiele  
 Wenn Sie in den folgenden Beispielen funktionierende Beispiele erstellen möchten, müssen Sie die unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../sqlxml/requirements-for-running-sqlxml-examples.md)angegebenen Anforderungen erfüllen.  
  
 Beachten Sie vor der Verwendung der Update Gram-Beispiele Folgendes:  
  
-   Die Beispiele verwenden die Standardzuordnung (d. h. es ist kein Zuordnungsschema im Updategram angegeben). Weitere Beispiele für Update grams, die Mapping-Schemas verwenden, finden Sie unter [Angeben eines Mappingschemas mit Anmerkungen in einem Update Gram &#40;SQLXML 4,0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
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
  
2.  Bereiten Sie das SQLXML 4,0-Testskript (Sqlxml4test. vb) [mithilfe von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) zum Ausführen des Update grams vor, indem Sie die folgenden Zeilen nach Hinzufügen `cmd.Properties("Output Stream").Value = outStream` :  
  
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
  
2.  Bereiten Sie das SQLXML 4,0-Testskript (Sqlxml4test. vb) [mithilfe von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) zum Ausführen des Update grams vor, indem Sie die folgenden Zeilen nach Hinzufügen `cmd.Properties("Output Stream").Value = outStream` :  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
