---
title: MSSQLSERVER_33027 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b117743265ba0f993abfde19abaf873eb13ad8f5
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551715"
---
# <a name="mssqlserver_33027"></a>MSSQLSERVER_33027
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|33027|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_CRYPTOPROV_CANTLOADDLL|  
|Meldungstext|Fehler beim Laden des Kryptografieanbieters ‚%.*ls’ aufgrund einer ungültigen Authenticode-Signatur oder eines ungültigen Dateipfades. Überprüfen Sie vorhergehende Meldungen auf weitere Fehler.|  
  
## <a name="explanation"></a>Erklärung  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte den in der Fehlermeldung aufgelisteten Kryptografieanbieter nicht verwenden, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die DLL nicht laden konnte. Entweder ist der Name ungültig, oder die Authenticode-Signatur ist ungültig.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie, ob die Datei vorhanden ist und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Berechtigung hat, auf diesen Speicherort zuzugreifen. Überprüfen Sie das Fehlerprotokoll auf zusätzliche verwandte Fehlermeldungen. Anderenfalls wenden Sie sich an den Kryptografieanbieter, um weitere Informationen zu erhalten.  
  
  
