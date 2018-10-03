---
title: MSSQLSERVER_9524 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0fae1116025949657739878f754782d775bf8717
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47653306"
---
# <a name="mssqlserver9524"></a>MSSQLSERVER_9524
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9254|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|XMLERR_INVALID_COLUMNSET_XML|  
|Meldungstext|Der angegebene XML-Inhalt entspricht nicht dem erforderlichen XML-Format für Sparsespaltensätze.|  
  
## <a name="explanation"></a>Erklärung  
Es wurde versucht, einen Spaltensatz zu ändern. Der XML-Inhalt eines Spaltensatzes muss die Formateinschränkungen für Spaltensätze erfüllen. Das allgemeine Format eines Spaltensatzes sieht folgendermaßen aus:  
  
`<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
Weitere Informationen zu Spaltensätzen finden Sie im Thema "Verwenden von Spaltensätzen" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="user-action"></a>Benutzeraktion  
Korrigieren Sie das XML-Format für den Spaltensatz in der Anweisung.  
  
