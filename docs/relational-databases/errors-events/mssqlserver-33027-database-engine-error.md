---
title: MSSQLSERVER_33027 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 047271007e5d0f6b9b5ef223696c4bfd8fc739df
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver33027"></a>MSSQLSERVER_33027
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|33027|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_CRYPTOPROV_CANTLOADDLL|  
|Meldungstext|Fehler beim Laden des Kryptografieanbieters ‚%.*ls’ aufgrund einer ungültigen Authenticode-Signatur oder eines ungültigen Dateipfades. Überprüfen Sie vorhergehende Meldungen auf weitere Fehler.|  
  
## <a name="explanation"></a>Erklärung  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte den in der Fehlermeldung aufgelisteten Kryptografieanbieter nicht verwenden, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die DLL nicht laden konnte. Entweder ist der Name ungültig, oder die Authenticode-Signatur ist ungültig.  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie, ob die Datei vorhanden ist und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Berechtigung hat, auf diesen Speicherort zuzugreifen. Überprüfen Sie das Fehlerprotokoll auf zusätzliche verwandte Fehlermeldungen. Anderenfalls wenden Sie sich an den Kryptografieanbieter, um weitere Informationen zu erhalten.  
  
