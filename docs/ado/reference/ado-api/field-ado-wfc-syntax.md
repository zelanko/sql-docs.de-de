---
title: Feld (ADO / WFC-Syntax) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 583e6de7dc8c3ea05d61dda53c3e630d05e4d5f9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918751"
---
# <a name="field-ado---wfc-syntax"></a>Field (ADO/WFC-Syntax)
## <a name="package-commswfcdata"></a>Paket com.ms.wfc.data  
  
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
  
 (Weitere Informationen finden Sie in der Dokumentation für die com.ms.wfc.data.IDataFormat-Schnittstelle.)  
  
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
  
### <a name="field-accessor-methods"></a>Feld-Zugriffsmethoden  
 Die [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft eine [Feld](../../../ado/reference/ado-api/field-object.md) Objekt ruft ab oder legt den Inhalt dieses Objekts fest. Der Inhalt wird als eine Variante, eine Art von Objekt, das ein Wert zugewiesen werden kann und alle mit verschiedenen Datentypen dargestellt.  
  
 ADO/WFC-implementiert die **Wert** Eigenschaft mit dem die **"GetValue"** Methode, die ein VARIANT-Objekt zurückgibt und die **SetValue** Methode, die einen Variant-Wert als Argument akzeptiert. Varianten werden möglichst effizient in bestimmten Sprachen wie z. B. Microsoft Visual Basic.  
  
 Zusätzlich zu den **Wert** Eigenschaft ADO/WFC-bietet *Accessor* Methoden, mit denen Java-Datentypen zu erhalten, und legen Sie den Inhalt der **Feld** Objekte. Die meisten dieser Methoden haben Namen im Format **erhalten**_DataType_ oder **festgelegt**_DataType_.  
  
 Es gibt zwei wichtige Ausnahmen: Eines der **GetObject** Methoden gibt ein Objekt, das in einer bestimmten Klasse umgewandelt. Gibt es keine **GetNull** Eigenschaft; stattdessen wird eine **IsNull** -Eigenschaft, die gibt einen booleschen Wert, der angibt, ob das Feld null ist.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)
