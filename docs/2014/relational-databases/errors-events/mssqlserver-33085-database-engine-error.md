---
title: MSSQLSERVER_33085 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 33085 (Database Engine error)
ms.assetid: c27b8d1d-668a-4ba8-8b61-25a5ebbc5485
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2d66231f97869207fdc8334b85d9f5d4d24e0183
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046679"
---
# <a name="mssqlserver33085"></a>MSSQLSERVER_33085
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|33085|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND|  
|Meldungstext|Eine oder mehrere Methoden können nicht in der Kryptografieanbieterbibliothek gefunden werden ‚%.*ls’.|  
  
## <a name="explanation"></a>Erklärung  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte den in der Fehlermeldung aufgelisteten Kryptografieanbieter nicht verwenden. Der Kryptografieanbieter hat eine erforderliche Methode nicht unterstützt. Der Status des Fehlers gibt an, welche Methode nicht gefunden wurde.  
  
|Status|Description|  
|-----------|-----------------|  
|1|SqlCryptInitializeProvider|  
|2|SqlCryptFreeProvider|  
|3|SqlCryptOpenSession|  
|4|SqlCryptCloseSession|  
|5|SqlCryptGetProviderInfo|  
|6|SqlCryptGetNextAlgorithmId|  
|7|SqlCryptGetAlgorithmInfo|  
|8|SqlCryptCreateKey|  
|9|SqlCryptDropKey|  
|10|SqlCryptGetNextKeyId|  
|11|SqlCryptGetKeyInfoByKeyId|  
|12|SqlCryptGetKeyInfoByThumb|  
|13|SqlCryptGetKeyInfoByName|  
|14|SqlCryptExportKey|  
|15|SqlCryptImportKey|  
|16|SqlCryptEncrypt|  
|17|SqlCryptDecrypt|  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenden Sie sich an den Kryptografieanbieter, um weitere Informationen zu erhalten.  
  
  