---
title: ADO-Java-Klassen-Wrapper | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ddcbba246f0bdcfb5c3a22766f5d335a2bd5893e
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350314"
---
# <a name="ado-java-class-wrappers"></a>ADO-Java-Klassen-Wrapper
Dieser Code deklariert eine Instanz von der ADO [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Klassenwrapper und initialisiert, auf die gleiche Zeile des Codes. Es darüber hinaus deklariert Variablen für jeden der Argumente in der [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode, dies gilt insbesondere für [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) und [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (da Java unterstützt keine aufgelistet Typen). Er öffnet und schließt die **Recordset** Objekt. Rs1 lediglich auf NULL festlegen, plant diese Variable freigegeben werden, wenn Java der systematischen und unterbrochene-Version von nicht verwendeten Objekten ausführt.  
  
```java
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Using the Microsoft SDK for Java (Verwenden des Microsoft SDK für Java)](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
