---
title: Tabellennamen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5dd8de055521f4a1831d20a9a34bedb9309d1de6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67939786"
---
# <a name="table-names"></a>Tabellennamen
Wenn der dBASE-, Microsoft Excel-, Paradox-oder Text-Treiber verwendet wird, können Tabellennamen, die in der from-Klausel von SELECT oder DELETE auftreten, nach der INTO-Klausel in INSERT und After Update, CREATE TABLE und DROP TABLE einen gültigen Pfad, Primärnamen und eine gültige Dateinamenerweiterung enthalten. .  
  
 Die Verwendung eines Tabellennamens an einer anderen Stelle in einer SQL-Anweisung unterstützt nicht die Verwendung von Pfaden oder Erweiterungen, akzeptiert jedoch nur den Primärnamen (z. b. EMP aus c:\abc\emp).  
  
 Korrelations Namen (Aliase) können verwendet werden. Beispiel:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
