---
title: Das 0xFFFF-Zeichen ist nicht als Objekt Bezeichner gültig. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4594c1cca0fc183100d927842cc2b533694bf90e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85046159"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>0xFFFF-Zeichen ist als Objektbezeichner nicht gültig
  Der Upgrade Advisor hat das 0xFFFF-Zeichen in einem Objektbezeichner erkannt. Wenn der Datenbank-Kompatibilitätsmodus auf 90 oder höher festgelegt ist, kann in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher nicht auf Objekte wie Datenbanken, Tabellen und Spalten verwiesen werden, die dieses Zeichen in ihrem Bezeichner enthalten. Die Objekte können zudem nicht umbenannt werden. Wenn Sie auf [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] aktualisieren, behalten die Benutzerdatenbanken ihren Kompatibilitätsmodus bei. Bevor Sie den Datenbank-Kompatibilitätsmodus in 90 oder höher ändern, benennen Sie das Objekt um, das das Zeichen 0xFFFF enthält.  
  
 Weitere Informationen über Bezeichner finden Sie unter "Bezeichner" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation. Weitere Informationen über Datenbankkompatibilitätsmodi finden Sie unter "sp_dbcmptlevel" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
