---
title: Field (ADO-WFC-Syntax) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Field collection [ADO], ADO/WFC syntax
ms.assetid: 7e01cb24-2338-4f92-ad46-8d97248e1a4d
author: rothja
ms.author: jroth
ms.openlocfilehash: a1c4167b033163c8106a31070a83d044eb8e8fe7
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82757076"
---
# <a name="field-ado---wfc-syntax"></a>Field (ADO/WFC-Syntax)
## <a name="package-commswfcdata"></a>Paket "com. ms. wfc. Data"  
  
### <a name="methods"></a>Methoden  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
public byte[] getByteChunk(int len)  
public char[] getCharChunk(int len)  
public String getStringChunk(int len)  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
public int getActualSize()  
public int getAttributes()  
public void setAttributes(int pl)  
public com.ms.com.IUnknown getDataFormat()  
public void setDataFormat(com.ms.com.IUnknown format)  
```  
  
 (Weitere Informationen finden Sie in der Dokumentation zur Schnittstelle "com. ms. wfc. Data. IDataFormat").  
  
```  
public int getDefinedSize()  
public void setDefinedSize(int pl)  
public String getName()  
public int getNumericScale()  
public void setNumericScale(byte pbNumericScale)  
public Variant getOriginalValue()  
public int getPrecision()  
public void setPrecision(byte pbPrecision)  
public int getType()  
public void setType(int pDataType)  
public Variant getUnderlyingValue()  
public Variant getValue()  
public void setValue(Variant value)  
public AdoProperties getProperties()  
```  
  
### <a name="field-accessor-methods"></a>Feld Accessor-Methoden  
 Die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft eines [Feld](../../../ado/reference/ado-api/field-object.md) Objekts Ruft den Inhalt dieses Objekts ab oder legt ihn fest. Der Inhalt wird als Variant dargestellt. dabei handelt es sich um einen Objekttyp, dem ein Wert und mehrere Datentypen zugewiesen werden können.  
  
 ADO/WFC implementiert die **value** -Eigenschaft mit der **GetValue** -Methode, die ein Variant-Objekt zurückgibt. und die **SetValue** -Methode, die eine Variante als Argument annimmt. Varianten sind in bestimmten Sprachen, wie z. b. Microsoft Visual Basic, sehr effizient.  
  
 Zusätzlich zur **value** -Eigenschaft stellt ADO/WFC Accessormethoden *bereit* , die Java-Datentypen verwenden, um den Inhalt von **Feld** Objekten zu erhalten und festzulegen. Die meisten dieser Methoden haben Namen der Form **Get**_DataType_ oder **set**_DataType_.  
  
 Es gibt zwei bemerkenswerte Ausnahmen: eine der **GetObject** -Methoden gibt ein Objekt zurück, das in eine angegebene Klasse umgewandelt wurde. Es ist keine **getnull** -Eigenschaft vorhanden. Stattdessen gibt es eine **IsNull** -Eigenschaft, die einen booleschen Wert zurückgibt, der angibt, ob das Feld NULL ist.  
  
```  
public native boolean getBoolean();  
public void setBoolean(boolean v)  
public native byte getByte();  
public void setByte(byte v)  
public native byte[] getBytes();  
public void setBytes(byte[] v)  
public native double getDouble();  
public void setDouble(double v)  
public native float getFloat();  
public void setFloat(float v)  
public native int getInt();  
public void setInt(int v)  
public native long getLong();  
public void setLong(long v)  
public native short getShort();  
public void setShort(short v)  
public native String getString();  
public void setString(String v)  
public native boolean isNull();  
public void setNull()  
public Object getObject()  
public Object getObject(Class c)  
public void setObject(Object value)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)
