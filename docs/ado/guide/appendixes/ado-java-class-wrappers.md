---
title: ADO-Java-Klassen Wrapper | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 485c53645387e5dafbe562442ec12503df0a6737
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760556"
---
# <a name="ado-java-class-wrappers"></a>ADO-Java-Klassen-Wrapper
Dieser Code deklariert eine Instanz des ADO- [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Klassen-Wrapper und initialisiert Sie, alle in derselben Codezeile. Außerdem werden Variablen für jedes der Argumente in der [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode deklariert, insbesondere für [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) und Cursor Type (da Java Enumerationstypen nicht unterstützt). [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) Das **Recordset** -Objekt wird geöffnet und geschlossen. Durch Festlegen von "RS1 auf NULL" wird lediglich die Freigabe dieser Variablen geplant, wenn Java die systematische und vorübergehende Freigabe nicht verwendeter Objekte ausführt.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des Microsoft SDK für Java](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
