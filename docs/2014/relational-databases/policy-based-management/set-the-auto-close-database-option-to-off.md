---
title: Festlegen der Datenbankoption AUTO_CLOSE auf OFF | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: db6cf5a3f82c3493a8732958594743104fccc968
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066689"
---
# <a name="set-the-auto_close-database-option-to-off"></a>Festlegen der Datenbankoption AUTO_CLOSE auf OFF
  Diese Regel überprüft, ob die AUTO_CLOSE-Option auf OFF festgelegt ist. Wenn AUTO_CLOSE auf ON festgelegt ist, kann diese Option bei Datenbanken, auf die häufig zugegriffen wird, aufgrund des erhöhten Aufwands zum Öffnen und Schließen der Datenbank nach jeder Verbindung zu einer Leistungseinbuße führen. AUTO_CLOSE bewirkt auch die Leerung des Prozedurcaches nach jeder Verbindung.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Wenn auf eine Datenbank häufig zugegriffen wird, legen Sie die AUTO_CLOSE-Option für die Datenbank auf OFF fest.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
