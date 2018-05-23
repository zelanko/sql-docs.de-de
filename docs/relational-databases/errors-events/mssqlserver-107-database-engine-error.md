---
title: MSSQLSERVER_107 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46a7627b3dce6100ba77cf1fbc4b42081451c299
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver107"></a>MSSQLSERVER_107
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|107|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|P_NOCORRMATCH|  
|Meldungstext|Das Spaltenpräfix '%.*ls' stimmt mit keinem in der Abfrage verwendeten Tabellen- oder Aliasnamen überein.|  
  
## <a name="explanation"></a>Erklärung  
Die Auswahlliste der Abfrage enthält ein Sternchen (*), das falsch mit einem Spaltenpräfix gekennzeichnet ist. Dieser Fehler kann unter folgenden Bedingungen zurückgegeben werden:  
  
-   Das Spaltenpräfix stimmt mit keinem in der Abfrage verwendeten Tabellen- oder Aliasnamen überein. In der folgenden Anweisung wird beispielsweise ein Aliasname (`T1`) als Spaltenpräfix verwendet, der Alias ist jedoch nicht in der FROM-Klausel definiert.  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   Wenn in der FROM-Klausel ein Aliasname für die Tabelle festgelegt ist, wird ein Tabellenname als Spaltenpräfix angegeben. In der folgenden Anweisung wird beispielsweise der Tabellenname `ErrorLog` als Spaltenpräfix verwendet, für die Tabelle ist jedoch ein Alias (`T1`) in der FROM-Klausel definiert.  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
    Wenn in der FROM-Klausel ein Alias für einen Tabellennamen angegeben wurde, kann nur der Alias verwendet werden, der den Spalten in der Tabelle als Präfix vorangestellt wird.  
  
## <a name="user-action"></a>Benutzeraktion  
Gleichen Sie die Spaltenpräfixe mit den in der FROM-Klausel der Abfrage angegeben Tabellen- oder Aliasnamen ab. Die oben genannten Anweisungen können beispielsweise folgendermaßen korrigiert werden:  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
oder  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[MSSQLSERVER_4104](~/relational-databases/errors-events/mssqlserver-4104-database-engine-error.md)  
  
