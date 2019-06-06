---
title: Append-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Append
helpviewer_keywords:
- Append method [ADO]
ms.assetid: f8a9bbed-ba9c-4698-945d-317ad22d2e92
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 987b7d7006ff448a92eee1926a2c60c3b7ae039e
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696676"
---
# <a name="append-method-ado"></a>Append-Methode (ADO)
Fügt ein Objekt einer Auflistung an. Wenn die Auflistung [Felder](../../../ado/reference/ado-api/fields-collection-ado.md), ein neues [Feld](../../../ado/reference/ado-api/field-object.md) Objekt kann erstellt werden, bevor es der Auflistung angehängt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
collection.Append object  
fields.Append Name, Type, DefinedSize, Attrib, FieldValue  
```  
  
#### <a name="parameters"></a>Parameter  
 *collection*  
 Ein Auflistungsobjekt.  
  
 *fields*  
 Ein **Felder** Auflistung.  
  
 *object*  
 Eine Objektvariable, die das-Objekt anzufügenden darstellt.  
  
 *Name*  
 Ein **Zeichenfolge** -Wert, der den Namen des neuen enthält **Feld** Objekt, und muss nicht der gleiche Namen wie jedes andere Objekt in *Felder*.  
  
 *Typ*  
 Ein [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) Wert, dessen Standardwert **AdEmpty**, der den Datentyp des neuen Felds angibt. Die folgenden Datentypen werden nicht unterstützt, die für ADO und sollte nicht werden verwendet, wenn anfügen neuer Felder zu einer [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md): **AdIDispatch**, **AdIUnknown**, **AdVariant**.  
  
 *DefinedSize*  
 Optional. Ein **lange** Wert, der die definierte Größe in Zeichen oder Bytes, des neuen Felds darstellt. Der Standardwert für diesen Parameter wird von abgeleiteten *Typ*. Felder mit einem *DefinedSize* größer als 255 Byte als Spalten variabler Länge behandelt werden. Der Standardwert für *DefinedSize* ist nicht angegeben.  
  
 *Attrib*  
 Optional. Ein [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) Wert, dessen Standardwert **AdFldDefault**, die Attribute für das neue Feld angibt. Wenn dieser Wert nicht angegeben ist, wird das Feld enthalten Attribute, die von abgeleiteten *Typ*.  
  
 *FieldValue*  
 Optional. Ein **Variant** , das den Wert für das neue Feld darstellt. Wenn nicht angegeben, wird das Feld einen null-Wert angefügt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="parameters-collection"></a>Parameters-Auflistung  
 Müssen Sie festlegen, die [Typ](../../../ado/reference/ado-api/type-property-ado.md) Eigenschaft eine [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt vor dem Anfügen, damit die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung. Wenn Sie einen Datentyp mit variabler Länge auswählen, müssen Sie auch Festlegen der [Größe](../../../ado/reference/ado-api/size-property-ado-parameter.md) Eigenschaft mit einem Wert größer als 0 (null).  
  
 Beschreiben der Parameter selbst minimiert die Aufrufe an den Anbieter und aus diesem Grund verbessert die Leistung bei der Verwendung von gespeicherten Prozeduren oder parametrisierte Abfragen. Allerdings müssen Sie wissen, die Eigenschaften der Parameter der gespeicherten Prozedur zugeordnet oder einer parametrisierten Abfrage, die Sie aufrufen möchten.  
  
 Verwenden Sie die [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) Methode zum Erstellen **Parameter** Objekte und die entsprechenden Einstellungen und die Verwendung der **Anfügen** Methode zum Hinzufügen der [ Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung. Dadurch können Sie festlegen und Zurückgeben von Werten ohne den Anbieter für die Parameterinformationen aufrufen. Wenn Sie an einen Anbieter schreiben, die keine Parameterinformationen enthält, müssen Sie diese Methode verwenden, um manuell Auffüllen der **Parameter** Auflistung, um den Parameter verwenden.  
  
## <a name="fields-collection"></a>Fields-Sammlung  
 Die *FieldValue* Parameter ist nur gültig, beim Hinzufügen einer **Feld** -Objekt eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekts nicht auf eine **Recordset** Objekt. Mit einem **Datensatz** Objekt ist, können Sie fügen Felder und Werte gleichzeitig bereitstellen. Mit einer **Recordset** Objekt ist, müssen Sie die Felder, die beim Erstellen der **Recordset** ist geschlossen, und öffnen Sie dann die **Recordset** und die Felder Werte zuzuweisen.  
  
> [!NOTE]
>  Für den neuen **Feld** Objekte, die angefügt wurden die **Felder** Auflistung von eine **Datensatz** -Objekt, das [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft muss festgelegt werden vor allen anderen **Feld** Eigenschaften können angegeben werden. Zuerst, einen bestimmten Wert für die **Wert** Eigenschaft zugewiesen und [Update](../../../ado/reference/ado-api/update-method.md) auf die **Felder** Sammlung mit dem Namen. Klicken Sie dann auf andere Eigenschaften wie z. B. [Typ](../../../ado/reference/ado-api/type-property-ado.md) oder [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) zugegriffen werden kann. **Feld** Objekte die folgenden Datentypen (**DataTypeEnum**) kann nicht angefügt werden, um die **Felder** Auflistung und führt dazu, dass einen Fehler auftreten: **AdArray**, **AdChapter**, **AdEmpty**, **AdPropVariant**, und **AdUserDefined**. Darüber hinaus werden die folgenden Datentypen nicht unterstützt für ADO: **AdIDispatch**, **AdIUnknown**, und **AdIVariant**. Für diese Typen verwenden tritt kein Fehler auf, beim Anfügen, aber Verwendung kann zu unvorhersehbaren Ergebnissen wie z. B. Speicherverlusten führen.  
  
## <a name="recordset"></a>Recordset  
 Wenn Sie nicht Festlegen der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft vor dem Aufruf der **Anfügen** -Methode, **CursorLocation** festgelegt **AdUseClient** ( eine [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) Wert) automatisch, wenn die [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts aufgerufen wird.  
  
 Wird ein Laufzeitfehler auftreten, wenn die **Append** Methode wird aufgerufen, auf die **Felder** Auflistung eines geöffneten **Recordset**, oder auf eine **Recordset** in denen die [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) -Eigenschaft festgelegt wurde. Sie können nur Felder zum Anfügen einer **Recordset** , ist nicht geöffnet und noch nicht mit einer Datenquelle verbunden wurde. Dies ist normalerweise der Fall bei einer **Recordset** Objekt wird erstellt, mit der [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) Methode oder einer Objektvariablen zugewiesen.  
  
## <a name="record"></a>Datensatz  
 Ein Laufzeitfehler nicht durchgeführt, falls die **Append** Methode wird aufgerufen, auf die **Felder** Auflistung eines geöffneten **Datensatz**. Wird das neue Feld hinzugefügt werden, um die **Felder** Auflistung von der **Datensatz** Objekt. Wenn die **Datensatz** abgeleitet wurde eine **Recordset**, das neue Feld wird nicht angezeigt, der **Felder** Auflistung von der **Recordset** Objekt.  
  
 Ein nicht vorhandenes Feld erstellt und angefügt werden kann, die **Felder** Auflistung, indem Sie der Field-Objekt einen Wert zuweisen, als ob sie in der Auflistung bereits vorhanden waren. Die Zuweisung löst die automatische Erstellung von und Anhängen von der **Feld** -Objekt, und klicken Sie dann auf die Zuweisung wird abgeschlossen.  
  
 Nach dem Anfügen einer **Feld** auf die **Felder** Auflistung von eine **Datensatz** Objekt, rufen Sie die **Update** -Methode der der **Felder**  -Auflistung, um die Änderung zu speichern.  
  
## <a name="applies-to"></a>Gilt für  
  
- [Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
- [Parameters-Collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Append und CreateParameter – Beispiel (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append und CreateParameter – Beispiel (VC++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [CreateParameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Delete-Methode (Fields-Collection – ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO-Parameters-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Update-Methode](../../../ado/reference/ado-api/update-method.md)
