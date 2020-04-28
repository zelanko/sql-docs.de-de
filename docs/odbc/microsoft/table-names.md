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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91a415cd456186f18ef358b9d504145f78152774
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303121"
---
# <a name="table-names"></a>Tabellennamen
Wenn der dBASE-, Microsoft Excel-, Paradox-oder Text-Treiber verwendet wird, können Tabellennamen, die in der from-Klausel von SELECT oder DELETE auftreten, nach der INTO-Klausel in INSERT und After Update, CREATE TABLE und DROP TABLE einen gültigen Pfad, Primärnamen und eine gültige Dateinamenerweiterung enthalten.  
  
 Die Verwendung eines Tabellennamens an einer anderen Stelle in einer SQL-Anweisung unterstützt nicht die Verwendung von Pfaden oder Erweiterungen, akzeptiert jedoch nur den Primärnamen (z. b. EMP aus c:\abc\emp).  
  
 Korrelations Namen (Aliase) können verwendet werden. Beispiel:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
