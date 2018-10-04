---
title: Festlegen der 'Max. Grad an Parallelität'-Option auf optimale Leistung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7313f93381c9a3e2dd4e821d98e35bf3b5d5a06f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123570"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Festlegen der 'Max. Grad an Parallelität'-Option auf optimale Leistung
  Diese Regel bestimmt, ob die Max. Grad an Parallelität-Option (MAXDOP) einen Wert größer als 8 hat. Wird diese Option auf einen größeren Wert festgelegt, führt dies häufig zu unerwünschtem Ressourcenverbrauch und zu Leistungseinbußen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die Max. Grad an Parallelität-Option mit sp_configure auf einen Wert von 8 oder weniger fest.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Microsoft Knowledge Base-Artikel 329204](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Konfigurieren der Serverkonfigurationsoption Max. Grad an Parallelität](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
