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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 591f2c00534f00529870b4eaa3742eef886d8e6d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48159920"
---
# <a name="use-the-binary-base64-option"></a>Verwenden der Option BINARY BASE64
  Wenn die Option BINARY BASE64 in der Abfrage angegeben ist, werden die Binärdaten im Base64-codierten Format zurückgegeben. Der AUTO-Modus unterstützt die URL-Codierung von Binärdaten standardmäßig (sofern die Option BINARY BASE64 nicht angegeben wurde). Das heißt, anstelle von Binärdaten wird ein Verweis (eine relative URL auf das virtuelle Stammverzeichnis der Datenbank, in der die Abfrage ausgeführt wird) zurückgegeben. Dieser Verweis kann für den Zugriff auf die Binärdaten in nachfolgenden Vorgängen verwendet werden. Die Abfrage muss ausreichend Informationen, wie etwa Primärschlüsselspalten, bereitstellen, damit Teile des Images später im XML-Dokument identifiziert werden können.  
  
 Wenn beim Angeben einer Abfrage ein Alias für die Binärspalte der Sicht verwendet wird, wird der Alias in der URL-Codierung der Binärdaten zurückgegeben. In nachfolgenden Vorgängen ist der Alias bedeutungslos, und die URL-Codierung kann nicht zum Abrufen des Images verwendet werden. Sie sollten somit keine Aliasse bei der Abfrage einer Sicht mithilfe des FOR XML AUTO-Modus verwenden.  
  
 In einer SELECT-Abfrage werden beispielsweise Spalten durch Konvertieren in ein BLOB (Binary Large Object) insofern zu einer temporären Entität, als sie den zugehörigen Tabellen- und Spaltennamen verlieren. Abfragen im AUTO-Modus geben daher einen Fehler aus, da der Wert nicht in der XML-Hierarchie eingeordnet werden kann. Zum Beispiel:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des AUTO-Modus mit FOR XML](use-auto-mode-with-for-xml.md)  
  
  
