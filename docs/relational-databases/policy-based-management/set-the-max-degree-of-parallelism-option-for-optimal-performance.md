---
title: Festlegen der 'Max. Grad an Parallelität'-Option auf optimale Leistung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3fb1cdb7d6b55d32a2029a840d8120b8f39b4e67
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627334"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Festlegen der 'Max. Grad an Parallelität'-Option auf optimale Leistung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel bestimmt, ob die Max. Grad an Parallelität-Option (MAXDOP) einen Wert größer als 8 hat. Wird diese Option auf einen größeren Wert festgelegt, führt dies häufig zu unerwünschtem Ressourcenverbrauch und zu Leistungseinbußen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die Max. Grad an Parallelität-Option mit sp_configure auf einen Wert von 8 oder weniger fest.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Microsoft Knowledge Base-Artikel 329204](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Konfigurieren der Serverkonfigurationsoption Max. Grad an Parallelität](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
