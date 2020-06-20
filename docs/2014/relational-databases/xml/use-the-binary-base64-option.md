---
title: Verwenden der Option BINARY BASE64 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
author: rothja
ms.author: jroth
ms.openlocfilehash: f3c6488a7a0c22fe2dfc91ac3d5760e8032e5b5f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067729"
---
# <a name="use-the-binary-base64-option"></a>Verwenden der Option BINARY BASE64
  Wenn die Option BINARY BASE64 in der Abfrage angegeben ist, werden die Binärdaten im Base64-codierten Format zurückgegeben. Der AUTO-Modus unterstützt die URL-Codierung von Binärdaten standardmäßig (sofern die Option BINARY BASE64 nicht angegeben wurde). Das heißt, anstelle von Binärdaten wird ein Verweis (eine relative URL auf das virtuelle Stammverzeichnis der Datenbank, in der die Abfrage ausgeführt wird) zurückgegeben. Dieser Verweis kann für den Zugriff auf die Binärdaten in nachfolgenden Vorgängen verwendet werden. Die Abfrage muss ausreichend Informationen, wie etwa Primärschlüsselspalten, bereitstellen, damit Teile des Images später im XML-Dokument identifiziert werden können.  
  
 Wenn beim Angeben einer Abfrage ein Alias für die Binärspalte der Sicht verwendet wird, wird der Alias in der URL-Codierung der Binärdaten zurückgegeben. In nachfolgenden Vorgängen ist der Alias bedeutungslos, und die URL-Codierung kann nicht zum Abrufen des Images verwendet werden. Sie sollten somit keine Aliasse bei der Abfrage einer Sicht mithilfe des FOR XML AUTO-Modus verwenden.  
  
 In einer SELECT-Abfrage werden beispielsweise Spalten durch Konvertieren in ein BLOB (Binary Large Object) insofern zu einer temporären Entität, als sie den zugehörigen Tabellen- und Spaltennamen verlieren. Abfragen im AUTO-Modus geben daher einen Fehler aus, da der Wert nicht in der XML-Hierarchie eingeordnet werden kann. Beispiel:  
  
```  
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)  
INSERT INTO MyTable VALUES (1, 0x7);  
```  
  
 Diese Abfrage führt wegen der Konvertierung in BLOB (Binary Large Object) zu einem Fehler:  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO;  
```  
  
 Die Lösung besteht im Hinzufügen der Option BINARY BASE64 zur FOR XML-Klausel. Ohne die Konvertierung liefert die Abfrage die erwarteten Ergebnisse:  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO, BINARY BASE64;  
```  
  
 Dies ist das Ergebnis:  
  
```  
<MyTable Col1="1" Col2="Bw==" />  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des AUTO-Modus mit FOR XML](use-auto-mode-with-for-xml.md)  
  
  
