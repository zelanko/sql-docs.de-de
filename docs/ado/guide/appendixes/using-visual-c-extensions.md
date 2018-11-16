---
title: Mithilfe von Visual C++-Erweiterungen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ [ADO], using VC++ extensions
- ADO, Visual C++
ms.assetid: ff759185-df41-4507-8d12-0921894ffbd9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aeae626f924776092bc8f6652e716747768b689c
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350524"
---
# <a name="visual-c-extensions"></a>Visual C++-Erweiterungen
## <a name="the-iadorecordbinding-interface"></a>Die IADORecordBinding-Schnittstelle
 Die Microsoft Visual C++-Erweiterungen für ADO-Zuordnung oder Bindung Felder einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt, das C/C++-Variablen. Wenn die Grenze der aktuellen Zeile **Recordset** geändert wird, die gebundene Felder in der **Recordset** in die C/C++-Variablen kopiert werden. Falls erforderlich, werden die kopierten Daten in den deklarierten Typ des C/C++-Variablen konvertiert.

 Die **BindToRecordset** Methode der **IADORecordBinding** Schnittstelle bindet Felder an C/C++-Variablen. Die **AddNew** Methode fügt eine neue Zeile mit dem Grenzwert **Recordset**. Die **Update** Methode füllt die Felder in neue Zeilen mit den **Recordset**, oder Felder in vorhandene Zeilen aktualisiert, mit dem Wert der C/C++-Variablen.

 Die **IADORecordBinding** Schnittstelle wird implementiert, indem die **Recordset** Objekt. Sie die Implementierung nicht selbst programmieren.

## <a name="binding-entries"></a>Binden von Einträgen
 Visual C++-Erweiterungen für ADO Zuordnen von Feldern von einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt, das C/C++-Variablen. Die Definition einer Zuordnung zwischen einem Feld und eine Variable wird aufgerufen, eine *Bindungsreihenfolge*. Makros werden Bindungseinträge für numerische fester Länge und variabler Länge, die Daten bereitgestellt. Die Bindungseinträge und die C/C++-Variablen werden in einer von der Visual C++-Erweiterungen-Klasse abgeleiteten Klasse deklariert **CADORecordBinding**. Die **CADORecordBinding** Klasse wird intern durch die einstiegsmakros für die Bindung definiert.

 ADO ordnet die Parameter in diese Makros intern eine OLE DB **DBBINDING** strukturieren und erstellt einen OLE DB- **Accessor** Objekt, um das Verschieben und die Konvertierung von Daten zwischen Felder und Variablen verwalten. OLE DB definiert die Daten als besteht aus drei Teilen: ein *Puffer* wo die Daten gespeichert werden; eine *Status* , der angibt, ob ein Feld wurde erfolgreich im Puffer gespeichert wurde oder wie die Variable wiederhergestellt werden soll das Feld sein. und die *Länge* der Daten. (Finden Sie unter [abrufen und Einfügen der Daten (OLE DB)](https://msdn.microsoft.com/4369708b-c9fb-4d48-a321-bf949b41a369)in der OLE DB Programmer's Reference, Weitere Informationen.)

## <a name="header-file"></a>Header-Datei
 Schließen Sie die folgende Datei, in Ihrer Anwendung, um die Visual C++-Erweiterungen für ADO verwenden:

```cpp
#include <icrsint.h>
```

## <a name="binding-recordset-fields"></a>Binden des Recordset-Feldern

#### <a name="to-bind-recordset-fields-to-cc-variables"></a>So binden Sie Recordset-Feldern an C/C++-Variablen

1.  Erstellen Sie eine Klasse, die von abgeleiteten der **CADORecordBinding** Klasse.

2.  Geben Sie die Bindungseinträge und entsprechende C-/C++-Variablen in der abgeleiteten Klasse. Die Bindungseinträge zwischen Klammer **BEGIN_ADO_BINDING** und **END_ADO_BINDING** Makros. Beenden Sie die Makros, die mit Kommas oder Semikolons nicht. Entsprechende Trennzeichen werden automatisch durch die einzelnen Makros angegeben.

     Geben Sie ein Bindungseintrag für jedes Feld, eine C/C++-Variable zugeordnet werden soll. Verwenden Sie ein geeignetes Mitglied aus der **ADO_FIXED_LENGTH_ENTRY**, **ADO_NUMERIC_ENTRY**, oder **ADO_VARIABLE_LENGTH_ENTRY** Familie von Makros.

3.  Erstellen Sie in Ihrer Anwendung eine Instanz der abgeleiteten Klasse von **CADORecordBinding**. Abrufen der **IADORecordBinding** -Schnittstelle aus der **Recordset**. Rufen Sie dann die **BindToRecordset** Methode zum Binden der **Recordset** Felder zu den C-/C++-Variablen.

 Weitere Informationen finden Sie unter den [Visual C++-Erweiterungen – Beispiel](../../../ado/guide/appendixes/visual-c-extensions-example.md).

## <a name="interface-methods"></a>Schnittstellenmethoden
 Die **IADORecordBinding** Schnittstelle verfügt über drei Methoden: **BindToRecordset**, **AddNew**, und **Update**. Das einzige Argument für jede Methode ist ein Zeiger auf eine Instanz der abgeleiteten Klasse von **CADORecordBinding**. Aus diesem Grund die **AddNew** und **Update** Methoden können nicht angeben, die Parameter, der die ADO-Methoden gleichen Namens.

## <a name="syntax"></a>Syntax
 Die **BindToRecordset** Methode ordnet die **Recordset** Felder mit C/C++-Variablen.

```cpp
BindToRecordset(CADORecordBinding *binding)
```

 Die **AddNew** Methode aufruft, die gleichnamige, das ADO [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) Methode, um eine neue Zeile hinzuzufügen. die **Recordset**.

```cpp
AddNew(CADORecordBinding *binding)
```

 Die **aktualisieren** Methode aufruft, die gleichnamige, das ADO [aktualisieren](../../../ado/reference/ado-api/update-method.md) Methode zum Aktualisieren der **Recordset**.

```cpp
Update(CADORecordBinding *binding)
```

## <a name="binding-entry-macros"></a>Einstiegsmakros für Bindung
 Einstiegsmakros für die Bindung definiert die Zuordnung von einem **Recordset** Feld und eine Variable. Ein Makro Anfangs- und Enddatumsangaben begrenzt die Anzahl der Einträge zu binden.

 Familien von Makros werden für Daten mit fester Länge, bereitgestellt, z. B. **AdDate** oder **AdBoolean**; numerische Daten, z. B. **AdTinyInt**, **AdInteger**, oder **AdDouble**; und Daten mit variabler Länge, wie z. B. **AdChar**, **AdVarChar** oder **AdVarBinary**. Alle numerischen Typen, mit Ausnahme von **AdVarNumeric**, sind auch Typen mit fester Länge. Jede Familie hat unterschiedliche Sätze von Parametern, sodass Sie Bindungsinformationen ausschließen können, die nicht von Interesse ist.

 Weitere Informationen finden Sie unter [Anhang A: Datentypen](https://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6), von der OLE DB Programmer's Reference.

### <a name="begin-binding-entries"></a>Binden Einträge zu beginnen
 **BEGIN_ADO_BINDING**(*Klasse*)

### <a name="fixed-length-data"></a>Daten fester Länge
 **ADO_FIXED_LENGTH_ENTRY**(*Ordinalzahl "," DataType "," Puffer "," Status ändern*)

 **ADO_FIXED_LENGTH_ENTRY2**(*Ordnungszahl, Datentyp, Puffer ändern*)

### <a name="numeric-data"></a>Numerische Daten
 **ADO_NUMERIC_ENTRY**(*Ordnungszahl, Datentyp, Puffer, Genauigkeit, Skalierung, Status ändern*)

 **ADO_NUMERIC_ENTRY2**(*Ändern der Ordnungszahl "," DataType "," Puffer "," Precision, Scale,*)

### <a name="variable-length-data"></a>Daten mit variabler Länge
 **ADO_VARIABLE_LENGTH_ENTRY**(*Ordnungszahl, Datentyp, Puffer, Größe, Status, Länge ändern*)

 **ADO_VARIABLE_LENGTH_ENTRY2**(*Ordnungszahl "," DataType "," Puffer "," Größe "," Status ändern*)

 **ADO_VARIABLE_LENGTH_ENTRY3**(*Ordnungszahl, Datentyp, Puffer, Größe, Länge ändern*)

 **ADO_VARIABLE_LENGTH_ENTRY4**(*Ordinalzahl "," DataType "," Puffer "," Größe ändern*)

### <a name="end-binding-entries"></a>Binden Einträge End
 **END_ADO_BINDING**()

|Parameter|Description|
|---------------|-----------------|
|*Klasse*|Klasse, die in der die Bindungseinträge und die C/C++-Variablen definiert werden.|
|*Ordinal*|Ordnungszahl, beginnend mit 1, der die **Recordset** Feld entspricht der C/C++-Variablen.|
|*DataType*|Entsprechende ADO-Datentyp, der C/C++-Variablen (finden Sie unter [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) eine Liste gültiger Datentypen). Der Wert des der **Recordset** Feld wird auf diesen Datentyp konvertiert werden, falls erforderlich.|
|*Buffer*|Name der C/C++-Variablen, in denen die **Recordset** Feld gespeichert werden sollen.|
|*Größe*|Maximale Größe in Byte der *Puffer*. Wenn *Puffer* enthält eine Zeichenfolge variabler Länge, lassen Sie Platz für eine abschließende 0 (null).|
|*Status*|Name einer Variablen, die angibt, ob der Inhalt des *Puffer* gültig sind, und gibt an, ob die Konvertierung des Felds, *DataType* war erfolgreich.<br /><br /> Die beiden wichtigsten Werte für diese Variable sind **AdFldOK**, was bedeutet, dass die Konvertierung erfolgreich war und **AdFldNull**, was bedeutet, dass den Wert des Felds wäre eine Variante des Typs VT_NULL und nicht nur leer.<br /><br /> Mögliche Werte für *Status* finden Sie in der folgenden Tabelle, "Status-Werte."|
|*Ändern*|Boolesches Flag, das; Wenn TRUE, gibt ADO kann zum Aktualisieren der entsprechenden **Recordset** mit dem Wert im Feld *Puffer*.<br /><br /> Die mit einem booleschen Wert *ändern* Parameter auf "true", Aktivieren von ADO zum Aktualisieren von des gebundenen Felds zugeordnet ist, und FALSE, wenn Sie den überprüfen, jedoch nicht ändern möchten.|
|*Genauigkeit*|Anzahl der Ziffern, die in einer numerischen Variablen dargestellt werden kann.|
|*Dezimalstellen*|Die Anzahl der Dezimalstellen in einer numerischen Variablen.|
|*Länge*|Name einer 4-Byte-Variablen, die die tatsächliche Länge der Daten in enthält *Puffer*.|

## <a name="status-values"></a>Statuswerte
 Der Wert des der *Status* Variable gibt an, ob ein Feld auf eine Variable wurde erfolgreich kopiert wurde.

 Beim Festlegen der Daten, *Status* kann festgelegt werden, um **AdFldNull** an, dass die **Recordset** Feld auf Null.

|Konstante|Wert|Description|
|--------------|-----------|-----------------|
|**adFldOK**|0|Es wurde ein Feldwert ungleich Null-zurückgegeben.|
|**adFldBadAccessor**|1|Bindung war ungültig.|
|**adFldCantConvertValue**|2|Wert konnte nicht für den Datenüberlauf stimmt nicht überein oder Daten konvertiert werden.|
|**adFldNull**|3|Wenn ein Feld abrufen zu können, gibt Sie an, dass ein null-Wert zurückgegeben wurde.<br /><br /> Wenn Sie ein Feld festlegen, gibt an, das Feld sollte festgelegt werden, um **NULL** Wenn das Feld kann nicht codiert **NULL** selbst (z. B. ein Array von Zeichen oder eine ganze Zahl).|
|**adFldTruncated**|4|Daten mit variabler Länge oder die Ziffern wurden abgeschnitten.|
|**adFldSignMismatch**|5|Wert ist signiert und Datentyp der Variablen ohne Vorzeichen.|
|**adFldDataOverFlow**|6|Wert ist größer als die in den Datentyp der Variablen gespeichert werden können.|
|**adFldCantCreate**|7|Unbekannter Spaltentyp und Feld bereits geöffnet.|
|**adFldUnavailable**|8|Wert des Felds konnte nicht bestimmt werden – z. B. auf ein neues, nicht zugewiesene Feld hat keinen Standardwert.|
|**adFldPermissionDenied**|9|Bei der Aktualisierung keine Berechtigung zum Schreiben von Daten.|
|**adFldIntegrityViolation**|10|Bei der Aktualisierung würde Spaltenintegrität Feldwert verletzt werden.|
|**adFldSchemaViolation**|11|Bei der Aktualisierung würde Spaltenschema Feldwert verletzt werden.|
|**adFldBadStatus**|12|Bei der Aktualisierung ungültigen Status-Parameter.|
|**adFldDefault**|13|Bei der Aktualisierung wurde ein Standardwert verwendet.|

## <a name="see-also"></a>Siehe auch
 [Visual C++-Erweiterungen – Beispiel](../../../ado/guide/appendixes/visual-c-extensions-example.md) [Visual C++-Erweiterungsheader](../../../ado/guide/appendixes/visual-c-extensions-header.md)
