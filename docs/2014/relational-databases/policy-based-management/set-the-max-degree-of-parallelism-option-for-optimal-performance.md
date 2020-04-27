---
title: Festlegen der 'Max. Grad an Parallelität'-Option auf optimale Leistung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 794dfea63b193ff79fb5831cb3a4e519d7d5f63e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62691389"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Festlegen der 'Max. Grad an Parallelität'-Option auf optimale Leistung
  Diese Regel bestimmt, ob die Max. Grad an Parallelität-Option (MAXDOP) einen Wert größer als 8 hat. Wird diese Option auf einen größeren Wert festgelegt, führt dies häufig zu unerwünschtem Ressourcenverbrauch und zu Leistungseinbußen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die Max. Grad an Parallelität-Option mit sp_configure auf einen Wert von 8 oder weniger fest.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Microsoft Knowledge Base-Artikel 329204](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Konfigurieren der Serverkonfigurationsoption Max. Grad an Parallelität](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
