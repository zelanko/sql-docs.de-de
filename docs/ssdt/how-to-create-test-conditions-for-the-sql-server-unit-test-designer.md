---
title: 'Gewusst wie: Erstellen von Testbedingungen für den SQL Server-Komponententest-Designer | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 48076062-1ef5-419a-8a55-3c7b4234cc35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c0fe82226d1c4de82883498ba92893ec98fc7b05
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681968"
---
# <a name="how-to-create-test-conditions-for-the-sql-server-unit-test-designer"></a>Vorgehensweise: Erstellen von Testbedingungen für den SQL Server-Komponententest-Designer
Mit der erweiterbaren [TestCondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx)-Klasse können neue Testbedingungen erstellt werden. Beispielsweise können Sie eine neue Testbedingung erstellen, mit der die Anzahl der Spalten oder die Werte in einem Resultset überprüft werden.  
  
## <a name="to-create-a-test-condition"></a>So erstellen Sie eine Testbedingung  
Im folgenden Verfahren wird erläutert, wie Sie eine Testbedingung erstellen, die im SQL Server-Komponententest-Designer angezeigt wird.  
  
1.  Erstellen Sie in Visual Studio ein Klassenbibliotheksprojekt.  
  
2.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**.  
  
3.  Klicken Sie auf die Registerkarte **.NET**.  
  
4.  Klicken Sie in der Liste **Komponentenname** auf **System.ComponentModel.Composition** und dann auf **OK**.  
  
5.  Fügen Sie die erforderlichen Assemblyverweise hinzu. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Verweis hinzufügen**. Klicken Sie auf **Durchsuchen**, und navigieren Sie zum Ordner „C:\Programme (x86)\\Microsoft SQL Server\110\DAC\Bin“. Wählen Sie „Microsoft.Data.Tools.Schema.Sql.dll“ aus, klicken Sie auf „Hinzufügen“, und klicken Sie dann auf „OK“.  
  
6.  Klicken Sie im Menü **Projekt** auf **Projekt entladen**.  
  
7.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **<project name>.csproj bearbeiten** aus.  
  
8.  Fügen Sie nach dem Import von Microsoft.CSharp.targets folgende Import-Anweisungen hinzu:  
  
    ```  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' == ''" />  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' != ''" />  
    ```  
  
9. Speichern Sie die Datei, und schließen Sie sie. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Projekt erneut laden** aus.  
  
10. Leiten Sie die Klasse von der [TestCondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx)-Klasse ab.  
  
11. Signieren Sie die Assembly mit einem starken Namen. Weitere Informationen finden Sie unter [Gewusst wie: Signieren einer Assembly mit einem starken Namen](http://msdn.microsoft.com/library/xc31ft41.aspx).  
  
12. Erstellen Sie die Klassenbibliothek.  
  
13. Bevor Sie die neue Testbedingung verwenden können, müssen Sie die signierte Assembly in den folgenden Ordner kopieren: „%Programme%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions“. Wenn der Ordner nicht vorhanden ist, erstellen Sie ihn. Sie müssen auf Ihrem Computer über Administratorprivilegien verfügen, um Daten in dieses Verzeichnis zu kopieren.  
  
14. Installieren Sie die Testbedingung. Weitere Informationen finden Sie unter [Benutzerdefinierte Testbedingungen für SQL Server-Komponententests](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md).  
  
15. Fügen Sie dem Projekt einen neuen SQL Server-Komponententest hinzu, um einen Verweis auf die Testbedingung zu erstellen, die dem Projekt hinzugefügt werden soll. Sie können manuell einen Verweis auf die Testbedingungsassembly im Projekt hinzufügen. Laden Sie den Designer nach diesem Schritt neu.  
  
    > [!NOTE]  
    > Zum Erstellen des Verweises muss eine Testklasse hinzugefügt werden. Nachdem der Verweis hinzugefügt wurde, können Sie die Testklasse löschen.  
  
Im folgenden Beispiel erstellen Sie eine einfache Testbedingung, mit der die Anzahl der im Resultset zurückgegebenen Spalten überprüft wird. Mit dieser einfachen Testbedingung können Sie sicherstellen, dass der Vertrag für eine gespeicherte Prozedur richtig ist.  
  
```  
using System;  
using System.ComponentModel;  
using System.Data;  
using System.Data.Common;  
using Microsoft.Data.Tools.Schema.Sql.UnitTesting;  
using Microsoft.Data.Tools.Schema.Sql.UnitTesting.Conditions;  
  
namespace Ssdt.Samples.SqlUnitTesting  
{  
  
    [ExportTestCondition("ResultSet Column Count", typeof(ResultSetColumnCountCondition))]  
    public class ResultSetColumnCountCondition : TestCondition  
    {  
        private int _resultSet;  
        private int _count;  
        private int _batch;  
  
        public ResultSetColumnCountCondition()  
        {  
            _resultSet = 1;  
            _count = 0;  
            _batch = 1;  
        }  
  
        // method you need to override  
        // to perform the condition verification  
        public override void Assert(DbConnection validationConnection, SqlExecutionResult[] results)  
        {  
            // call base for parameter validation  
            base.Assert(validationConnection, results);  
  
            // verify batch exists  
            if (results.Length < _batch)  
                throw new DataException(String.Format("Batch {0} does not exist", _batch));  
  
            SqlExecutionResult result = results[_batch - 1];  
  
            // verify resultset exists  
            if (result.DataSet.Tables.Count < ResultSet)  
                throw new DataException(String.Format("ResultSet {0} does not exist", ResultSet));  
  
            DataTable table = result.DataSet.Tables[ResultSet - 1];  
  
            // actual condition verification  
            // verify resultset column count matches expected  
            if (table.Columns.Count != Count)  
                throw new DataException(String.Format(  
                    "ResultSet {0}: {1} columns did not match the {2} columns expected",  
                    ResultSet, table.Columns.Count, Count));  
        }  
  
        // this method is called to provide the string shown in the  
        // test conditions panel grid describing what the condition tests  
        public override string ToString()  
        {  
            return String.Format(  
                "Condition fails if ResultSet {0} does not contain {1} columns",  
                ResultSet, Count);  
        }  
  
        // below are the test condition properties  
        // that are exposed to the user in the property browser  
        #region Properties  
  
        // property specifying the resultset for which  
        // you want to check the column count  
        [Category("Test Condition")]  
        [DisplayName("ResultSet")]  
        [Description("ResultSet Number")]  
        public int ResultSet  
        {  
            get { return _resultSet; }  
  
            set  
            {  
                //basic validation  
                if (value < 1)  
                    throw new ArgumentException("ResultSet cannot be less than 1");  
  
                _resultSet = value;  
            }  
        }  
  
        // property specifying  
        // expected column count  
        [Category("Test Condition")]  
        [DisplayName("Count")]  
        [Description("Column Count")]  
        public int Count  
        {  
            get { return _count; }  
  
            set  
            {  
                //basic validation  
                if (value < 0)  
                    throw new ArgumentException("Count cannot be less than 0");  
  
                _count = value;  
            }  
        }  
  
        #endregion  
    }  
}  
```  
  
Die Klasse für die benutzerdefinierte Testbedingung erbt von der [TestCondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx)-Basisklasse. Da die benutzerdefinierte Testbedingung über zusätzliche Eigenschaften verfügt, können Benutzer die Bedingung nach der Installation im Eigenschaftenfenster konfigurieren.  
  
[ExportTestConditionAttribute](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.exporttestconditionattribute(v=vs.103).aspx) muss Klassen zur Erweiterung von [TestCondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx) hinzugefügt werden. Durch dieses Attribut kann die Klasse von SQL Server Data Tools ermittelt und während des Entwurfs und der Ausführung von Komponententests verwendet werden. Das Attribut verwendet zwei Parameter:  
  
|Attributparameter|Position|und Beschreibung|  
|-----------------------|------------|---------------|  
|DisplayName|1|Identifiziert die Zeichenfolge im Kombinationsfeld Testbedingungen. Dieser Name muss eindeutig sein. Wenn zwei Bedingungen über denselben Anzeigenamen verfügen, wird die erste gefundene Bedingung angezeigt, und im Fehler-Manager von Visual Studio wird eine Warnung ausgegeben.|  
|ImplementingType|2|Dieser Parameter wird verwendet, um die Erweiterung eindeutig zu identifizieren. Er muss in Anpassung an den Typ geändert werden, für den das Attribut verwendet wird. In diesem Beispiel wird der Typ **ResultSetColumnCountCondition** verwendet. Verwenden Sie daher **typeof(ResultSetColumnCountCondition)**. Falls Sie den Typ **NewTestCondition** verwenden, verwenden Sie **typeof(NewTestCondition)**.|  
  
In diesem Beispiel fügen Sie zwei Eigenschaften hinzu. Benutzer der benutzerdefinierten Testbedingung können die ResultSet-Eigenschaft verwenden, um das Resultset anzugeben, dessen Spaltenanzahl überprüft werden soll. Anschließend kann mit der Count-Eigenschaft die erwartete Spaltenanzahl angegeben werden.  
  
Für jede Eigenschaft werden drei Attribute hinzugefügt:  
  
-   Der Kategoriename, durch den die Organisation von Eigenschaften unterstützt wird.  
  
-   Der Anzeigename der Eigenschaft.  
  
-   Eine Beschreibung der Eigenschaft.  
  
Die Eigenschaften werden überprüft, um sicherzustellen, dass der Wert der ResultSet-Eigenschaft nicht kleiner als 1 und dass der Wert der Count-Eigenschaft größer als 0 ist.  
  
Mit der Assert-Methode wird die primäre Aufgabe der Testbedingung ausgeführt. Sie überschreiben die Assert-Methode, um zu überprüfen, ob die erwartete Bedingung erfüllt ist. Diese Methode bietet zwei Parameter:  
  
-   Der erste Parameter entspricht der zur Überprüfung der Testbedingung verwendeten Datenbankverbindung.  
  
-   Der zweite, wichtigere Parameter ist das Ergebnisarray, das für jeden ausgeführten Batch ein einzelnes Arrayelement zurückgibt.  
  
Für jedes Testskript wird nur ein einzelner Batch unterstützt. Daher wird durch Testbedingungen immer das erste Arrayelement überprüft. Das Arrayelement enthält ein Dataset, das wiederum die zurückgegebenen Resultsets für das Testskript enthält. In diesem Beispiel wird vom Code überprüft, ob die Datentabelle im Dataset die geeignete Anzahl von Spalten enthält. Weitere Informationen finden Sie unter "DataSet".  
  
Sie müssen die Klassenbibliothek festlegen, die die zu signierende Testbedingung enthält. Verwenden Sie dazu die Projekteigenschaften auf der Registerkate Signierung.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Benutzerdefinierte Testbedingungen für SQL Server-Komponententests](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
  
