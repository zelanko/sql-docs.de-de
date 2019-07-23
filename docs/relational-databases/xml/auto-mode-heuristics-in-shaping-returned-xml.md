---
title: AUTO-Modus-Heuristik beim Ermitteln der Form des zurückgegebenen XML-Codes | Microsoft-Dokumentation
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||=azuresqldb-mi-current||>=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions
ms.openlocfilehash: 408589a38ae9b01777110bbab1fb3b20c380a6c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029340"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a>AUTO-Modus-Heuristik beim Ermitteln der Form des zurückgegebenen XML-Codes

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Der AUTO-Modus ermittelt die Form des zurückgegebenen XML-Codes auf der Grundlage der Abfrage. Um zu ermitteln, wie die Elemente geschachtelt werden sollen, vergleicht die AUTO-Modus-Heuristik die Spaltenwerte in benachbarten Zeilen. Dabei werden Spalten aller Datentypen, mit Ausnahme von **ntext**, **text**, **image**und **xml**miteinander verglichen. Spalten des Datentyps **(n)varchar(max)** und **varbinary(max)** werden verglichen.  
  
 Das folgende Beispiel veranschaulicht die Heuristik des AUTO-Modus beim Ermitteln der Form des resultierenden XML-Codes:  
  
```sql
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
ORDER BY T1.Id
FOR XML AUTO;
```  
  
 Um zu ermitteln, wo ein neues <`T1`>-Element beginnt, werden alle Spaltenwerte von Tabelle T1 (außer **ntext**, **text**, **image** und **xml**) verglichen, wenn der Schlüssel für die Tabelle T1 nicht angegeben wurde. Nehmen wir als Nächstes an, dass die **Name**-Spalte den Typ **nvarchar(40)** aufweist und dass die SELECT-Anweisung das folgende Rowset zurückgibt:  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 Die Heuristik des AUTO-Modus vergleicht alle Werte aus Tabelle T1, die Id- und die Name-Spalten. Da die ersten zwei Zeilen über die gleichen Werte für die Spalten „Id“ und „Name“ verfügen, wird ein \<T1>-Element, das über zwei untergeordnete \<T2>-Elemente verfügt, im Ergebnis hinzugefügt.  
  
 Der folgende XML-Code wird zurückgegeben:  
  
```xml
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 Nehmen wir jetzt an, dass die Name-Spalte den **text** -Datentyp aufweist. Die Heuristik des AUTO-Modus führt keinen Vergleich der Werte für diesen Datentyp durch. Stattdessen wird angenommen, dass sich die Werte voneinander unterscheiden. Dadurch wird der folgende XML-Code generiert:  
  
```xml
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des AUTO-Modus mit FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)  
  
  
