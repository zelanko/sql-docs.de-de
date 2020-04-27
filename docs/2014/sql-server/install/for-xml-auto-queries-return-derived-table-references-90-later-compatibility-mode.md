---
title: FOR XML Auto-Abfragen geben Verweise auf abgeleitete Tabellen im Kompatibilitätsmodus 90 oder höher zurück. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5b42d8fd7694aaa3962d049cb0e9663479778958
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095191"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a>FOR XML AUTO-Abfragen geben abgeleitete Tabellenverweise im Kompatibilitätsmodus 90 oder höher zurück
  Wenn der Datenbank-Kompatibilitätsgrad auf 90 oder höher festgelegt ist, geben FOR XML-Abfragen, die im AUTO-Modus ausgeführt werden, Verweise auf Aliase abgeleiteter Tabellen wieder. Wenn der Datenbank-Kompatibilitätsgrad auf 80 festgelegt ist, geben FOR XML AUTO-Abfragen Verweise auf die Basistabellen wieder, die eine abgeleitete Tabelle definieren.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Sehen Sie sich z. B. die folgende Tabelle an:  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 Die folgende Abfrage, die eine abgeleitete Tabelle umfasst, führt bei den Kompatibilitätsgraden 80, 90 oder höher zu unterschiedlichen Ergebnissen:  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 Beim Kompatibilitätsgrad 80 gibt die Abfrage die folgenden Ergebnisse zurück. Die Ergebnisse verweisen auf die Basistabellenaliase `a` und `b` der abgeleiteten Tabelle anstatt auf den Alias der abgeleiteten Tabelle.  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 Beim Kompatibilitätsgrad 90 oder höher gibt die Abfrage Verweise auf den Alias `DerivedTest` der abgeleiteten Tabelle anstatt auf die Basistabellen der abgeleiteten Tabelle wieder.  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie die Anwendung nach Bedarf, um den Änderungen bei den Ergebnissen von FOR XML AUTO-Abfragen, die abgeleitete Tabellen umfassen und mit dem Kompatibilitätsgrad 90 oder höher ausgeführt werden, Rechnung zu tragen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
