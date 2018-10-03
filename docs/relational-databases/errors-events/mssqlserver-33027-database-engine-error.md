---
title: MSSQLSERVER_33027 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 880abcd92943e9a9083f69d7c41b6b33147c9ed1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597518"
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
SQL Server konnte den in der Fehlermeldung aufgelisteten Kryptografieanbieter nicht verwenden, da SQL Server die DLL nicht laden konnte. Entweder ist der Name ungültig, oder die Authenticode-Signatur ist ungültig.  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie, ob die Datei vorhanden ist und SQL Server die Berechtigung hat, auf diesen Speicherort zuzugreifen. Überprüfen Sie das Fehlerprotokoll auf zusätzliche verwandte Fehlermeldungen. Anderenfalls wenden Sie sich an den Kryptografieanbieter, um weitere Informationen zu erhalten.  
  
