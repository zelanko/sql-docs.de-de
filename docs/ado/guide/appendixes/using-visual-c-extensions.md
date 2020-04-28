---
title: Verwenden von Visual C++-Erweiterungen | Microsoft-Dokumentation
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
ms.openlocfilehash: a9d60695bd033bfc83e3a091490f27f9432782c0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926455"
---
# <a name="visual-c-extensions"></a>Visual C++ Erweiterungen
## <a name="the-iadorecordbinding-interface"></a>Die IADORecordBinding-Schnittstelle
 Die Microsoft Visual C++ Erweiterungen für ADO-Zuordnungs-oder Bindungs Felder eines [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts zu C/C++-Variablen. Wenn sich die aktuelle Zeile des gebundenen **Recordsets** ändert, werden alle gebundenen Felder im **Recordset** in die C/C++-Variablen kopiert. Bei Bedarf werden die kopierten Daten in den deklarierten Datentyp der C/C++-Variablen konvertiert.

 Die **BindToRecordset** -Methode der **IADORecordBinding** -Schnittstelle bindet Felder an C/C++-Variablen. Die **AddNew** -Methode fügt dem gebundenen **Recordset**eine neue Zeile hinzu. Die **Update** -Methode füllt Felder in neuen Zeilen des **Recordsets**auf oder aktualisiert Felder in vorhandenen Zeilen mit dem Wert der C/C++-Variablen.

 Die **IADORecordBinding** -Schnittstelle wird durch das **Recordset** -Objekt implementiert. Sie müssen die Implementierung nicht selbst codieren.

## <a name="binding-entries"></a>Bindungs Einträge
 Die Visual C++ Erweiterungen für ADO-Karten Felder eines [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts zu C/C++-Variablen. Die Definition einer Zuordnung zwischen einem Feld und einer Variablen wird als *Bindungs Eintrag*bezeichnet. Makros stellen Bindungs Einträge für numerische Daten mit fester Länge und variabler Länge bereit. Die Bindungs Einträge und C/C++-Variablen werden in einer Klasse deklariert, die von der Visual C++ Extensions-Klasse **CADORecordBinding**abgeleitet ist. Die **CADORecordBinding** -Klasse wird intern durch die Bindungs Eintrags Makros definiert.

 ADO ordnet die Parameter in diesen Makros intern einer OLE DB **DBBINDING** -Struktur zu und erstellt ein **OLE DB** Accessorobjekt, um die Verschiebung und Konvertierung von Daten zwischen Feldern und Variablen zu verwalten. OLE DB definiert Daten, die aus drei Teilen bestehen: einem *Puffer* , in dem die Daten gespeichert werden. ein *Status* , der angibt, ob ein Feld erfolgreich im Puffer gespeichert wurde, oder wie die Variable im Feld wieder hergestellt werden soll. und die *Länge* der Daten. (Weitere Informationen finden Sie unter "beziehen [und Festlegen von Daten (OLE DB)](https://msdn.microsoft.com/4369708b-c9fb-4d48-a321-bf949b41a369)" in der OLE DB Programmierer-Referenz.)

## <a name="header-file"></a>Headerdatei
 Fügen Sie die folgende Datei in die Anwendung ein, um die Visual C++-Erweiterungen für ADO zu verwenden:

```cpp
#include <icrsint.h>
```

## <a name="binding-recordset-fields"></a>Binden von Recordsetfeldern

#### <a name="to-bind-recordset-fields-to-cc-variables"></a>So binden Sie Recordsetfelder an C/C++-Variablen

1.  Erstellen Sie eine von der **CADORecordBinding** -Klasse abgeleitete Klasse.

2.  Geben Sie die Bindungs Einträge und die entsprechenden C/C++-Variablen in der abgeleiteten Klasse an. Binden Sie die Bindungs Einträge zwischen **BEGIN_ADO_BINDING** und **END_ADO_BINDING** Makros. Beenden Sie die Makros nicht mit Kommas oder Semikolons. Entsprechende Trennzeichen werden automatisch von jedem Makro angegeben.

     Geben Sie einen Bindungs Eintrag für jedes Feld an, das einer C/C++-Variablen zugeordnet werden soll. Verwenden Sie einen geeigneten Member aus der **ADO_FIXED_LENGTH_ENTRY**-, **ADO_NUMERIC_ENTRY**-oder **ADO_VARIABLE_LENGTH_ENTRY** Familie von Makros.

3.  Erstellen Sie in Ihrer Anwendung eine Instanz der Klasse, die von **CADORecordBinding**abgeleitet wurde. Abrufen der **IADORecordBinding** -Schnittstelle aus dem **Recordset**. Anschließend können Sie die **BindToRecordset** -Methode aufrufen, um die **Recordsetfelder** an die C/C++-Variablen zu binden.

 Weitere Informationen finden Sie im [Beispiel für Visual C++ Erweiterungen](../../../ado/guide/appendixes/visual-c-extensions-example.md).

## <a name="interface-methods"></a>Schnittstellenmethoden
 Die **IADORecordBinding** -Schnittstelle verfügt über drei Methoden: **BindToRecordset**, **AddNew**und **Update**. Das einzige Argument für jede Methode ist ein Zeiger auf eine Instanz der Klasse, die von **CADORecordBinding**abgeleitet ist. Daher können die **AddNew** -Methode und die **Update** -Methode keinen der Parameter Ihrer ADO-Methoden namesakes angeben.

## <a name="syntax"></a>Syntax
 Die **BindToRecordset** -Methode ordnet die **Recordsetfelder** den C/C++-Variablen zu.

```cpp
BindToRecordset(CADORecordBinding *binding)
```

 Die **AddNew** -Methode ruft ihren Namespace, die ADO [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) -Methode, auf, um dem **Recordset**eine neue Zeile hinzuzufügen.

```cpp
AddNew(CADORecordBinding *binding)
```

 Die **Update** -Methode ruft ihren Namespace, die ADO- [Aktualisierungs](../../../ado/reference/ado-api/update-method.md) Methode, auf, um das **Recordset**zu aktualisieren.

```cpp
Update(CADORecordBinding *binding)
```

## <a name="binding-entry-macros"></a>Bindungs Eintrags Makros
 Bindungs Eintrags Makros definieren die Zuordnung eines **recordsetfelds** und einer Variablen. Ein Makro für den Anfang und das Ende begrenzt den Satz von Bindungs Einträgen.

 Familien von Makros werden für Daten mit fester Länge, z. b. **adDate** oder **adboolean**, bereitgestellt. numerische Daten, z. b. **adtinyint**, **adinteger**oder **adDouble**; und Daten variabler Länge, z. b. **adchar**, **adVarChar** oder **adVarBinary**. Alle numerischen Typen, mit Ausnahme von **advarnumeric**, sind auch Typen mit fester Länge. Jede Familie verfügt über unterschiedliche Sätze von Parametern, sodass Sie Bindungs Informationen ausschließen können, die nicht von Interesse sind.

 Weitere Informationen finden Sie unter [Anhang A: Datentypen](https://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6)der OLE DB Programmierer-Referenz.

### <a name="begin-binding-entries"></a>Binden von Einträgen beginnen
 **BEGIN_ADO_BINDING**(*Klasse*)

### <a name="fixed-length-data"></a>Daten mit fester Länge
 **ADO_FIXED_LENGTH_ENTRY**(*Ordinal, DataType, Buffer, Status, Modify*)

 **ADO_FIXED_LENGTH_ENTRY2**(*Ordinal, DataType, Buffer, Modify*)

### <a name="numeric-data"></a>Numerische Daten
 **ADO_NUMERIC_ENTRY**(*Ordinal, DataType, Buffer, Precision, Scale, Status, Modify*)

 **ADO_NUMERIC_ENTRY2**(*Ordinal, DataType, Buffer, Precision, Scale, Modify*)

### <a name="variable-length-data"></a>Daten variabler Länge
 **ADO_VARIABLE_LENGTH_ENTRY**(*Ordinal, Datentyp, Puffer, Größe, Status, Länge, ändern*)

 **ADO_VARIABLE_LENGTH_ENTRY2**(*Ordinal, DataType, Buffer, Size, Status, Modify*)

 **ADO_VARIABLE_LENGTH_ENTRY3**(*Ordinal, DataType, Buffer, Size, length, Modify*)

 **ADO_VARIABLE_LENGTH_ENTRY4**(*Ordinal, DataType, Buffer, Size, Modify*)

### <a name="end-binding-entries"></a>Bindungs Einträge beenden
 **END_ADO_BINDING**()

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Class*|Die Klasse, in der die Bindungs Einträge und die C/C++-Variablen definiert werden.|
|*Ordnungszahl*|Die Ordinalzahl des **recordsetfelds** , die der C/C++-Variablen entspricht.|
|*DataType*|Entsprechender ADO-Datentyp der C/C++-Variablen (Weitere Informationen finden Sie unter [datatypeer](../../../ado/reference/ado-api/datatypeenum.md) -Enumeration). Der Wert des **Recordset** -Felds wird bei Bedarf in diesen Datentyp konvertiert.|
|*Ert*|Der Name der C/C++-Variablen, in der das **Recordsetfeld** gespeichert wird.|
|*Größe*|Maximale Größe des *Puffers*in Bytes. Wenn der *Puffer* eine Zeichenfolge variabler Länge enthält, lassen Sie Raum für eine abschließende NULL-Werte zu.|
|*Status*|Der Name einer Variablen, die angibt, ob der Inhalt des *Puffers* gültig ist und ob die Konvertierung des Felds in den *Datentyp* erfolgreich war.<br /><br /> Die zwei wichtigsten Werte für diese Variable sind **adFldOK**, was bedeutet, dass die Konvertierung erfolgreich war. und **adFldNull**. Dies bedeutet, dass der Wert des Felds eine Variante vom Typ VT_NULL und nicht nur leer ist.<br /><br /> Mögliche Werte für den *Status* sind in der nächsten Tabelle "Statuswerte" aufgeführt.|
|*Änderung*|Boolesches Flag; TRUE gibt an, dass ADO das entsprechende **Recordsetfeld** mit dem im *Puffer*enthaltenen Wert aktualisieren darf.<br /><br /> Legen Sie den booleschen Parameter *Modify* auf true fest, damit ADO das gebundene Feld aktualisieren kann, und false, wenn Sie das Feld untersuchen, aber nicht ändern möchten.|
|*Genauigkeit*|Anzahl von Ziffern, die in einer numerischen Variablen dargestellt werden können.|
|*Skalieren*|Anzahl der Dezimalstellen in einer numerischen Variablen.|
|*Länge*|Der Name einer 4-Byte-Variablen, die die tatsächliche Länge der Daten im *Puffer*enthält.|

## <a name="status-values"></a>Statuswerte
 Der Wert der *Status* Variablen gibt an, ob ein Feld erfolgreich in eine Variable kopiert wurde.

 Beim Festlegen von Daten kann der *Status* auf **adFldNull** festgelegt werden, um anzugeben, dass das **Recordsetfeld** auf NULL festgelegt werden soll.

|Konstante|Wert|BESCHREIBUNG|
|--------------|-----------|-----------------|
|**adFldOK**|0|Es wurde ein Feldwert ungleich NULL zurückgegeben.|
|**adfldbadaccessor**|1|Die Bindung war ungültig.|
|**adfldcantconvertvalue**|2|Der Wert konnte aus anderen Gründen nicht konvertiert werden als Vorzeichen oder Datenüberlauf.|
|**adFldNull**|3|Gibt beim erhalten eines Felds an, dass ein NULL-Wert zurückgegeben wurde.<br /><br /> Gibt beim Festlegen eines Felds an, dass das Feld auf **null** festgelegt werden soll, wenn das Feld **null** selbst nicht codieren kann (z. b. ein Zeichen Array oder eine Ganzzahl).|
|**adfldtruncated**|4|Daten variabler Länge oder numerische Ziffern wurden abgeschnitten.|
|**adfldsignmismatch**|5|Der Wert ist signiert, und der Datentyp der Variablen ist nicht signiert.|
|**adflddataoverflow**|6|Der Wert ist größer als der Wert, der im Variablen Datentyp gespeichert werden kann.|
|**adfldcantcreate**|7|Unbekannter Spaltentyp und Feld sind bereits geöffnet.|
|**adfldunavailable**|8|Der Feldwert konnte nicht bestimmt werden, z. b. für ein neues, nicht zugewiesenes Feld ohne Standardwert.|
|**adfldpermissiondenied**|9|Keine Berechtigung zum Schreiben von Daten, wenn Sie aktualisiert werden.|
|**adfldintegrityverletzungs**|10|Beim Aktualisieren würde der Feldwert die Spalten Integrität verletzen.|
|**adfldschemaverletzung**|11|Beim Aktualisieren würde der Feldwert das Spalten Schema verletzen.|
|**adfldbadstatus**|12|Ungültiger Status Parameter beim Aktualisieren.|
|**adFldDefault**|13|Bei der Aktualisierung wurde ein Standardwert verwendet.|

## <a name="see-also"></a>Weitere Informationen
 [Beispiel für Visual C++ Erweiterungen](../../../ado/guide/appendixes/visual-c-extensions-example.md) [Visual C++ Extensions-Header](../../../ado/guide/appendixes/visual-c-extensions-header.md)
