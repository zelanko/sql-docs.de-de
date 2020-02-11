---
title: Parameter (ADO-WFC-Syntax) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Parameter collection [ADO], ADO/WFC syntax
ms.assetid: d00d1e1e-14b1-41a2-a00f-2a3cb7396f15
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22f9d928cf008396346067a3e166fa281be4093d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931714"
---
# <a name="parameter-ado---wfc-syntax"></a>Parameter (ADO/WFC-Syntax)
## <a name="package-commswfcdata"></a>Paket "com. ms. wfc. Data"  
  
### <a name="constructor"></a>Konstruktor  
  
```  
public Parameter()  
public Parameter(String name)  
public Parameter(String name, int type)  
public Parameter(String name, int type, int dir)  
public Parameter(String name, int type, int dir, int size)  
public Parameter(String name, int type, int dir, int size, Object value)  
```  
  
### <a name="methods"></a>Methoden  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
public int getAttributes()  
public void setAttributes(int attr)  
public int getDirection()  
public void setDirection(int dir)  
public String getName()  
public void setName(String name)  
public int getNumericScale()  
public void setNumericScale(int scale)  
public int getPrecision()  
public void setPrecision(int prec)  
public int getSize()  
public void setSize(int size)  
public int getType()  
public void setType(int type)  
public com.ms.com.Variant getValue()  
public void setValue(Object v)  
public AdoProperties getProperties()  
```  
  
## <a name="parameter-accessor-methods"></a>Parameter Accessor-Methoden  
 Die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft eines [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekts Ruft den Inhalt dieses Objekts ab oder legt ihn fest. Der Inhalt wird als Variant dargestellt. dabei handelt es sich um einen Objekttyp, dem ein Wert und mehrere Datentypen zugewiesen werden können.  
  
 ADO/WFC implementiert die **value** -Eigenschaft mit der **GetValue** -Methode, die ein Variant-Objekt zurückgibt. und die **SetValue** -Methode, die eine Variante als Argument annimmt. Varianten sind in bestimmten Sprachen, wie z. b. Microsoft Visual Basic, sehr effizient.  
  
 Zusätzlich zur **value** - *Eigenschaft stellt ADO* /WFC Accessormethoden bereit, die Java-Datentypen verwenden, um den Inhalt von **Parameter** Objekten zu erhalten und festzulegen. Die meisten dieser Methoden haben Namen der Form **Get**_DataType_ oder **set**_DataType_.  
  
 Es gibt eine bemerkenswerte Ausnahme: Es ist keine **getnull** -Eigenschaft vorhanden. Stattdessen gibt es eine **IsNull** -Eigenschaft, die einen booleschen Wert zurückgibt, der angibt, ob das Feld NULL ist.  
  
```  
public boolean getBoolean()  
public void setBoolean(boolean v)  
public byte getByte()  
public void setByte(byte v)  
public double getDouble()  
public void setDouble(double v)  
public float getFloat()  
public void setFloat(float v)  
public int getInt()  
public void setInt(int v)  
public long getLong()  
public void setLong(long v)  
public short getShort()  
public void setShort(short v)  
public String getString()  
public void setString(String v)  
public boolean isNull()  
public void setNull()  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)
