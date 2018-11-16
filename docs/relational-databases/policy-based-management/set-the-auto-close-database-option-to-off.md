---
title: Festlegen der Datenbankoption AUTO_CLOSE auf OFF | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 6b9fda04dd570d0077b692b86937e401bac54e42
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512905"
---
# <a name="set-the-autoclose-database-option-to-off"></a>Festlegen der Datenbankoption AUTO_CLOSE auf OFF
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel überprüft, ob die AUTO_CLOSE-Option auf OFF festgelegt ist. Wenn AUTO_CLOSE auf ON festgelegt ist, kann diese Option bei Datenbanken, auf die häufig zugegriffen wird, aufgrund des erhöhten Aufwands zum Öffnen und Schließen der Datenbank nach jeder Verbindung zu einer Leistungseinbuße führen. AUTO_CLOSE bewirkt auch die Leerung des Prozedurcaches nach jeder Verbindung.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Wenn auf eine Datenbank häufig zugegriffen wird, legen Sie die AUTO_CLOSE-Option für die Datenbank auf OFF fest.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
