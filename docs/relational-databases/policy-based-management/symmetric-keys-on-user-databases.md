---
title: Symmetrische Schlüssel für Benutzerdatenbanken | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dd650742e2781388d0d0941b80c6c9a9d60a801c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727306"
---
# <a name="symmetric-keys-on-user-databases"></a>Symmetrische Schlüssel für Benutzerdatenbanken
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel überprüft, ob Schlüssel mit einer Länge von weniger als 128 Bytes den RC2- oder RC4-Verschlüsselungsalgorithmus verwenden.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Verwenden Sie die AES-128-Bit-Verschlüsselung oder eine stärkere Verschlüsselung, um symmetrische Schlüssel für die Datenverschlüsselung zu erstellen. Wenn AES nicht vom Betriebssystem unterstützt wird, verwenden Sie 3DES.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
